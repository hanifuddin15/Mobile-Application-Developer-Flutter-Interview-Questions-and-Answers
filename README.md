# 📘 Contents Overview 

✅ All **100 questions + answers**
✅ Additional **20 advanced Flutter/Dart questions**
✅ Important questions **highlighted** with ⭐ or **bold**
✅ Clean sections + headers + tables + code blocks
✅ Attractive formatting — perfect for GitHub README

You can copy–paste directly into a README file.

---

# 📘 **Flutter Interview Q&A – Complete Developer Guide (2025 Edition)**

### **By: Hanif Uddin**

> 🚀 *A fully structured and styled markdown file for your GitHub. Includes 100 core questions + 20 advanced questions.*

---

# 🟦 Table of Contents

* [🔥 Core Flutter Questions](#-core-flutter-questions)
* [💠 Dart Language Questions](#-dart-language-questions)
* [🟧 State Management Questions](#-state-management-questions)
* [🌐 API & Backend Questions](#-api--backend-integration)
* [☁️ Firebase & Cloud Questions](#-firebase--cloud-services)
* [⚡ Performance Optimization](#-app-performance-optimization)
* [🏛 Architecture & Structure](#-architecture--structure)
* [📦 Deployment & DevOps](#-deployment--devops)
* [🧪 Debugging & Testing](#-debugging--testing)
* [📱 Mobile Fundamentals](#-mobile-development-fundamentals)
* [🎭 Scenario-Based Questions](#-scenario-based-questions)
* [👔 HR Questions](#-hr-questions)
* [📌 CV-Based Questions](#-questions-specific-to-my-cv)
* [🧠 Advanced Flutter Questions](#-advanced-flutter--dart-questions)

---

# 🔥 **CORE FLUTTER QUESTIONS**

---

### ⭐ **1. What is Flutter and why do you prefer it?**

**Answer:**
Flutter is Google’s UI SDK for building cross-platform apps from a single codebase.
I prefer it because of:

* Fast development
* UI flexibility
* 60fps performance
* Mature ecosystem

---

### **2. Explain the widget tree.**

**Answer:**
The widget tree is the hierarchical representation of UI elements. Flutter rebuilds widgets efficiently by diffing old & new widget trees.

---

### ⭐ **3. Difference between StatelessWidget and StatefulWidget?**

| StatelessWidget      | StatefulWidget         |
| -------------------- | ---------------------- |
| No state changes     | Has mutable state      |
| UI fixed after build | UI updates dynamically |
| Lightweight          | Heavier                |

---

### **4. Flutter rendering pipeline – short explanation**

1. **Build** → Widget tree
2. **Layout** → Size & constraints
3. **Paint** → Draw UI
4. **Composite** → Layers
5. **Rasterize** → GPU rendering

---

### ⭐ **5. What are keys in Flutter? When do you use them?**

**Answer:**
Keys preserve widget identity when order/position changes. Helpful in:

* Lists
* Animations
* Forms
* Reorder widgets

---

### **6. Hot Reload vs Hot Restart**

* **Hot Reload:** Injects code, preserves state
* **Hot Restart:** Restarts app, resets state

---

### **7. What is BuildContext?**

**Answer:**
A reference to the widget’s position in the tree. Used for:

* Navigation
* Getting Theme / MediaQuery
* Finding ancestors

---

### ⭐ **8. How do you handle navigation?**

**Answer:**
I use:

* **GetX** for simple navigation
* **GoRouter** for deep linking
* **Navigator 2.0** for custom routing flows

---

### **9. What is InheritedWidget?**

**Answer:**
A low-level way to pass data down the tree. Used internally by Provider, Riverpod, etc.

---

### **10. What is an Isolate in Flutter?**

**Answer:**
A separate memory-thread for heavy CPU tasks.

---

### ⭐ **11. How to write responsive UI?**

* MediaQuery
* LayoutBuilder
* Flexible/Expanded
* DeviceType breakpoints

---

### **12. What is Flutter DevTools?**

**Answer:**
Toolkit for examining:

* Rebuilds
* Memory leaks
* CPU usage
* Frame rendering

---

### ⭐ **13. Element Tree vs Widget Tree**

* **Widget Tree:** Immutable descriptions
* **Element Tree:** Runtime instances maintaining state

---

### **14. Lifecycle of StatefulWidget**

```
initState → didChangeDependencies → build → didUpdateWidget → deactivate → dispose
```

---

### ⭐ **15. What causes unnecessary rebuilds?**

* Large setState calls
* Bad widget structure
* Not using const

**Solutions:**

* const widgets
* ValueListenable
* BLoC or GetX

---

---

# 💠 **DART LANGUAGE QUESTIONS**

---

### ⭐ **16. async/await?**

Used to handle non-blocking asynchronous operations.

---

### **17. Future vs Stream**

* Future → single response
* Stream → multiple async responses

---

### **18. Isolates?**

Used for CPU-heavy work to avoid UI jank.

---

### ⭐ **19. Extension Methods?**

Add custom methods to existing classes without inheritance.

---

### **20. Null safety?**

Prevents null errors by making variables non-nullable unless marked with `?`.

---

### **21. Mixins?**

Sharing methods between classes without inheritance.

---

### ⭐ **22. Factory vs Normal constructor**

* Normal: always creates new object
* Factory: can return existing instance/singleton

---

### **23. late vs nullable?**

* `late`: initialized later, must not be null
* `?`: variable can be null

---

### ⭐ **24. final vs const vs var**

* var → mutable
* final → assigned once
* const → compile-time constant

---

### **25. Cascade operator**

```
object
  ..method1()
  ..method2();
```

---

---

# 🟧 **STATE MANAGEMENT QUESTIONS**

---

### ⭐ **26. Explain BLoC**

Separates UI & logic using:
**Events → Logic → States**
Excellent for scalable apps.

---

### **27. API calls in BLoC**

Emit loading → call API → emit success/error.

---

### ⭐ **28. Difference between Cubit & BLoC**

* Cubit: simpler, direct state
* BLoC: event-driven, structured

---

### **29. Why GetX?**

Simple, reactive, fast, less boilerplate.

---

### ⭐ **30. Provider vs Riverpod vs GetX**

* Provider: simple
* Riverpod: robust & safe
* GetX: fastest & easiest

---

### **31. What does state management solve?**

Keeps UI predictable & reduces rebuild issues.

---

---

# 🌐 **API & BACKEND INTEGRATION**

---

### ⭐ **32. How do you integrate REST APIs?**

* Dio/http → service layer → repository → BLoC/GetX → UI

---

### **33. Dio vs http**

* Dio has interceptors, cancellation, progress, better errors.

---

### ⭐ **34. Status codes**

* 200 OK
* 400 Bad request
* 401 Unauthorized
* 500 Server error

---

### **35. Token storage?**

SharedPreferences / secure storage.

---

### ⭐ **36. Caching?**

Local DB (SQFLite/Hive) to improve speed.

---

### **37. Network error handling?**

Retry, fallback UI, error states.

---

### **38. Large JSON parsing?**

Use **isolates** or `compute()`.

---

### **39. Pagination?**

Load more when reaching bottom using scroll listeners.

---

### ⭐ **40. File upload?**

Multipart form-data using Dio.

---

---

# ☁️ **FIREBASE & CLOUD SERVICES**

---

### ⭐ **41. Firebase Authentication?**

Handles login → returns UID + token.

---

### **42. Firestore vs Realtime DB**

* Firestore → modern, scalable
* RTDB → simple, faster

---

### ⭐ **43. FCM notifications?**

1. Get token
2. Handle message
3. Show notification (local plugin)

---

### **44. Crashlytics?**

Tracks crashes & stack traces in production.

---

### ⭐ **45. Firebase Storage?**

Upload/download images, videos.

---

### **46. FCM foreground/background?**

* Foreground → manual notification
* Background → OS handles

---

### **47. Dynamic links?**

Used for deep linking.
Yes, used via Firebase + GoRouter.

---

### **48. Securing Firebase rules?**

Use auth checks, validation, timestamps, role-based access.

---

---

# ⚡ **APP PERFORMANCE OPTIMIZATION**

---

### ⭐ **49. Optimize slow app?**

* const widgets
* pagination
* caching
* isolate for heavy tasks

---

### **50. Animation jank?**

Heavy work on UI thread.

---

### ⭐ **51. Reduce APK size?**

* AAB format
* Compress assets
* Tree-shake icons

---

### **52. Profile memory/CPU?**

Use DevTools → Performance tab.

---

### ⭐ **53. Lazy loading?**

Load only items when needed (ListView.builder).

---

---

# 🏛 **ARCHITECTURE & STRUCTURE**

---

### ⭐ **54. Clean Architecture?**

Divided into **presentation → domain → data** layers.

---

### **55. MVC vs MVVM vs BLoC**

* MVC: basic
* MVVM: ViewModel
* BLoC: event-state stream

---

### ⭐ **56. Why layered architecture?**

Maintainable + scalable + testable.

---

### **57. Project structure?**

Feature-based folders with data/presentation layers.

---

### ⭐ **58. Dependency injection?**

GetX DI / get_it DI to inject services.

---

---

# 📦 **DEPLOYMENT & DEVOPS**

---

### ⭐ **59. Generate APK/AAB**

```
flutter build apk --release
flutter build appbundle --release
```

---

### **60. Play Store release?**

Increase version → upload AAB → release track.

---

### ⭐ **61. App Signing?**

Authenticates developer identity.

---

### **62. App Store pipeline?**

Xcode archive → TestFlight → review → release.

---

### **63. Versioning?**

In `pubspec.yaml` → `version: 1.0.0+1`

---

---

# 🧪 **DEBUGGING & TESTING**

---

### ⭐ **64. Debug runtime errors?**

Breakpoints, logs, Crashlytics.

---

### **65. Flutter Inspector?**

Check constraints, layout issues.

---

### ⭐ **66. Unit testing?**

Test individual functions.

---

### **67. Widget tests?**

Test UI behavior, button press, widget render.

---

### ⭐ **68. Crash tracking?**

Crashlytics.

---

---

# 📱 **MOBILE DEVELOPMENT FUNDAMENTALS**

---

### ⭐ **69. App lifecycle**

`resumed → inactive → paused → detached`

---

### **70. Permissions?**

Using permission_handler package.

---

### ⭐ **71. Local storage?**

* Structured: SQFLite
* Key-value: SharedPreferences

---

### **72. Adaptive vs Responsive?**

* Responsive: screen size
* Adaptive: platform-oriented

---

### ⭐ **73. Method Channel?**

Calling native Android/iOS code.

---

---

# 🎭 **SCENARIO-BASED QUESTIONS**

---

### ⭐ **74. Random crash debugging?**

Check Crashlytics → replicate → fix → retest.

---

### **75. Slow API?**

Cache → pagination → async loading.

---

### ⭐ **76. Too many rebuilds?**

Use const, restructure widgets, use BLoC/GetX.

---

### **77. App freezes on large data?**

Move parsing to isolate.

---

### ⭐ **78. Custom animation plan?**

AnimationController + Tween + Curves.

---

### **79. Offline support?**

Local DB caching + sync queue.

---

### ⭐ **80. Wrong backend data?**

Validate → fallback → report backend issue.

---

---

# 👔 **HR QUESTIONS**

---

### ⭐ **81. Tell us about yourself.**

*(Customize with your intro.)*

---

### **82. Why should we hire you?**

Because I fit perfectly in Flutter, APIs, Firebase, BLoC, deployment.

---

### ⭐ **83. Why leave last company?**

For growth & challenging projects.

---

### **84. Strengths?**

Clean code, debugging, fast learning.

---

### ⭐ **85. Weaknesses?**

Too detail-oriented at times.

---

### **86. Future goal?**

Become senior Flutter engineer.

---

### ⭐ **87. Work environment?**

Collaborative & engineering-driven.

---

### **88. Team or solo?**

Both.

---

### ⭐ **89. Stress handling?**

Prioritize + communicate.

---

### **90. Expected salary?**

Market-standard based on expertise.

---

### ⭐ **91. Willing to learn new tech?**

Always.

---

### **92. Conflict resolution example?**

Misaligned API → communicated → resolved.

---

### ⭐ **93. Motivation?**

Building real impactful apps.

---

### **94. Biggest achievement?**

Successfully shipping AUSTTAA & Kambaii apps.

---

### ⭐ **95. Any questions for us?**

“What architecture do you use internally?”

---

---

# 📌 **QUESTIONS SPECIFIC TO MY CV**

---

### ⭐ **96. QP Social Media modules?**

Newsfeed, reactions, comments, reels, stories, groups, wallet, marketplace.

---

### **97. Reels upload/live stream?**

Video compression → API upload → RTMP streaming.

---

### ⭐ **98. CTG WASA App?**

Dashboard, complaints, billing modules.

---

### **99. AUSTTAA Chat?**

Firestore + streams + push notifications.

---

### ⭐ **100. Performance optimization?**

Pagination, caching, const widgets, minimizing rebuilds.

---

---

# 🧠 **ADVANCED FLUTTER & DART QUESTIONS (BONUS 20)**

---

### ⭐ **A1. What is RenderObject in Flutter?**

A low-level class responsible for layout, painting & hit detection.

---

### **A2. What is the difference between repaint boundary and layer?**

RepaintBoundary prevents full repaint → improves performance.

---

### ⭐ **A3. What is Skia?**

Flutter uses Skia graphics engine for drawing UI at 60–120 FPS.

---

### **A4. Explain Platform Channels deeply.**

Bi-directional bridge between Dart & native.

---

### ⭐ **A5. What is BuildOwner?**

Controls the lifecycle of elements during the build phase.

---

### **A6. How do you implement custom RenderBox?**

By overriding performLayout & paint.

---

### ⭐ **A7. What is tree shaking?**

Removes unused code during build.

---

### **A8. Difference between hot reload & stateful hot reload?**

Stateful preserves state; stateless reload rebuilds all.

---

### ⭐ **A9. What is ShaderMask?**

Applies gradients/shaders over widgets.

---

### **A10. How to improve list performance?**

Use ListView.builder, caching, AutomaticKeepAlive.

---

### ⭐ **A11. Explain microtasks in Dart.**

Higher priority asynchronous tasks.

---

### **A12. How Dart garbage collection works?**

Uses generational GC model.

---

### ⭐ **A13. What is the event loop in Dart?**

Controls execution of Future, Stream, microtasks.

---

### **A14. Explain AppBundle advantages.**

Smaller size, dynamic delivery.

---

### ⭐ **A15. What is isolate communication?**

Uses sendPort/receivePort.

---

### **A16. Why Flutter uses composition over inheritance?**

Allows flexible UI without deep inheritance chains.

---

### ⭐ **A17. Explain Hero animation mechanism.**

Matches widgets across routes using tags.

---

### **A18. How to create custom gestures?**

Using GestureRecognizer.

---

### ⭐ **A19. Performance optimization for animations?**

Use RepaintBoundary + avoid heavy computations.

---

### **A20. Code splitting in Flutter?**

Use deferred imports to load features lazily.

---

---


