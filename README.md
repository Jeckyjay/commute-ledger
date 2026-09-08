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

```bash
# 1. Clone the repository
git clone https://github.com/Jeckyjay/commute-ledger.git
cd commute-ledger

# 2. Install dependencies
npm install
# or
yarn install

# 3. Install Android dependencies (if not already installed)
# Make sure you have Android SDK, NDK, and JDK installed
# Update: Android SDK: API 34+, Build Tools: 34.0.0+

# 4. Start Metro bundler (in one terminal)
npm run android:dev
# or
yarn android:dev

# 5. Build and run on Android (in another terminal)
npm run android:build
# or
yarn android:build

# To build release APK:
npm run android:release
```

#### Project Structure
```
commute-ledger/
├── android/              # Android native code
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
