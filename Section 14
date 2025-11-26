# 🧠 **SECTION 14 — ADVANCED FLUTTER & DART QUESTIONS (A1–A20)**

---

# ⭐ **A1. RenderObject**

* Low-level class responsible for layout, painting, and hit-testing.
* Example: Custom layout widgets extend `RenderBox`.

---

# **A2. RepaintBoundary vs Layer**

* **RepaintBoundary** prevents unnecessary repaint
* **Layer** is a composited drawing layer

---

# ⭐ **A3. Skia**

* Graphics engine Flutter uses to draw UI at 60–120 FPS.

---

# **A4. Platform Channels Deep Dive**

* Bi-directional bridge between Dart and native (Android/iOS)
* Example:

```dart
MethodChannel('com.app/channel').invokeMethod('getBatteryLevel');
```

---

# ⭐ **A5. BuildOwner**

* Manages lifecycle of elements during build phase

---

# **A6. Custom RenderBox**

* Override `performLayout` & `paint`

```dart
class MyBox extends RenderBox {
  @override
  void performLayout() => size = constraints.biggest;
  @override
  void paint(PaintingContext context, Offset offset) {}
}
```

---

# ⭐ **A7. Tree shaking**

* Removes unused code during compilation → smaller APK/AAB

---

# **A8. Hot reload vs Stateful hot reload**

* Stateful preserves widget state
* Stateless rebuilds everything

---

# ⭐ **A9. ShaderMask**

* Applies gradient/shader on widget

```dart
ShaderMask(
  shaderCallback: (rect) => LinearGradient(colors: [Colors.red, Colors.blue]).createShader(rect),
  child: Text('Hello', style: TextStyle(color: Colors.white)),
)
```

---

# **A10. Improve list performance**

* `ListView.builder`
* Cache items
* Use `AutomaticKeepAliveClientMixin`

---

# ⭐ **A11. Microtasks in Dart**

* Higher priority async tasks than normal event queue
* Example: `scheduleMicrotask(() => print("micro"));`

---

# **A12. Dart garbage collection**

* Generational GC model (new/old objects)
* Automatic memory cleanup

---

# ⭐ **A13. Dart event loop**

* Controls execution of Future, Stream, and microtasks
* Ensures asynchronous operations execute in order

---

# **A14. AppBundle advantages**

* Smaller app size
* Dynamic delivery for different devices

---

# ⭐ **A15. Isolate communication**

* `sendPort` / `receivePort`
* Example:

```dart
final receivePort = ReceivePort();
Isolate.spawn(worker, receivePort.sendPort);
```

---

# **A16. Composition over inheritance**

* Use widget composition for flexibility instead of deep inheritance chains

---

# ⭐ **A17. Hero animation mechanism**

* Match widgets across routes using **tag**

```dart
Hero(tag: 'logo', child: Image.asset('logo.png'))
```

---

# **A18. Custom gestures**

* Extend `GestureRecognizer`
* Example: Drag, pinch, rotate

---

# ⭐ **A19. Performance optimization for animations**

* Use `RepaintBoundary`
* Avoid heavy computations during build

---

# **A20. Code splitting**

* Use **deferred imports** to load features lazily

```dart
import 'feature.dart' deferred as feature;
await feature.loadLibrary();
feature.run();
```

---

