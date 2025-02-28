# Biometric Authentication in Flutter

## Overview
This Flutter project implements biometric authentication using the `local_auth` package, allowing users to authenticate via fingerprint or facial recognition. This enhances security and improves the user experience by eliminating the need for passwords.

## Features
- **Fingerprint & Face ID Authentication**
- **Fallback to PIN/Password if Biometrics Fail**
- **Seamless Integration with Flutter Apps**
- **Secure & Fast Authentication Mechanism**

## Technologies Used
- **Flutter** (Latest Stable Version)
- **Dart**
- **local_auth: ^2.3.0**

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/biometric_auth_flutter.git
   ```
2. Navigate to the project directory:
   ```sh
   cd biometric_auth_flutter
   ```
3. Install dependencies:
   ```sh
   flutter pub get
   ```
4. Run the application:
   ```sh
   flutter run
   ```

## Configuration
### Android
1. Update `android/app/build.gradle` with the required permissions:
   ```gradle
   android {
       compileSdkVersion 33
       defaultConfig {
           minSdkVersion 23
       }
   }
   ```
2. Add the necessary permissions in `AndroidManifest.xml`:
   ```xml
   <uses-permission android:name="android.permission.USE_BIOMETRIC"/>
   <uses-feature android:name="android.hardware.fingerprint" android:required="false"/>
   ```

### iOS
1. Add the following key-value pairs in `ios/Runner/Info.plist`:
   ```xml
   <key>NSFaceIDUsageDescription</key>
   <string>We use Face ID to authenticate you securely.</string>
   ```
2. Enable biometric authentication capabilities in Xcode.

## Implementation
### Import the Package
```dart
import 'package:local_auth/local_auth.dart';
```

### Initialize Biometric Authentication
```dart
final LocalAuthentication auth = LocalAuthentication();

Future<bool> authenticateUser() async {
  bool isAuthenticated = false;
  try {
    isAuthenticated = await auth.authenticate(
      localizedReason: 'Scan your fingerprint or face to authenticate',
      options: const AuthenticationOptions(biometricOnly: true),
    );
  } catch (e) {
    print("Error: $e");
  }
  return isAuthenticated;
}
```

### Call the Authentication Function
```dart
void onLoginPressed() async {
  bool isAuthenticated = await authenticateUser();
  if (isAuthenticated) {
    print("Authentication Successful");
  } else {
    print("Authentication Failed");
  }
}
```

## Screenshots
![Biometric Authentication](https://your-image-link.com)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author
[Your Name](https://github.com/yourusername)

---
Feel free to contribute, report issues, or suggest improvements!

