
# 📦 **SECTION 8 — DEPLOYMENT & DEVOPS (Questions 59–63)**

---

# ⭐ **59. How to generate APK / AAB**

```bash
flutter build apk --release
flutter build appbundle --release
```

* **APK** → installable directly
* **AAB** → preferred for Play Store, smaller download size

---

# **60. Play Store release steps**

1. Increase version in `pubspec.yaml`

   ```yaml
   version: 1.0.1+2
   ```
2. Build **AAB**
3. Upload to Google Play Console → Internal / Alpha / Beta → Production

---

# ⭐ **61. App Signing**

* Ensures your app is trusted and updates are allowed.
* Create a **keystore**:

```bash
keytool -genkey -v -keystore key.jks -alias mykey
```

* Configure `key.properties` in Gradle.

---

# **62. App Store pipeline (iOS)**

* Xcode Archive → Upload to App Store → TestFlight → Review → Release

---

# ⭐ **63. Versioning**

* Semantic versioning:

  ```
  version: major.minor+build
  ```

  Example:

  ```yaml
  version: 1.2.0+10
  ```

---
