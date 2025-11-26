Perfect — now we move into one of the **most important interview sections**:

# 🌐 **SECTION 4 — API & Backend Integration (Questions 32–40)**

This section includes **deep explanations + diagrams + real Flutter examples + best practices** used in production apps.

---

# ⭐ **32. How do you integrate REST APIs in Flutter?**

## ✔ Typical Layered Architecture for API Integration

```
UI → BLoC / Controller → Repository → API Service → Server
```

### ✔ Breakdown of Responsibilities

* **UI** → displays data
* **BLoC / GetX Controller** → manages state
* **Repository** → abstracts API sources
* **API Service** → handles HTTP calls
* **Model** → parses JSON

---

## ✔ Example: API Integration Step-by-Step

### **Step 1: Create Model**

```dart
class User {
  final int id;
  final String name;

  User({required this.id, required this.name});

  factory User.fromJson(Map<String, dynamic> json) {
    return User(
      id: json['id'],
      name: json['name'],
    );
  }
}
```

---

### **Step 2: API Service**

Using **Dio** (recommended):

```dart
class ApiService {
  final Dio dio = Dio(BaseOptions(
    baseUrl: 'https://jsonplaceholder.typicode.com',
  ));

  Future<List<User>> getUsers() async {
    final response = await dio.get('/users');
    return (response.data as List)
        .map((json) => User.fromJson(json))
        .toList();
  }
}
```

---

### **Step 3: Repository**

```dart
class UserRepository {
  final ApiService api;

  UserRepository(this.api);

  Future<List<User>> fetchUsers() => api.getUsers();
}
```

---

### **Step 4: BLoC / GetX Controller Example (BLoC)**

```dart
class UserBloc extends Bloc<UserEvent, UserState> {
  final UserRepository repo;

  UserBloc(this.repo) : super(UserLoading()) {
    on<FetchUsers>((event, emit) async {
      emit(UserLoading());
      try {
        final users = await repo.fetchUsers();
        emit(UserLoaded(users));
      } catch (e) {
        emit(UserError(e.toString()));
      }
    });
  }
}
```

---

### **Step 5: UI**

```dart
BlocBuilder<UserBloc, UserState>(
  builder: (context, state) {
    if (state is UserLoading) return CircularProgressIndicator();
    if (state is UserLoaded)
      return ListView(
        children: state.users
            .map((u) => ListTile(title: Text(u.name)))
            .toList(),
      );
    if (state is UserError) return Text("Error: ${state.message}");
    return SizedBox.shrink();
  },
)
```

---

# ⭐ **33. Difference between Dio and the http package**

| Feature                  | Dio          | HTTP      |
| ------------------------ | ------------ | --------- |
| Interceptors             | ✔ Yes        | ❌ No      |
| Cancel Requests          | ✔ Yes        | ❌ No      |
| Upload/Download Progress | ✔ Built-in   | ❌ Manual  |
| Base Options             | ✔ Easy       | 🔸 Manual |
| Error Handling           | ✔ Structured | ❌ Basic   |
| File Upload              | ✔ Simple     | 🔸 Hard   |
| Performance              | Fast         | Moderate  |

---

## ✔ Example: Upload with Progress using Dio

```dart
await dio.post(
  "/upload",
  data: FormData.fromMap({
    'file': await MultipartFile.fromFile(path),
  }),
  onSendProgress: (sent, total) {
    print("${sent / total * 100}%");
  },
);
```

---

# ⭐ **34. Explain status codes like 200, 400, 401, 500**

### ✔ Common HTTP Status Codes

| Code    | Meaning             | Example Reason                |
| ------- | ------------------- | ----------------------------- |
| **200** | OK                  | Success                       |
| **201** | Created             | New resource                  |
| **400** | Bad Request         | Validation failed             |
| **401** | Unauthorized        | Invalid token / not logged in |
| **403** | Forbidden           | No permission                 |
| **404** | Not Found           | Invalid endpoint              |
| **409** | Conflict            | Duplicate record              |
| **500** | Server Error        | Bug in backend                |
| **503** | Service Unavailable | Server down                   |

---

## ✔ Example in Flutter (Dio)

