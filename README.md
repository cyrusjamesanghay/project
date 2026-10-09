# Aether Guardians: Shattered World

A browser-based fantasy RPG prototype built with HTML, CSS, and vanilla JavaScript. It includes a pixel-style character renderer, login/register flow, ten guardians, turn-based battles, 10 chapters / 50 stages, gacha summoning, inventory, resources, and an AI-controlled arena.

## Run locally

1. Extract the ZIP.
2. Open the folder in VS Code.
3. Run `index.html` with the Live Server extension (recommended), or use any static web server.
4. Create a demo account. In demo mode, accounts and game saves are stored in this browser's local storage.

## Firebase cloud saves (optional)

1. Create a Firebase project at https://console.firebase.google.com/.
2. Enable **Authentication → Email/Password**.
3. Create a **Cloud Firestore** database.
4. Copy your web app configuration into the `firebaseConfig` object at the top of `game.js`.
5. Add Firestore rules like the following for a student prototype, then publish them:

```text
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /players/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

Do not put service-account secrets in browser code. Firebase web config is public by design; secure data with Authentication and Firestore Rules.

## Deploy to Vercel

1. Upload this folder to a GitHub repository.
2. In Vercel, choose **Add New → Project** and import the repository.
3. Use the **Other** framework preset; no build command is required and the output directory is `.`.
4. Deploy. For cloud saves, configure the Firebase settings in `game.js` before deployment.

## Included gameplay

- 10 elemental guardians: Aeron, Lyra, Kael, Seraphine, Ragnar, Nyx, Draven, Mira, Orion, Vex.
- Turn-based party combat with guardian skills, enemy turns, elemental advantage, rewards, XP, and level-ups.
- Ten chapters, five encounters each, with sequential stage unlocking and chapter bosses.
- Single and five-pull summons, duplicate essence, coins, gems, energy, potions, and materials.
- AI arena battles and win/loss statistics.
- Local demo authentication and browser save fallback; optional Firebase Authentication + Firestore.

## Notes

This is a playable student-project starter, not a commercial-grade MMO. The Arena is AI-controlled and is not real-time online PvP. Character sprites are procedurally drawn pixel-style sprites; replace or enhance them with original sprite sheets for richer frame-by-frame animation. Always test Firebase rules and account flows before sharing publicly.
