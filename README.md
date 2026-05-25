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

