

# ✅ **SECTION 1: CORE FLUTTER QUESTIONS (Detailed Answers + Examples + Code)**



---

# 🔥 **SECTION 1 — CORE FLUTTER QUESTIONS (Highly Detailed)**

*(Each answer has examples + code + diagrams + best practices)*

---

# ⭐ **1. What is Flutter and why do you prefer it?**

### ✔ Detailed Explanation

Flutter is Google’s open-source UI toolkit that allows developers to build **cross-platform apps** (Android, iOS, Web, Desktop) using a **single codebase**.
It uses the **Dart language** and the **Skia rendering engine** to draw every pixel directly on the screen — meaning **no OEM UI components**.

### ✔ Why I Prefer Flutter

1. **Single codebase** → Build once, run everywhere
2. **Fast development** → Hot reload, hot restart
3. **Beautiful UI** → Custom designs with no platform limitations
4. **High performance (60–120 FPS)**
5. **Huge ecosystem & community**

---

# ⭐ **2. Explain the widget tree.**

### ✔ Detailed Explanation

Everything in Flutter is a widget — layouts, text, buttons, animations, even the entire app.

Flutter builds UI in a **tree structure**, where widgets are nested inside each other.

### ✔ Simple Diagram

```
MaterialApp
 └── Scaffold
      ├── AppBar
      └── Body
           └── Column
                ├── Text("Hello")
                └── ElevatedButton("Click")
```

### ✔ Why It Matters

Flutter updates UI by **rebuilding portions of the widget tree**, making UI reactive and fast.

---

# ⭐ **3. StatelessWidget vs StatefulWidget**

### ✔ Explanation

| StatelessWidget        | StatefulWidget                        |
| ---------------------- | ------------------------------------- |
| No internal state      | Has internal mutable state            |
| UI does not change     | UI updates when state changes         |
| Lightweight            | Slightly heavier                      |
| Ideal for static pages | Ideal for forms, animations, API data |

### ✔ Example Code

**Stateless:**

```dart
class MyText extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text("Hello");
  }
}
```

**Stateful:**

```dart
class Counter extends StatefulWidget {
  @override
  _CounterState createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int count = 0;

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: () => setState(() => count++),
      child: Text("Count: $count"),
    );
  }
}
```

---

# ⭐ **4. How does the Flutter rendering pipeline work?**

### ✔ Full Pipeline Breakdown

```
Widget tree → Element tree → Render tree → Layout → Paint → Layer → GPU → Screen
```

### ✔ Steps Explained

1. **Build phase**
   Creates widget → element → render objects.

2. **Layout phase**
   Each widget receives constraints (size rules).
   Determines **size & position**.

3. **Paint phase**
   Widgets draw themselves onto a canvas.

4. **Layer composition**
   Flutter combines multiple layers (opacity, transform, etc.).

5. **Rasterization**
   GPU converts layers into pixels.

---

# ⭐ **5. What are keys in Flutter & when do you use them?**

### ✔ Explanation

Keys help Flutter identify widgets uniquely during rebuilds.
They prevent UI from **losing state** when the order of widgets changes.

### ✔ Common Use Cases

* Reorderable lists
* AnimatedList
* Form fields
* PageView children
* When widgets swap positions

### ✔ Example

```dart
ListView(
  children: [
    Container(key: ValueKey("A")),
    Container(key: ValueKey("B")),
  ],
);
```

Without keys, Flutter might mix their states during reorder.

---

# ⭐ **6. Hot Reload vs Hot Restart**

### ✔ Hot Reload

* Injects code changes into running app
* **Preserves state**
* Good for UI changes

### ✔ Hot Restart

* Fully restarts the application
* **State resets**
* Used when app breaks or code change affects global state

---

# ⭐ **7. What is BuildContext?**

### ✔ Explanation

BuildContext is a reference to a widget’s position in the widget tree.
It helps you:

* Access parent widgets
* Access inherited data (Theme, MediaQuery)
* Navigate
* Show dialogs, snackbars

### ✔ Example

```dart
final width = MediaQuery.of(context).size.width;
```

### ✔ BuildContext Rule

❗ *Do NOT use BuildContext during initState unless using WidgetsBinding.*

---

# ⭐ **8. How do you handle navigation in Flutter?**

### ✔ Methods I Use

---

## ✅ **Using GoRouter** (Recommended modern approach)

```dart
final GoRouter router = GoRouter(
  routes: [
    GoRoute(path: '/', builder: (context, _) => HomePage()),
    GoRoute(path: '/details', builder: (context, _) => DetailsPage()),
  ],
);
```

Navigate:

```dart
context.go('/details');
```

---

## ✅ **Using GetX**

```dart
Get.to(DetailsPage());
```

---

## ✅ **Navigator 2.0** → Good for large apps

More control over navigation stack.

---

# ⭐ **9. What is InheritedWidget? Have you used it?**

### ✔ Explanation

InheritedWidget is a low-level way to pass data down the widget tree without using constructors.

Provider, Riverpod internally use it.

### ✔ Example

```dart
class AppSettings extends InheritedWidget {
  final String theme;

  AppSettings({required this.theme, required Widget child}) : super(child: child);

  @override
  bool updateShouldNotify(covariant AppSettings oldWidget) {
    return theme != oldWidget.theme;
  }
}
```

---

# ⭐ **10. What is an Isolate in Flutter?**

### ✔ Explanation

An isolate is a separate thread with its own memory.
Used for heavy tasks:

* JSON parsing
* Encryption
* Image compression
* File operations

### ✔ Example using `compute()`

```dart
final result = await compute(parseJson, jsonString);
```

---

# ⭐ **11. How do you write responsive UI?**

### ✔ Tools I Use

* MediaQuery
* LayoutBuilder
* Expanded / Flexible
* Flutter Responsive Framework
* Custom breakpoints (mobile/tablet/web)

### ✔ Example

```dart
if (MediaQuery.of(context).size.width > 600) {
  return TabletUI();
} else {
  return MobileUI();
}
```

---

# ⭐ **12. What is Flutter DevTools?**

### ✔ Features

* Memory profiler
* CPU profiler
* Rebuild tracking
* Layout overflow debugger
* Network calls monitor
* Frame rendering analysis

### ✔ Example Use

Finding widget rebuild problems using "Repaint Rainbow".

---

# ⭐ **13. Explain Widget Tree vs Element Tree**

### ✔ Widget Tree

* Immutable
* Blueprint of UI

### ✔ Element Tree

* Long-lived
* Maintains widget state
* Connected to Render Objects

### ✔ Diagram

```
Widget Tree        Element Tree
-----------       ----------------
Text("A")   →     Element #1
Container   →     Element #2
Button      →     Element #3
```

---

# ⭐ **14. Lifecycle of StatefulWidget**

### ✔ Full Lifecycle

```
createState
initState
didChangeDependencies
build
didUpdateWidget
setState → build
deactivate
dispose
```

---

# ⭐ **15. What causes unnecessary rebuilds & how to prevent them?**

### ✔ Causes

* Using setState on entire screen
* Not using const widgets
* Rebuilding parents instead of children
* Anonymous functions inside build

### ✔ Fixes

✔ Use const
✔ Extract widgets
✔ Use selectors (Provider)
✔ Use BlocBuilder with specific conditions
✔ Use Keys

---

# ✅ **SECTION 1 COMPLETED**

