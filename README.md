# DeviceManager

DeviceManager is a full-stack inventory and resale value tracking app built with Next.js, TypeScript, Firebase, and the eBay Browse API. It helps users track their personal devices and games, compare purchase prices against current market values, upload item images, archive sold items, and view price history over time.

## Features

- Google login with Firebase Authentication
- User-specific cloud data with Firestore
- Device inventory tracking
- Game collection tracking
- eBay market price lookup
- Manual price override
- Price history tracking
- Detail pages for devices and games
- Firebase image upload
- Archive and sold-profit tracking
- Search, sort, and filters
- Responsive dashboard layout
- Protected user data with Firebase security rules

## Tech Stack

- Next.js
- React
- TypeScript
- Tailwind CSS
- Firebase Authentication
- Firebase Firestore
- Firebase Storage
- eBay Browse API
- Vercel

## Pages

```txt
/                 Devices dashboard
/games            Games dashboard
/devices/[id]     Device detail page
/games/[id]       Game detail page
/import-devices   Bulk import helper page
/api/market-price eBay market price API route
```

## Project Structure

```txt
app/
  api/market-price/
  devices/[id]/
  games/
  games/[id]/
  import-devices/

components/
  auth/
  devices/
  games/
  shared/

data/
  devices.ts
  games.ts

lib/
  cloudInventory.ts
  date.ts
  firebase.ts
  format.ts
  imageUpload.ts
  market.ts
  priceHistory.ts
  storage.ts

types/
  inventory.ts
```

## Environment Variables

Create a `.env.local` file in the project root.

```txt
EBAY_CLIENT_ID=your_ebay_client_id
EBAY_CLIENT_SECRET=your_ebay_client_secret

NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_firebase_auth_domain
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_firebase_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_firebase_storage_bucket
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_firebase_messaging_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_firebase_app_id
```

Do not commit `.env.local`.

## Firebase Setup

Enable the following Firebase services:

- Authentication
- Firestore Database
- Storage

Enable Google sign-in:

```txt
Firebase Console
→ Authentication
→ Sign-in method
→ Google
→ Enable
```

## Firestore Rules

```txt
rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Firebase Storage Rules

```txt
rules_version = '2';

service firebase.storage {
  match /b/{bucket}/o {
    match /users/{userId}/{allPaths=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Local Development

Install dependencies:

```bash
npm install
```

Run the development server:

```bash
npm run dev
```

Open:

```txt
http://localhost:3000
```

Build the project:

```bash
npm run build
```

## Deployment

The project is deployed with Vercel.

Deploy preview:

```bash
npx vercel@latest
```

Deploy production:

```bash
npx vercel@latest --prod
```

Add the same environment variables from `.env.local` to Vercel:

```txt
Vercel Dashboard
→ Project
→ Settings
→ Environment Variables
```

After deployment, add the Vercel domain to Firebase:

```txt
Firebase Console
→ Authentication
→ Settings
→ Authorized domains
```

Example:

```txt
your-project.vercel.app
```

## Security Notes

- Firebase public keys are safe to expose because Firebase security depends on Firestore and Storage rules.
- eBay credentials must stay private and should only be stored in `.env.local` and Vercel environment variables.
- User inventory data is stored under `/users/{userId}` and protected by Firebase Auth.
- Uploaded images are stored under `/users/{userId}` in Firebase Storage.

## Current Limitations

- Price lookup depends on eBay search results, so market prices may need manual adjustment.
- Price history only starts after price checks are made.
- The app currently supports personal inventory tracking, not multi-user sharing.
- Rate limiting has not been added yet.

## Future Improvements

- Add CSV export
- Add price alerts
- Add dashboard analytics
- Add better game-specific fields such as region, manual included, case included, and authenticity status
- Add item tags
- Add rate limiting for price checks
- Add shared public collection view

## Resume Description

Built a full-stack inventory and resale value tracking application using Next.js, TypeScript, Firebase Authentication, Firestore, Firebase Storage, and the eBay Browse API. The app allows users to track devices and games, upload item images, compare purchase prices against live market values, save price history, archive sold items, and calculate resale profit or loss.
