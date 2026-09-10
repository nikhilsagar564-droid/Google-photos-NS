# CloudGallery

A Flutter + Firebase Google Photos-style starter app.

## 1. Prerequisites

Install:
- Flutter
- Android Studio / Android SDK
- Node.js 20+
- Firebase CLI
- FlutterFire CLI

Never put an OpenAI API key inside Flutter/Dart code or an APK.

## 2. Create Firebase project

Create a Firebase project, then enable:
- Authentication -> Email/Password
- Cloud Firestore
- Cloud Storage

From the project root:

```bash
firebase login
dart pub global activate flutterfire_cli
flutterfire configure
```

Choose Android and your Firebase project.

This generates:

```text
lib/firebase_options.dart
```

Do not replace that generated file with a fake one.

## 3. Install Flutter packages

```bash
flutter pub get
```

## 4. Initialize Firebase Functions

The functions folder is already included.

```bash
cd functions
npm install
cd ..
```

## 5. OpenAI secret

The API key must stay server-side.

```bash
firebase functions:secrets:set OPENAI_API_KEY
```

When prompted, enter your NEW key.

Do NOT put the key in:
- lib/main.dart
- .env shipped inside the APK
- AndroidManifest.xml
- GitHub
- Firestore
- Storage

Then deploy:

```bash
firebase deploy --only functions
```

## 6. Deploy Firebase rules

```bash
firebase deploy --only firestore:rules,storage
```

## 7. Run

```bash
flutter run
```

## 8. Build APK

```bash
flutter clean
flutter pub get
flutter build apk --release
```

APK:

```text
build/app/outputs/flutter-apk/app-release.apk
```

## What this starter already does

- Email/password authentication
- Multi-image selection
- Firebase Storage upload
- Firestore media metadata
- Cloud gallery stream
- Search by filename/labels
- Favorites
- Trash/restore/permanent delete
- Full-screen image viewer
- Share download URL
- Dark/light theme support through Material 3
- Secure user-isolated Firestore/Storage rules
- Server-side OpenAI function
- Server-side media activity trigger

## Important

This is a real Firebase-backed MVP, not a pixel-for-pixel copy of Google's proprietary application. Features such as face grouping, memories, automatic device backup while the app is closed, advanced photo editing, OCR, map clustering, shared albums and sophisticated AI vision require additional modules.
