
# 🧪 **SECTION 9 — DEBUGGING & TESTING (Questions 64–68)**

---

# ⭐ **64. Debug runtime errors**

* Use **breakpoints**
* Use **print/logging**
* Use **Flutter DevTools**
* Crashlytics for production errors

---

# **65. Flutter Inspector**

* Check constraints
* Widget tree visualization
* Layout issues
* Detect unnecessary rebuilds

---

# ⭐ **66. Unit testing example**

```dart
int add(int a, int b) => a + b;

void main() {
  test('Addition works', () {
    expect(add(2,3), 5);
  });
}
```

---

# **67. Widget tests example**

```dart
testWidgets('Button tap increments counter', (WidgetTester tester) async {
  await tester.pumpWidget(MyApp());
  await tester.tap(find.byIcon(Icons.add));
  await tester.pump();
  expect(find.text('1'), findsOneWidget);
});
```

---

# ⭐ **68. Crash tracking with Crashlytics**

* Records unhandled exceptions
* Shows device info, OS, app version
* Use `FlutterError.onError`

---

