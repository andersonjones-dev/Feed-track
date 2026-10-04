# Little Feeds – setup

## 1. Sync backend (free, ~5 minutes)
1. Go to https://console.firebase.google.com → **Add project** (turn Analytics off).
2. **Build → Realtime Database → Create database** (any region, start in locked mode).
3. Open the **Rules** tab, paste this, and **Publish**:
```json
{
  "rules": {
    "fam": {
      "$code": {
        ".read": "$code.length >= 12",
        ".write": "$code.length >= 12",
        "log": { ".indexOn": ["s"] }
      }
    }
  }
}
```
4. Copy the database URL shown at the top of the Data tab (like `https://xxxx-default-rtdb.firebaseio.com`) into `config.js`.

## 2. Publish on GitHub
1. Create a repo, upload all files in this folder (keep them in the repo root).
2. **Settings → Pages → Deploy from a branch → main / root**. Your app will be at `https://<user>.github.io/<repo>/`.

## 3. Connect partners
1. Open the site, ⚙︎ → **Partner sync → Create a family**, then **Share invite link**.
2. Your partner opens the link once (it joins automatically). Both phones: Share → **Add to Home Screen**.
3. Everything works offline; entries sync automatically when either phone is back online.

## Notes
- Anyone with the family code can read/write that family's log, so only share the link with people you trust. Codes are long and random.
- Reminders fire only while the app is open. On iPhone, notifications need iOS 16.4+ and the app added to the Home Screen.
- Voice entry may not work in the Home Screen app on iPhone; Safari works better, and you can always type the sentence instead.
- After editing any file, change `V` in `sw.js` so phones fetch the update.
