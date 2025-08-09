# React Native Firebase App

A basic React Native mobile application built with Expo and Firebase integration, featuring user authentication and a simple notes management system.

## Features

- **User Authentication**: Sign up and sign in with email/password using Firebase Auth
- **Real-time Notes**: Create, view, and delete notes stored in Firebase Firestore
- **Cross-platform**: Runs on both iOS and Android
- **Modern UI**: Clean and responsive user interface
- **Real-time Updates**: Notes are synchronized in real-time across devices

## Tech Stack

- **React Native** with Expo
- **Firebase** (Authentication & Firestore)
- **React Navigation** for navigation
- **JavaScript** ES6+

## Prerequisites

Before running this project, make sure you have:

1. Node.js (version 14 or higher)
2. npm or yarn
3. Expo CLI (`npm install -g @expo/cli`)
4. A Firebase project set up

## Firebase Setup

1. Go to the [Firebase Console](https://console.firebase.google.com/)
2. Create a new project or use an existing one
3. Enable Authentication with Email/Password provider
4. Create a Firestore database
5. Get your Firebase configuration from Project Settings
6. Replace the configuration in `firebase.js` with your actual Firebase config

```javascript
const firebaseConfig = {
  apiKey: "your-api-key-here",
  authDomain: "your-project-id.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project-id.appspot.com",
  messagingSenderId: "your-sender-id",
  appId: "your-app-id"
};
```

## Installation

1. Clone or download this project
2. Navigate to the project directory:
   ```bash
   cd your-project-directory
   ```
3. Install dependencies:
   ```bash
   npm install
   ```
4. Update Firebase configuration in `firebase.js`
5. Start the development server:
   ```bash
   npm start
   ```

## Available Scripts

- `npm start` - Start the Expo development server
- `npm run android` - Run on Android device/emulator
- `npm run ios` - Run on iOS simulator (macOS only)
- `npm run web` - Run in web browser

## Project Structure

```
├── screens/
│   ├── LoginScreen.js      # Authentication screen
│   └── HomeScreen.js       # Main app screen with notes
├── components/
│   └── Button.js           # Reusable button component
├── firebase.js             # Firebase configuration
├── App.js                  # Main app component with navigation
└── README.md
```

## How to Use

1. Launch the app using `npm start`
2. On the login screen, you can:
   - Sign in with existing credentials
   - Create a new account by toggling to "Sign Up"
3. Once authenticated, you'll see the home screen where you can:
   - View your notes
   - Add new notes using the "Add Note" button
   - Delete notes by tapping the delete button
   - Sign out using the "Sign Out" button

## Firebase Security Rules

For production use, make sure to set up proper Firestore security rules. Here's a basic example:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /notes/{document} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.userId;
    }
  }
}
```

## Development Notes

- The app uses Firebase Authentication for user management
- Notes are stored in Firestore with user-specific access
- Real-time listeners are used for live updates
- The app includes proper error handling and loading states
- Cross-platform compatible with iOS and Android

## Troubleshooting

If you encounter issues:

1. Make sure your Firebase configuration is correct
2. Ensure Firebase Authentication and Firestore are enabled
3. Check that you have the latest versions of dependencies
4. Clear your Expo cache: `expo r -c`

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is open source and available under the MIT License.
