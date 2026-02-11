

# Add Photos to the Mixtape Template

## The Idea: "Album Art Slideshow"

Photos will appear as rotating **album art** in the music player during Stage 2 (the visualizer). As each lyric line plays, a photo fades in behind the visualizer — like a music video or album slideshow synced to the "lyrics." This feels natural for a mixtape/music theme.

Additionally, photos will be used as **vinyl record labels** on the cassette reels in Stage 1, giving the cassette a personal touch.

---

## Changes to `src/templates/Mixtape.tsx`

### 1. Stage 1 — Photo-filled Cassette Reels
- Replace the plain colored circles inside the two spinning tape reels with cropped circular photos from `config.photos`
- Left reel uses `config.photos[0]`, right reel uses `config.photos[1]`
- Photos are clipped to circles and spin with the reels, like vinyl record labels

### 2. Stage 2 — Album Art Slideshow Behind Visualizer
- Add a large, softly blurred photo behind the visualizer area that crossfades in sync with each lyric line
- Each lyric index maps to a photo from `config.photos` (cycling if there are more lyrics than photos)
- The photo has a warm orange-tinted overlay and slight scale animation for a cinematic feel
- Uses `AnimatePresence` for smooth crossfade transitions between photos

### 3. Stage 3 — Photo Mosaic Background
- When the "Hidden Track" is revealed, show a subtle grid/mosaic of all photos as a faded background behind the proposal text
- Photos are small, slightly rotated, and low-opacity to keep the text readable

---

## Technical Details

- All photos sourced from `config.photos` array (already has 8 placeholder URLs)
- Photos cycle using modulo: `config.photos[lyricIndex % config.photos.length]`
- Images use `object-cover` and rounded corners for consistent sizing
- No new dependencies needed — just `motion` components from framer-motion and standard `img` tags