```dart
try {
  final res = await dio.get('/users');
} on DioException catch (e) {
  if (e.response!.statusCode == 401) {
    print("Unauthorized! Redirect to login.");
  }
}
```

---

# ⭐ **35. How do you handle authentication (token storage)?**

## ✔ Best Practice: Use secure, encrypted storage

### Options:

* **flutter_secure_storage** → recommended
* SharedPreferences → not secure
* Hive → secure if encrypted

---

## ✔ Example using `flutter_secure_storage`

```dart
final storage = FlutterSecureStorage();
await storage.write(key: "token", value: "abc123");

String? token = await storage.read(key: "token");
```

---

## ✔ Sending Token in API Headers

```dart
dio.options.headers['Authorization'] = 'Bearer $token';
```

---

## ✔ Auto refresh token (interceptor)

Dio interceptors can refresh expired tokens automatically.

---

# ⭐ **36. What is caching and how do you implement it?**

## ✔ Why caching?

* Faster loading
* Less API usage
* Better offline experience

---

## ✔ Methods of Caching

1. **SharedPreferences** → simple key-value
2. **Hive** → fast NoSQL db
3. **SQFLite** → structured relational db
4. **Local JSON storage** → for app config
5. **Dio Cache Interceptor** → auto cache network responses

---

## ✔ Example: Storing API response in Hive

```dart
var box = await Hive.openBox('users');

await box.put("userList", response.data);
```

Retrieve:

```dart
var cachedUsers = box.get("userList");
```

---

# ⭐ **37. How do you handle network errors gracefully?**

## ✔ Example: Handling errors with Dio

```dart
try {
  final res = await dio.get('/users');
} on DioException catch (e) {
  if (e.type == DioExceptionType.connectionTimeout) {
    showError("Connection Timeout!");
  } else if (e.response?.statusCode == 500) {
    showError("Server error! Try later.");
  } else {
    showError("Something went wrong.");
  }
}
```

---

## ✔ UI error handling example

```dart
if (state is UserError)
  return Column(
    children: [
      Text("Failed to load data"),
      ElevatedButton(onPressed: retry, child: Text("Retry"))
    ],
  );
```

---

# ⭐ **38. How do you parse large JSON files?**

## ✔ Large JSON parsing can freeze the UI

To avoid jank:

✔ Use **Isolates**
✔ Use **compute()**

---

## ✔ Example

```dart
final result = await compute(parseUsers, responseBody);
```

Function:

```dart
List<User> parseUsers(String jsonStr) {
  final data = jsonDecode(jsonStr) as List;
  return data.map((e) => User.fromJson(e)).toList();
}
```

---

## ✔ Why isolate?

Parsing 10,000+ items in main thread causes frame drops.

---

# ⭐ **39. What is pagination? How have you implemented it?**

## ✔ Pagination = loading data page-by-page

Used for:

* Infinite scrolling
* Comments
* News feed
* Chats

---

## ✔ Simple Pagination Logic

1. Start with page = 1
2. At scroll bottom → call next page
3. Append new items
4. Update UI

---

## ✔ Example (scroll listener)

```dart
_scrollController.addListener(() {
  if (_scrollController.position.pixels ==
      _scrollController.position.maxScrollExtent) {
    context.read<UserBloc>().add(FetchMoreUsers());
  }
});
```

---

## ✔ Backend sample URL

```
GET /users?page=1&limit=20
```

---

# ⭐ **40. How do you upload images/files to a server?**

## ✔ Using Dio (recommended)

### Example:

```dart
Future uploadImage(String path) async {
  FormData formData = FormData.fromMap({
    'file': await MultipartFile.fromFile(path, filename: 'image.jpg'),
  });

  final res = await dio.post('/upload', data: formData);
  return res.data;
}
```

---

## ✔ Upload with Progress

```dart
onSendProgress: (sent, total) {
  print("Uploading: ${sent / total * 100}%");
}
```

---

## ✔ Compress images before upload

Use **flutter_image_compress** to reduce size.

---

# 🎉 **SECTION 4 COMPLETED!**

---


➡ **Continue Section 5 (Firebase & Cloud Services — Detailed)**
