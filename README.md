# Commute Ledger

A smart expense-sharing app for office carpools. Automatically calculates payments, tracks settlements, and manages car rotation — no calculator required.

## Features

✅ **One-time setup** — Define your group, members, and rates once  
✅ **Daily tracking** — Confirm car, mark absent members, done  
✅ **Smart calculations** — Auto-calculates who owes what (₹75 one-way, ₹150 return)  
✅ **Multiple cars** — Split the group across available vehicles  
✅ **Payment tracking** — Mark payments with pending balance tracking  
✅ **Monthly settlement** — Automatic settlement with clear payment instructions  
✅ **Car rotation** — Fair distribution of driving load  
✅ **Offline-first** — No internet required, all data stored locally  
✅ **Backup & restore** — Protect your data with local backups  
✅ **WhatsApp sharing** — Export monthly summary for group messaging  

## Quick Start

### For Users
1. **Set up your group** — Add members and set rates (₹75 one-way, ₹150 return)
2. **Daily workflow** — Open app → Confirm car → Mark absent members → Done
3. **Track payments** — Mark payments as received
4. **Monthly settlement** — View who owes whom and share with group

### For Developers

#### Tech Stack
- **Frontend:** React Native (iOS/Android)
- **Backend:** Local SQLite database
- **State Management:** Redux
- **UI Framework:** Native Base / React Native Paper

#### Prerequisites
- Node.js 16+
- Android SDK (for Android development)
- Xcode (for iOS development)
- React Native CLI

#### Build Android App

**Step 1: Install Android Development Environment**

```bash
# On macOS with Homebrew
brew install android-sdk
brew install android-ndk

# On Windows/Linux, download from:
# https://developer.android.com/studio

# Set environment variables in ~/.bashrc or ~/.zshrc
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

**Step 2: Clone & Install Project**

```bash
# Clone the repository
git clone https://github.com/Jeckyjay/commute-ledger.git
cd commute-ledger

# Install Node dependencies
npm install
# or
yarn install
```

**Step 3: Build Android Debug APK**

```bash
# Build debug APK
npm run android:build
# or
cd android && ./gradlew assembleDebug && cd ..

# APK will be generated at:
# android/app/build/outputs/apk/debug/app-debug.apk
```

**Step 4: Build Android Release APK**

```bash
# Generate release keystore (first time only)
keytool -genkey -v -keystore my-release-key.keystore -keyalg RSA -keysize 2048 -validity 10000 -alias my-key-alias

# Build release APK
npm run android:release
# or
cd android && ./gradlew assembleRelease && cd ..

# APK will be generated at:
# android/app/build/outputs/apk/release/app-release.apk
```

**Step 5: Run on Device/Emulator**

```bash
# Option A: Using React Native CLI
npx react-native run-android

# Option B: Using Android Studio
# Open the android/ folder in Android Studio and click Run

# Option C: Manual installation
adb install android/app/build/outputs/apk/debug/app-debug.apk
```

#### Project Structure
```
commute-ledger/
├── android/              # Android native code & gradle config
├── ios/                  # iOS native code
├── src/
│   ├── components/       # React Native components
│   ├── screens/          # App screens
│   ├── services/         # Database & business logic
│   ├── store/            # Redux state management
│   ├── navigation/       # Navigation stack
│   └── utils/            # Helper functions
├── __tests__/            # Test files
├── app.json              # App configuration
├── package.json          # Dependencies
└── README.md
```

#### Key Features Implementation

1. **Setup Screen** — Group configuration
2. **Daily Screen** — Trip recording and settlements
3. **Payment Screen** — Payment tracking
4. **Settlement Screen** — Monthly summary with payment instructions
5. **Car Management** — Availability and rotation
6. **Settings** — Backup/restore, data export

## Architecture

### Data Model

**Groups**
```
- groupId, name, createdAt, updatedAt
```

**Members**
```
- memberId, groupId, name, hasCar, createdAt
```

**Rates**
```
- rateId, groupId, oneWay, return, createdAt
```

**Trips**
```
- tripId, groupId, carOwnerId, date, direction (morning/evening), passengers []
```

**Payments**
```
- paymentId, tripId, fromMemberId, toMemberId, amount, status (pending/paid), createdAt
```

**CarUsage**
```
- usageId, carOwnerId, date, tripCount (for rotation)
```

## Development Workflow

1. **Features** — Each feature is tracked as a GitHub Issue
2. **Branches** — Create feature branches (`feature/settlement-calculation`)
3. **Tests** — Unit tests for calculations, integration tests for flows
4. **Build** — Automated builds for Android/iOS

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit changes with clear messages
4. Push to your branch
5. Open a Pull Request

## License

MIT License - See LICENSE file for details

## Support

For issues, feature requests, or questions, open a GitHub Issue.

---

**Version:** 0.1.0 (Initial Setup)  
**Status:** In Development
