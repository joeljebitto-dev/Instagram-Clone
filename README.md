# Instagram Clone

A simple Instagram-style social media web app built with React, Firebase, and Material UI. The app supports user authentication, image uploads, captions, and a feed of posts loaded from Firestore.

## Features

* React frontend built with Create React App
* Firebase email/password authentication
* Sign up modal
* Sign in modal
* Logout support
* Firestore-backed post feed
* Posts ordered by timestamp
* Firebase Storage image uploads
* Upload progress indicator
* Caption input for new posts
* Authenticated post creation
* Instagram-style header
* Material UI buttons, inputs, modals, avatar, and progress bar
* Reusable post component

## Tech Stack

* React
* Create React App
* JavaScript
* Firebase Authentication
* Cloud Firestore
* Firebase Storage
* Material UI
* CSS

## Project Structure

```text
Instagram-Clone/
├── public/
├── src/
│   ├── App.js
│   ├── App.css
│   ├── Post.js
│   ├── Post.css
│   ├── firebase.js
│   ├── index.js
│   └── index.css
├── package.json
└── README.md
```

## How It Works

Application flow:

```text
Load app
  ↓
Listen for Firebase auth state
  ↓
Load posts from Firestore ordered by timestamp
  ↓
Render Instagram-style feed
  ↓
User signs in or signs up
  ↓
Authenticated user uploads image and caption
  ↓
Image is stored in Firebase Storage
  ↓
Post metadata is saved to Firestore
  ↓
Feed updates in real time
```

## Firebase Features Used

| Firebase Service        | Purpose                                                                 |
| ----------------------- | ----------------------------------------------------------------------- |
| Firebase Authentication | User sign up, sign in, and logout                                       |
| Cloud Firestore         | Store post metadata such as username, caption, image URL, and timestamp |
| Firebase Storage        | Store uploaded post images                                              |

## Installation

Clone the repository:

```bash
git clone https://github.com/joeljebitto-dev/Instagram-Clone.git
cd Instagram-Clone
```

Install dependencies:

```bash
npm install
```

Or with Yarn:

```bash
yarn install
```

## Firebase Setup

Create a Firebase project from the Firebase Console.

Enable:

* Authentication with email/password sign-in
* Cloud Firestore
* Firebase Storage

Create or update the Firebase configuration file:

```text
src/firebase.js
```

The file should initialize Firebase and export the required services used by the app:

```js
import firebase from "firebase";

const firebaseApp = firebase.initializeApp({
  apiKey: "your-api-key",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "your-sender-id",
  appId: "your-app-id",
});

const db = firebaseApp.firestore();
const auth = firebase.auth();
const storage = firebase.storage();

export { db, auth, storage };
```

Do not commit production Firebase credentials or unrestricted security rules.

## Running the App

Start the development server:

```bash
npm start
```

Or with Yarn:

```bash
yarn start
```

Then open:

```text
http://localhost:3000
```

## Available Scripts

```bash
npm start
npm test
npm run build
```

Or with Yarn:

```bash
yarn start
yarn test
yarn build
```

## Build for Production

```bash
npm run build
```

The optimized production build will be generated in the `build/` directory.

## Firestore Data Model

Example `posts` document:

```js
{
  username: "Joel",
  caption: "My first post",
  imageUrl: "https://firebasestorage.googleapis.com/...",
  timestamp: firebase.firestore.FieldValue.serverTimestamp()
}
```

## Notes

* This is a frontend-focused Instagram clone.
* The app depends on Firebase for authentication, storage, and database persistence.
* Users must be signed in to create posts.
* The current image upload path uses the uploaded file name; unique IDs are recommended to avoid filename collisions.
* The project uses older Firebase namespaced SDK syntax.
* Security rules should be configured before deploying publicly.

## Future Improvements

* Add comments
* Add likes
* Add user profile pages
* Add profile image upload
* Add unique image file names for uploads
* Add loading and error states
* Add image type and file size validation
* Add responsive mobile layout improvements
* Add Firestore security rules documentation
* Add environment-based Firebase config
* Upgrade to the modular Firebase SDK
* Upgrade Material UI and React dependencies
* Add tests for auth and post rendering

## Author

Built by [Joel Jebitto](https://github.com/joeljebitto-dev).
