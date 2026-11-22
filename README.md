# Safe Plate Finder — setup guide

A phone app (installable web app) that finds restaurants with gluten-free dishes and helps you check them for **nuts, legumes, peas, chickpeas and soy**. Total cost: **$0**.

## What's in the folder

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `manifest.json`, `sw.js` | Let it install to your home screen and open like an app |
| `*.png` | App icons |

## Step 1: Put it online (free, about 10 minutes)

The app needs an `https://` address so your phone will share its location. GitHub Pages is free and doesn't require any command line.

1. Create a free account at **github.com**.
2. Click **+ → New repository**. Name it `safe-plate`, set it to **Public**, and click **Create repository**.
3. Click **uploading an existing file**. Drag in `index.html`, `manifest.json`, `sw.js`, `README.md` and the **`icons` folder**, then click **Commit changes**.
4. Go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, then **main** and **/ (root)**, and click **Save**.
5. Wait 1–2 minutes. Your app is now at `https://YOUR-USERNAME.github.io/safe-plate/`

Nothing secret is stored in these files. Your Google key (if you add one) lives only on your phone.

## Step 2: Install it on your phone

- **iPhone:** Open the link in **Safari**, tap **Share**, then **Add to Home Screen**.
- **Android:** Open the link in **Chrome**, tap **⋮**, then **Install app** (or **Add to Home screen**).

When it asks for your location, allow it.

The app searches Google Maps, so it needs a free Google key (Step 3) before the first search.

## Step 3: Add your Google Maps key (free, capped at $0)

Google provides the restaurants and reviews, which the app scans for "celiac," "dedicated fryer," "got sick" and similar phrases. Google requires a card on file, but the free monthly allowance is far more than one family uses. The caps below make sure you never go past it.

1. Go to **console.cloud.google.com** and create a project (e.g. "Safe Plate").
2. Set up **Billing** for the project (card required).
3. Go to **APIs & Services → Library** and enable **Places API (New)** and **Maps JavaScript API**.
4. Go to **APIs & Services → Credentials → Create credentials → API key**. Then edit the key:
   - **Application restrictions:** *Websites*. Add `https://YOUR-USERNAME.github.io/*`
   - **API restrictions:** *Restrict key* to **Places API (New)** and **Maps JavaScript API**.
5. **Set a hard cap:** Go to **APIs & Services → Places API (New) → Quotas & System Limits**. Find the Text Search request limit (per day) and set it to **30**. Once the cap is hit, searches stop working until the next day. They don't start charging.
   - Each search asks for reviews, which Google counts at its highest price level. That level includes 1,000 free requests a month, and 30 a day stays under it.
6. Optionally, add a **budget alert** at $1 under **Billing → Budgets & alerts**. Alerts only email you; the quota in step 5 is what actually stops usage.
7. In the app, open **Settings**, paste the key and tap **Save key**. The key is saved per device, so add it on each phone that uses the app.

## How to use it

- **Find:** Tap *Near me* or type a place. Results come from Google Maps, numbered to match the map, and are ranked by gluten-free signals in reviews (dedicated GF, celiac, allergy-friendly), with minus points for reported reactions or cross-contact. Each restaurant has one-tap links to its website, menu search, allergen-guide search, **Find Me Gluten Free**, **Reddit**, directions and phone number.
- **Recipes tab:** Search The Loopy Whisk (and any other recipe sites you add) for things like "bread" or "pizza crust". It searches only the words you type (tap Vegan, Egg-free or Dairy-free to add those). Results open on the original site; save one to your recipe box to check its ingredients.
- **My recipe box:** Save a recipe's link and paste its ingredient list; the app flags anything on your avoid list (red = contains, amber = check the brand). Gluten-free flour blends, chocolate and protein powders get an amber "check" because they can hide soy, pea or bean. Recipes are included in shortlist backups.
- **Copy for Claude** on any restaurant copies a research request for just that place. Paste it into the *Celiac & Allergy Restaurant Finder* project in Claude for a free AI summary of its menu, allergen info, reviews, Reddit and Find Me Gluten Free.
- **Filters:** *Open now only* hides closed places, and *Hide cuisines heavy in soy, beans or chickpeas* hides Japanese, Chinese, Thai, Korean, Indian, Middle Eastern, Mexican and vegan spots. Changing a filter doesn't use another Google search.
- **Cuisine:** Each result shows a 🍽 cuisine badge (Italian, Pizza, Bakery and so on). After a search, a **Cuisine** menu lets you show just one type; the counts show how many of each were found. Places Google lists only as "restaurant" appear under *Other*. Like the other filters, it doesn't use another Google search.
- **Cuisine and chain badges:** Amber badges warn about soy-, bean- or chickpea-heavy cuisines. Chains get an **Official allergen chart** link that searches the chain's own website. Five Guys and Chick-fil-A are flagged for peanut oil.
- **Hours:** Each result shows whether it's open now and today's hours.
- **Save** places to your **Shortlist**. Mark each one *Looks safe*, *Need to ask* or *Avoid*, and keep notes on safe dishes.
- **Check a packaged food:** Tap **Scan a grocery item** at the top of the main screen (no search needed), or use the **Scan & check** tab. Scan a grocery barcode, take a photo of it, or type the number. The app looks it up in Open Food Facts, a free crowd-sourced database, and shows listed allergens, "may contain" warnings, gluten-free labels and the ingredient list with your avoid words highlighted.
- **Check menu:** Take a photo of a menu or allergen chart (read on the phone, free), or paste menu text. Red highlights are listed ingredients to avoid. Amber highlights are things that often hide allergens, like "vegetable oil" (often soy), sauces, marinades and shared fryers.
- **Ask:** Questions to ask staff, plus a chef card you can show your server.
- **Copy for Claude:** On the Shortlist tab, this copies a research request. Paste it into the *Celiac & Allergy Restaurant Finder* project in Claude for a deep multi-source check (menus, allergen charts, Reddit, Find Me Gluten Free) at no extra cost.

## Backup and sharing

In **Settings → Back up or share your shortlist**, tap **Send backup** to text or email your shortlist to another phone. On that phone, paste it into **Restore** and tap **Add to my shortlist**. Restoring adds new places and updates ones with newer notes; it never deletes anything. Your Google key is never included.

## Good to know

- **No app can promise a dish is safe.** Gluten-free tags and reviews almost never mention soy, peas, chickpeas or legumes. Treat results as leads, and confirm with the restaurant every time.
- The menu scanner matches words; it doesn't understand the menu. A clean result doesn't mean a dish is free of allergens. Oils, sauces and seasonings are rarely listed.
- Your shortlist, recipe box, notes and key are saved on this phone only. Clearing the browser's website data erases them.

## Updating the app

Upload the new files to the same GitHub repository (**Add file → Upload files**; same-named files are replaced). The app checks for new versions each time you open it. When one is ready, a **New version ready → Update now** banner appears on the main screen. You can also tap **Settings → Update now** anytime. Updating keeps your key, shortlist and notes. The version number is shown in Settings.

To change the home-screen icon, replace the four `.png` files. iPhones save the icon when the app is added, so remove the app from your home screen and add it again to see a new icon.
