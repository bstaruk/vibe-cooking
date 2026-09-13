# Photos

Photos are welcome here. They're what make the notebook worth browsing. The repo is public, though, so every photo goes through the same process before it's committed. That process is two Homebrew tools and plain commands, with no scripts.

## Tools

- **ImageMagick** (`magick`) rotates the image upright, resizes it, converts its colors, and strips metadata.
- **ExifTool** (`exiftool`) confirms that no identifying metadata survived.
- If either tool is missing, install both with `brew install imagemagick exiftool`.

## Getting photos in

- **Originals:** Brian drops the original files into `inbox/`, which is gitignored, or gives a path (for example, a photo AirDropped into `~/Downloads`). HEIC, JPEG, and PNG all work.
- **Photos pasted into chat:** you can look at these, but you can't save them. If one is worth keeping, say so once. The original file needs to go into `inbox/`.
- **Rights:** only commit photos Brian took. The content is licensed CC BY 4.0, so we can't include other people's images or photos of cookbook pages.
- **Leave the originals alone.** Never delete or move anything in `inbox/`. Brian clears it out.

## Look before processing

Open each photo and check the whole frame for anything that shouldn't be public:

- faces of people who haven't agreed to be shown
- mail or packages showing an address
- screens and documents
- a window view that would pinpoint the house

If you find a problem, skip that photo and say why.

## Process

Save each processed photo in a `photos/` folder next to the file that uses it:

- Cook photos: `journal/YYYY/photos/YYYY-MM-DD-<slug>-N.jpg`
- Gear photos (like a skillet's markings): `kitchen/photos/<call-name-slug>-N.jpg`

**Convert** each photo with one command:

~~~bash
magick "inbox/IMG_1234.HEIC" -auto-orient -resize "1600x1600>" -profile "/System/Library/ColorSync/Profiles/sRGB Profile.icc" -strip -quality 82 "journal/2026/photos/2026-09-20-cast-iron-cornbread-1.jpg"
~~~

This command:

- rotates the image to its correct orientation
- limits the longest side to 1600px
- converts the colors to sRGB so they display correctly
- removes all metadata (GPS, camera, timestamps)
- saves a small JPEG

**Verify** the result. This command must print nothing:

~~~bash
exiftool -q -q -GPS:all -EXIF:all -XMP:all -IPTC:all "journal/2026/photos/2026-09-20-cast-iron-cornbread-1.jpg"
~~~

If it prints anything, don't commit the file. Run `exiftool -all= -overwrite_original "<file>"`, then verify again.

## Using photos

- **Alt text:** embed each photo with a real description, since this is a public page: `![Cornbread wedge with a crackly golden crust](photos/2026-09-20-cast-iron-cornbread-1.jpg)`
- **How many:** 1–4 per cook. Pick the ones that show something: the finished dish, the crumb, the doneness, the mistake.
- **Hero images:** a recipe links to its best journal photo as its hero image. Don't copy the file.
