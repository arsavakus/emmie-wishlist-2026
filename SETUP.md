# Emmie's wishlist: 10-minute setup

You need two free things: a place to store the hearts (Firebase) and a place to host the page (Netlify Drop, or GitHub Pages).
Both can use a Google / GitHub login. No credit card is needed for either.

## 1. Create the shared "bought" list (Firebase)
1. Go to https://console.firebase.google.com, click **Create a project**, name it (e.g. `emmie-wishlist`), turn Google Analytics off.
2. In the left menu: **Build > Firestore Database > Create database**. Pick any region, choose **Start in production mode**.
3. Open the **Rules** tab, delete what is there, paste in everything from `firestore.rules`, click **Publish**.

## 2. Connect the page to it
1. Project **settings (gear icon) > General > Your apps > the `</>` Web icon**. Nickname it, skip hosting, click **Register app**.
2. You'll see a `firebaseConfig = { ... }` block. Copy the four values `apiKey`, `authDomain`, `projectId`, `appId` into `firebase-config.js` (replace the PASTE_... text). Save.
   (These keys are meant to be public; the rules in step 1 are what protect the data.)

## 3. Put it online (pick one)
**Netlify Drop (easiest):** open https://app.netlify.com/drop and drag this whole folder in. You get a link right away; you can rename it under Site settings.
**GitHub Pages:** create a repo, upload `index.html` and `firebase-config.js`, then Settings > Pages > Deploy from branch `main` / root. The link is `https://<you>.github.io/<repo>/`.

## 4. Test
Open the link on two devices. Tap a heart on one; it should fill on the other within a second or two. The small line at the bottom of the page says "Live" when it's connected.

## Good to know
- Anyone with the link can tick or untick hearts. That is how it works without logins.
- To start over, delete the `wishlist/state` document in the Firestore console.
- Items in `index.html` can be edited; each heart is tied to its position in its card, so don't reorder items after people start ticking.
