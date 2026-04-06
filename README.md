# 🤖 - repo name: apk-init - Master Android Init

> **One-Click Android Project Boilerplate via GitHub Actions**

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-Automated-blue?logo=githubactions)
![Android](https://img.shields.io/badge/Android-SDK_33-green?logo=android)
![Java](https://img.shields.io/badge/Java-17-orange?logo=openjdk)
![Gradle](https://img.shields.io/badge/Gradle-8.1.1-blue?logo=gradle)

---

## 📋 Overview

**Master Android Init** is a GitHub Actions workflow that automatically generates a complete, ready-to-build Android project structure directly in your repository — no local setup required.

Perfect for:
- 🚀 Rapid prototyping
- 🧪 Testing CI/CD pipelines
- 📦 Template repositories
- 👥 Onboarding new Android developers

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔧 **Auto Gradle Wrapper** | Bypasses Gradle 9.x compatibility issues by injecting wrapper v8.1.1 |
| 📁 **Complete Project Structure** | Generates `app/`, `src/main/`, resources, and manifests |
| 🧱 **Modern Android Config** | Compile SDK 33, Min SDK 24, AndroidX & Jetifier enabled |
| 🌐 **WebView-Ready** | Includes `INTERNET` permission for web-based apps |
| 📦 **Dependencies Preloaded** | AppCompat & Material Design libraries included |
| 🔄 **Auto Commit & Push** | Generated files are committed back to your repo automatically |

---

## 🚀 How to Use

### Option 1: Manual Trigger (Recommended)

1. Copy `.github/workflows/master-android-init.yml` into your repository
2. Go to **Actions** → **Master Android Init** → **Run workflow**
3. Select your branch and click **Run workflow**
4. Wait ~1-2 minutes for the job to complete
5. ✅ Your Android project files will appear in your repo!

### Option 2: Fork & Customize

```bash
# 1. Fork this repo
# 2. Edit the workflow file:
#    - Change package name: PKG="com.yourcompany.yourapp"
#    - Adjust SDK versions, dependencies, or resources
# 3. Run the workflow in your fork
```

---

## 📦 What Gets Generated

```
📦 Your Repo
├── 📄 settings.gradle          # Project config with ':app' module
├── 📄 gradle.properties        # AndroidX + Jetifier enabled
├── 📄 build.gradle             # Root build script + AGP 8.1.1
├── 📁 app/
│   ├── 📄 build.gradle         # App module config
│   └── 📁 src/main/
│       ├── 📄 AndroidManifest.xml  # Manifest with INTERNET permission
│       ├── 📁 java/com/johirx/webinapp/
│       │   └── 📄 MainActivity.java
│       ├── 📁 res/
│       │   ├── 📁 layout/activity_main.xml
│       │   ├── 📁 values/
│       │   └── 📁 drawable/
│       └── 📁 assets/
└── 📁 gradle/wrapper/          # Gradle Wrapper binaries (v8.1.1)
```

### 🔑 Default Configuration

```gradle
android {
    namespace 'com.johirx.webinapp'
    compileSdk 33
    defaultConfig {
        applicationId "com.johirx.webinapp"
        minSdk 24
        targetSdk 33
        versionCode 1
        versionName "1.0"
    }
}
```

---

## ⚙️ Customization Guide

Edit the workflow file before running to tailor your project:

### Change Package Name
```yaml
PKG="com.yourcompany.yourapp"  # Update in Step 2
```

### Modify SDK Versions
```gradle
compileSdk 34      # Latest stable
minSdk 21          # Wider device support
targetSdk 33
```

### Add Dependencies
```gradle
dependencies {
    implementation 'androidx.webkit:webkit:1.9.0'  // For WebView
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    // ...add more as needed
}
```

### Add Permissions
Edit the `AndroidManifest.xml` section in Step 2:
```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```

---

## 🛠️ Requirements

- ✅ GitHub repository with **Actions enabled**
- ✅ Workflow permissions: `contents: write` (to push generated files)
- ✅ Java 17 (handled automatically by the workflow)
- ✅ No local Android SDK needed!

---

## 🔐 Security Notes

> ⚠️ This workflow pushes code back to your repository automatically.

- Review the generated files before merging to production branches
- Consider running on a feature branch first: `git checkout -b android-init`
- The workflow uses `action@github.com` as commit author — customize in Step 3 if needed

---

## 🧩 Example: Turn This Into a WebView App

After the workflow completes, enhance `MainActivity.java`:

```java
import android.webkit.WebView;
import android.webkit.WebSettings;

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    WebView webView = new WebView(this);
    WebSettings settings = webView.getSettings();
    settings.setJavaScriptEnabled(true);
    webView.loadUrl("https://yourwebsite.com");
    setContentView(webView);
}
```

And update `activity_main.xml` or remove it since we're setting content programmatically.

---

## 🤝 Contributing

Found a bug or want to add a feature?

1. Fork the repo
2. Create your feature branch: `git checkout -b feat/awesome-idea`
3. Commit your changes: `git commit -m 'Add awesome feature'`
4. Push to the branch: `git push origin feat/awesome-idea`
5. Open a Pull Request 🎉

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

```
MIT License

Copyright (c) 2026 Johirx

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

> 💡 **Pro Tip**: Save this workflow in a [GitHub Template Repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository) to instantly bootstrap new Android projects with one click!

**Happy Coding!** 🎯📱✨
