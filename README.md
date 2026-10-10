# Wardrobe Maker

A browser-based wardrobe organizer that helps users upload clothing images, manage a personal collection of tops and bottoms, and generate outfit combinations based on color similarity.

Wardrobe Maker uses JavaScript to analyze clothing colors, rank possible combinations, and display the best-matching outfits in a simple, interactive interface. Uploaded items are saved in the browser so they remain available between visits.

## Features

- **Clothing uploads:** Add images of tops and bottoms from your device.
- **Persistent wardrobe:** Saves uploaded images and their color data in browser `localStorage`.
- **Interactive galleries:** Browse your clothing collection in separate galleries for tops and bottoms.
- **Selection controls:** Select individual items, select all, or deselect all items in a category.
- **Item management:** Delete individual clothing items or clear an entire category.
- **Dominant color estimation:** Estimates each clothing item's color by averaging RGB values from the central 60% of its image.
- **Color-based outfit generation:** Compares tops and bottoms using CIE Lab color distance to rank combinations by color similarity.
- **Outfit previews:** Displays up to four of the highest-ranked combinations.
- **Responsive interface:** Adapts the layout for smaller screens.
- **Visual feedback:** Uses color indicators, hover effects, image previews, and gallery overlays to make wardrobe management more intuitive.

## Technologies Used

- **HTML5** — Page structure and clothing upload controls
- **CSS3** — Responsive layouts, gallery styling, overlays, and visual effects
- **JavaScript** — Image processing, wardrobe management, and outfit generation
- **Browser File API** — Reads uploaded clothing images
- **Canvas API** — Processes image pixels to estimate clothing colors
- **localStorage** — Persists clothing collections in the browser
- **Chroma.js** — Calculates perceptual color distance in Lab color space

## Getting Started

### Requirements

- A modern web browser with JavaScript enabled
- An internet connection to load the external Chroma.js library from its CDN

No backend server, database, or package installation is required for the basic application.

### Installation

1. Download or clone this repository.
2. Make sure the project files are organized as follows:

   ```text
   Wardrobe-Maker/
   ├── index.html
   ├── style.css
   └── app.js
   ```

3. Open `index.html` in your browser.

For local development, you can also use the Live Server extension in Visual Studio Code.

## How to Use

1. **Upload clothing:** Choose an image for your tops or bottoms.
2. **Open a gallery:** View the uploaded items in the corresponding gallery.
3. **Select clothing:** Click the selection indicator on each item to include or exclude it from outfit generation.
4. **Manage your wardrobe:** Delete individual items, clear a category, or use the bulk selection controls.
5. **Generate outfits:** Click **Generate Outfits** to compare the selected tops and bottoms.
6. **Review the results:** View up to four combinations ranked by color similarity.

At least one top and one bottom must be selected before generating outfits.

## How Outfit Matching Works

Wardrobe Maker creates possible combinations from every selected top and bottom.

For each combination, the application:

1. Estimates the color of each clothing item by averaging the RGB values of pixels in the central portion of its image.
2. Calculates the color distance between the top and bottom using Chroma.js in CIE Lab color space.
3. Sorts combinations from the smallest color distance to the largest.
4. Displays up to four combinations with the smallest distances.

A smaller color distance indicates that the estimated colors are more similar.

**Note:** Color similarity is a simple matching criterion. It does not account for fashion rules, patterns, clothing styles, fabric textures, or personal preferences.

## Data Storage and Privacy

Wardrobe Maker stores clothing images and color information in the browser's `localStorage`.

- Uploaded images are stored as data URLs.
- Tops and bottoms are stored separately under the keys `uploadedTops` and `uploadedBottoms`.
- The wardrobe is associated with the browser and website origin used to access the application.
- Clearing the browser's site data may remove saved wardrobe items.
- The application does not require a backend database or user account.

Because images are stored directly in browser storage, large collections may eventually reach the browser's storage limits.

## External Libraries

The application loads Chroma.js from a CDN:

- [Chroma.js](https://gka.github.io/chroma.js/)

The HTML also includes Color Thief, although the current JavaScript implementation calculates average RGB color directly using the Canvas API instead of calling Color Thief.

## Current Limitations

- Only tops and bottoms are supported.
- Color matching is based on average RGB values from the central image region, which may be affected by backgrounds, lighting, and image composition.
- Generated outfits are ranked by color similarity, not overall style compatibility.
- Only the first four ranked combinations are displayed.
- Clothing data is saved locally in the browser rather than synchronized between devices.
- Browser storage limits may restrict the number or size of images that can be saved.
- The current implementation does not include user accounts, cloud storage, or an AI-based fashion recommendation system.

## Future Improvements

Potential enhancements include:

- Add categories for shoes, jackets, accessories, and other clothing.
- Allow users to filter outfits by color, occasion, or style.
- Improve clothing color extraction by detecting the garment separately from the background.
- Add outfit descriptions and more detailed color information.
- Provide options to export, import, or back up a wardrobe.
- Improve accessibility and keyboard navigation.

## Project Purpose

Wardrobe Maker demonstrates front-end web development through file uploads, image processing, browser storage, interactive galleries, responsive design, and a basic color-based recommendation algorithm.

## License

No license has been specified. Unless a license is added to the repository, the project should be treated as all rights reserved by its author.
