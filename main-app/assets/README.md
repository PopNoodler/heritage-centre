# Exhibit photos go here

The gallery currently uses generated illustrations so it works offline out of the box.
To show **real photographs**:

1. Copy your image files into this `assets/` folder, e.g. `fishing-fleet.jpg`.
   - Recommended: landscape JPGs around 1200×800 px, each under ~500 KB.
2. Open `main-app/index.html`, find the `EXHIBITS` array (near the bottom, inside the
   `<script>` block) and add a `photo:` line to the matching exhibit:

   ```js
   {
     id:1, motif:"⛵", sky:"#bfe9fb", sea:"#1c7fb0", accent:"#0b3d5c",
     title:"The Fishing Fleet",
     desc:"...",
     photo:"assets/fishing-fleet.jpg"   // <-- add this line
   },
   ```

3. Save and reload the app. The photo replaces the illustration automatically;
   everything else keeps working.

You can also add or remove exhibits by editing the `EXHIBITS` list in that script.
Keep the structure (`id`, `title`, `desc`, and either a `motif` or a `photo`).
