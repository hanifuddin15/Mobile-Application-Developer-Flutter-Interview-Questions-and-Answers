Excellent — moving on with **FULL DETAILED, EXPLAINED, EXAMPLE-RICH** answers for:

# 🟦 **SECTION 2 — DART LANGUAGE QUESTIONS (16–25)**

*(This will be long, but very clear and interview-ready.)*

---

# ⭐ **16. What is async/await in Dart?**

## ✔ Detailed Explanation

Dart is a single-threaded language, but it handles asynchronous tasks (API calls, database queries, timers) using an **event loop**.

`async` and `await` make asynchronous code look like synchronous code.

* `async` → marks a function as asynchronous
* `await` → pauses execution until a Future completes

### ✔ Example (API call)

```dart
Future<void> fetchUser() async {
  print("Fetching...");
  final data = await api.getUser();  // waits here
  print("Fetched: $data");
}
```

### ✔ Without async/await (hard to read)

```dart
api.getUser().then((data) {
  print("Fetched: $data");
});
```

### ✔ Why async/await is useful?

* Avoids callback hell
* Makes code readable
* Easy debugging

---

# ⭐ **17. Difference Between Future and Stream**

## ✔ Detailed Explanation

| Feature | Future               | Stream                          |
| ------- | -------------------- | ------------------------------- |
| Emits   | **one value**        | **multiple values over time**   |
| Type    | `Future<int>`        | `Stream<int>`                   |
| Usage   | API calls, file load | Chat messages, location updates |
| Cancel  | Not cancellable      | Can be paused/cancelled         |

### ✔ Future Example

```dart
Future<int> getAge() async {
  return 25;
}
```

### ✔ Stream Example (continuous data)

```dart
Stream<int> counter() async* {
  for (int i = 0; i < 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}
```

---

# ⭐ **18. What is the use of Isolates in Dart?**

## ✔ Detailed Explanation

An **Isolate** is a separate memory + thread for running CPU-heavy code without blocking UI.

### ✔ Use Cases

* Parsing huge JSON
* Compressing images
* Encrypting data
* Performing large loops
* Video processing

### ✔ Example using compute()

```dart
final result = await compute(parseJson, jsonString);
```

### Why compute()?

It automatically creates an isolate, sends the work, and returns result.

---

# ⭐ **19. What are extension methods?**

### ✔ Explanation

Extension methods let you **add new methods to existing classes** without inheritance.

### ✔ Example

```dart
extension StringExtension on String {
  bool get isValidEmail {
    return contains("@") && contains(".");
  }
}

void main() {
  print("hello@gmail.com".isValidEmail); // true
}
```

### ✔ Why useful?

* Cleaner code
* Reusable utilities
* Does not modify original class

---

# ⭐ **20. Describe null safety in Dart.**

### ✔ Explanation

Null safety prevents null pointer exceptions by ensuring variables cannot be null unless explicitly allowed.

### ✔ Variable types

| Syntax              | Meaning                     |
| ------------------- | --------------------------- |
| `String name;`      | Non-nullable                |
| `String? name;`     | Nullable                    |
| `late String name;` | Initialized later, non-null |

### ✔ Null-safe operators

* `?` → nullable variable
* `??` → default value
* `?.` → safe method call
* `!` → force non-null

### ✔ Example

```dart
String? city;
print(city ?? "Unknown");  // Default value
```

---

# ⭐ **21. What is a mixin?**

### ✔ Explanation

A mixin allows a class to share methods with other classes **without inheritance**.

### ✔ Example

```dart
mixin Logger {
  void log(String msg) => print("LOG: $msg");
}

class Service with Logger {}

void main() {
  Service().log("Started");
}
```

### ✔ Why mixins?

* Avoid long inheritance chains
* Reuse methods
* Cleaner architecture

---

# ⭐ **22. Difference Between Factory Constructor & Normal Constructor**

### ✔ Normal Constructor

Creates a **new instance** every time.

```dart
class User {
  User(this.name);
  String name;
}
```

---

### ⭐ Factory Constructor

Does **not always create new instance** — can return existing objects (Singleton), or conditional objects.

### ✔ Example — Singleton

```dart
class Database {
  static final Database _instance = Database._();

  factory Database() {
    return _instance;
  }

  Database._();
}
```

Now:

```dart
Database db1 = Database();
Database db2 = Database();
print(db1 == db2); // true
```

### ✔ When to use factory constructor?

* Singleton pattern
* Caching objects
* Parsing JSON & returning different subclasses

---

# ⭐ **23. late keyword vs nullable variable**

## ✔ Nullable Variable

```dart
String? name;   // can be null
```

---

## ✔ late Variable

Used when you want to promise Dart that:

✔ I will initialize this variable later
✔ It will NOT be null

### ✔ Example

```dart
late String token;

void init() {
  token = "ABC123";
}
```

### ✔ Why late?

* Initialize heavy variables lazily
* Initialize inside initState
* Avoid constructor injection

---

# ⭐ **24. final vs const vs var**

### ✔ var

* Mutable
* Type inferred automatically

```dart
var age = 20; 
age = 21;
```

### ✔ final

* Value cannot change after first assignment

```dart
final today = DateTime.now();  // allowed
```

### ✔ const

* Compile-time constant

```dart
const pi = 3.14;
const names = ["A", "B"]; 
```

### ✔ Difference

| Keyword | Type     | Can change? | When assigned |
| ------- | -------- | ----------- | ------------- |
| var     | inferred | yes         | runtime       |
| final   | fixed    | no          | runtime       |
| const   | fixed    | no          | compile-time  |

---

# ⭐ **25. Cascade operator (..) in Dart**

### ✔ Explanation

Cascade operator allows multiple operations on the **same object** without repeating the variable name.

### ✔ Example

```dart
User()
  ..name = "Hanif"
  ..age = 26
  ..printDetails();
```

Equivalent to:

```dart
var user = User();
user.name = "Hanif";
user.age = 26;
user.printDetails();
```

### ✔ When useful?

* Initializing objects
* UI builders
* Configuring classes with many setters

---

# 🎉 **SECTION 2 COMPLETED!**

