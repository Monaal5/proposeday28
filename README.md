# Monaal ♥ Riddhi — 28 October

A little website for Riddhi. Passcode hint: someone's DOB 🎂

Flow: passcode → our comic story (video) → day & night film → the surprise → six gifts
(letter, the day it became us, museum of us + 21 reasons, reels, games + wish jar, chat & video call).

## Deploy on Vercel
1. Import this repo in Vercel → Framework preset **Other** → no build command, output directory `.` → Deploy.
2. That's it. Everything is static (HTML, images, videos).

## Turn on Chat + Wish Jar (free, ~5 minutes)
1. Go to https://console.firebase.google.com → **Add project**.
2. In the project: **Build → Firestore Database → Create database** (production mode, region asia-south1).
3. **Rules** tab → paste and publish:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{db}/documents {
       match /{col}/{id} {
         allow read, create, update: if col in ['chat', 'wishes', 'settings'];
         allow delete: if false;
       }
     }
   }
   ```
4. **Project settings → Your apps → Web (</>)** → register → copy `apiKey`, `authDomain`, `projectId`, `appId` into `config.js` → commit → Vercel redeploys.

Note: anyone who has the site link can open the chat, so keep the link between the two of you.
The passcode only hides the surprise; it isn't real security.

## Video call
"Just us" → **start our call here** opens a private Jitsi room inside the page. Both open it to see each other.

## Our song
Add the song file to the repo (e.g. `song.mp3`) and set `songUrl: "song.mp3"` in `config.js`.
The ♪ button and the film will play it instead of the built-in piano tune.
