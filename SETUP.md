# Mini-Discord Setup Guide

Your Firebase config and Giphy API key are already configured in `index.html`.

## Admin Features

Server owners and admins can:
- **Manage Members**: Kick, Ban, Make Admin, Remove Admin (owner only)
- **Channels**: Create and delete channels
- **Messages**: Delete any message in the server

## Firebase Setup (if not done)

1. **Firebase Console**: https://console.firebase.google.com/
2. **Auth**: Build → Authentication → Get started → Enable Email/Password
3. **Firestore**: Build → Firestore Database → Create database (choose region)
4. **Storage**: Build → Storage → Get started (same region as Firestore)

## Deploy Rules

### Firestore Rules
1. Firebase Console → Firestore Database → Rules
2. Copy contents of `firestore.rules` and paste
3. Publish

### Storage Rules
1. Firebase Console → Storage → Rules
2. Copy contents of `storage.rules` and paste
3. Publish

## Firestore Indexes

Create these composite indexes in Firestore → Indexes:

| Collection  | Fields                    |
|-------------|---------------------------|
| channels    | serverId (Asc), createdAt (Asc) |
| messages    | channelId (Asc), createdAt (Desc) |
| memberships | userId (Asc), serverId (Asc)     |
| invites     | code (Asc)                      |

## Run Locally

- Open `index.html` in a browser, or
- Use Live Server in VS Code (right-click → Open with Live Server)

## Giphy

GIF search uses the Giphy API. The key is already in the config. If you need a new key: https://developers.giphy.com/dashboard/
