# 🏛 **SECTION 7 — ARCHITECTURE & STRUCTURE (Questions 54–58)**

---

# ⭐ **54. What is Clean Architecture in Flutter?**

**Layers:**

1. **Presentation** → Widgets/UI, BLoC/Cubit/ViewModel
2. **Domain** → Business logic, Use Cases
3. **Data** → API calls, database access

**Advantages:**

* Testable
* Scalable
* Maintainable

---

# **55. MVC vs MVVM vs BLoC**

| Pattern  | Description                                   |
| -------- | --------------------------------------------- |
| **MVC**  | Model → View → Controller (basic)             |
| **MVVM** | Model → View → ViewModel (UI logic separated) |
| **BLoC** | Event → State → UI (reactive, stream-based)   |

---

# ⭐ **56. Why use layered architecture?**

* Avoid tightly coupled code
* Easier testing
* Reusable business logic
* Easier team collaboration

---

# **57. Recommended Project Structure**

```
lib/
 ├─ features/
 │   ├─ auth/
 │   │   ├─ data/
 │   │   ├─ domain/
 │   │   └─ presentation/
 │   └─ home/
 └─ core/
     ├─ utils/
     ├─ constants/
     └─ network/
```

---

# ⭐ **58. Dependency Injection in Flutter**

* **get_it** or **GetX** can inject services

```dart
final getIt = GetIt.instance;
getIt.registerLazySingleton<ApiService>(() => ApiService());
```

* Access anywhere:

```dart
final api = getIt<ApiService>();
```

---
