# 📱 **SECTION 10 — MOBILE DEVELOPMENT FUNDAMENTALS (Questions 69–73)**

---

# ⭐ **69. App Lifecycle**

```dart
WidgetsBindingObserver().didChangeAppLifecycleState(state);
```

* States: `resumed`, `inactive`, `paused`, `detached`

---

# **70. Handling Permissions**

* Use `permission_handler`

```dart
Permission.camera.request();
```

---

# ⭐ **71. Local Storage**

* **Key-value:** SharedPreferences
* **Structured:** SQFLite, Hive

Example (SharedPreferences):

```dart
final prefs = await SharedPreferences.getInstance();
prefs.setString('token', 'abc123');
```

---

# **72. Adaptive vs Responsive**

* **Responsive:** adapts layout based on screen size
* **Adaptive:** changes behavior based on platform (iOS/Android)

---

# ⭐ **73. Method Channel**

* Call native Android/iOS code from Dart

```dart
static const platform = MethodChannel('com.app/channel');

final result = await platform.invokeMethod('getBatteryLevel');
```

---
