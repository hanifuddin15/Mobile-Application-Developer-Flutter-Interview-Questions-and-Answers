

# ⚡ **SECTION 6 — APP PERFORMANCE OPTIMIZATION (Questions 49–53)**

This section focuses on **making Flutter apps fast, smooth, and memory-efficient**. It includes practical tips, examples, and tools.

---

# ⭐ **49. How to optimize a slow Flutter app?**

### ✔ Common Causes

* Large widget rebuilds
* Heavy work on UI thread
* Large images or assets
* Inefficient state management

### ✔ Solutions

1. **Use const widgets**

   ```dart
   const Text('Hello World');
   ```

2. **Lazy loading / Pagination**

   ```dart
   ListView.builder(
     itemCount: items.length,
     itemBuilder: (context, index) {
       return ListTile(title: Text(items[index]));
     },
   );
   ```

3. **Caching data**
   Use Hive or SQFLite to avoid repeated API calls.

4. **Move heavy work to Isolates**

   ```dart
   compute(parseLargeJson, jsonString);
   ```

5. **Profile & monitor**
   Use Flutter DevTools → Performance tab → check jank.

---

# **50. How to fix animation jank?**

* Heavy work (API, parsing, DB) should **not run on UI thread**.
* **Use RepaintBoundary** for complex widgets.
* Prefer **TweenAnimationBuilder** or **AnimationController**.
* Avoid rebuilding the whole tree unnecessarily.

---

# ⭐ **51. How to reduce APK / App size?**

* Use **AAB** format:

  ```bash
  flutter build appbundle --release
  ```
* **Compress images and assets** (WebP format recommended)
* **Tree shaking** removes unused code
* Use **deferred imports** to lazy load features

---

# **52. How to profile memory/CPU?**

* Open **Flutter DevTools** → **Performance / Memory**
* Look for:

  * Jank frames
  * Memory spikes
  * Widget rebuild frequency

---

# ⭐ **53. Lazy loading technique?**

* Load only the visible items
* Use `ListView.builder`, `GridView.builder`
* **Example:**

```dart
ListView.builder(
  itemCount: largeList.length,
  itemBuilder: (context, index) {
    return Card(child: Text(largeList[index]));
  },
);
```

---


