# NerdyReader

**An offline book reader for Android.** PDF, EPUB, Word, text, Markdown and HTML, in a calm interface with real page turns, reading stats, marking tools and a built-in dictionary.

No account. No ads. No tracking. **The app has no internet permission at all**, so nothing you read ever leaves your phone.

`Version 1.5.0` · `Android 8.0+` · `Personal project by NerdyIntruder`

---

## Highlights

### Finds your documents for you
Allow file access once and NerdyReader **scans the phone and lists every PDF, EPUB, Word, text, Markdown and web file it finds**, neatly organised in one place. Filter by type, search by name, folder or author, sort (newest, oldest, A–Z, Z–A, largest, smallest, last opened), browse by folder or group the list by folder, and switch between a soft rounded grid and a list. PDFs get real page thumbnails. Open any file with one tap; it is copied into the library the first time so progress, stats and marks work.

### Reads like a real book
- **Book view** with two pages side by side (one page on a narrow screen) and a **realistic page curl**: the page lifts from the corner you touch, folds over, and shows its back and a soft shadow. Drag it, tap the edges, or swipe. Flip, Fade and None styles are also available, with speed and sound options.
- **Zoom** with one page or two: pinch, double-tap, or use the slider. PDF pages are redrawn sharp at any zoom.
- **Full screen on demand**: the app opens like any normal app, with the phone's top and bottom bars visible. A small floating button (or the Aa and Themes settings) switches full screen on and off.
- **All pages** shows page pictures so you can jump to any page.
- Scroll view, reflowable text for PDFs, adjustable font, spacing, margins, page colour, dimming and warm light.

### Mark up your books
- **PDFs:** highlighter, pen, line, rectangle, paragraph notes, eraser, colours, sizes, undo, redo and clear. Marks stay on the page when you zoom.
- **EPUB, Word, text:** select text and highlight it in four colours. Tap a highlight to remove it or save it as a quote.

### Built-in offline dictionary
Long-press (or tap) any word to see its meaning, examples and similar words. The dictionary is **WordNet 3.1** (about 70,000 English words) stored inside the app, and it understands word forms such as *running → run* and *went → go*. Save words to a personal vocabulary list.

### Reading habit tracking
- Time and pages are logged **only while a book is open and you are reading**.
- Month calendar, streak and best streak, daily goal ring, weekly chart, six-month heatmap, "when you read" chart, totals, most-read books and badges.
- Everything stays on the device. You can export or reset the log.

### Quotes from your own books
Every book you add is scanned in the background and its best lines are kept. Home shows them one after another, from a different book each time, with the title, chapter and page. Save favourites, copy them, or jump to the page. You can also save your own quotes while reading.

### And more
- **Convert** books to PDF, Word, EPUB, text, Markdown or a web page, or **save them as audio**.
- **Read aloud** with the phone's own voice, with speed, voice and sleep timer.
- **Themes:** twelve app themes (light and dark), several page colours, and an interface-size setting that adapts to your phone.
- **Calm music** generated live on the phone, and a cinematic **welcome film** with a short launch melody (both optional).
- Library with grid or list view, search, ratings, "mark finished", and a "Surprise me" button.

## Supported files

| Format | Notes |
| --- | --- |
| PDF | Original pages, or reflowable text. Scanned PDFs have no text, so use page view. |
| EPUB | Chapters, contents, images |
| Word (.docx) | Text and basic formatting |
| TXT, Markdown, HTML | Cut into real pages in Book view |

Not supported yet: MOBI/AZW and DRM-protected books.

## Privacy

- The app declares **no internet permission**. It cannot send anything anywhere.
- **File access** is the one sensitive permission it asks for ("all files access" on Android 11 and newer), only to list documents. It reads names, sizes and dates; a file's content is read only when you open it, or to draw a PDF's thumbnail. You can refuse it and add files by hand instead.
- Opened books are copied into the app's own storage, so they open even if you delete the original.
- Reading stats, marks, quotes, saved words and settings are stored only on the device.
- The dictionary and the PDF and EPUB engines are bundled with the app; nothing is loaded from the web.

## Get the APK (phone only, no computer needed)

1. Create a GitHub repository.
2. **Add file → Create new file**, name it `.github/workflows/build-apk.yml`, paste in the workflow from this project, and commit.
3. **Add file → Upload files** and upload `NerdyReader-source.zip` (as it is, no unzipping), then commit.
4. Open the **Actions** tab. The *Build NerdyReader APK* run takes about 3–5 minutes.
5. Download `NerdyReader.apk` from **Releases → NerdyReader (latest build)**, open it on your phone, and allow "install unknown apps" for your browser.
6. Open NerdyReader and tap **Allow access**. Android opens a settings page: turn on *Allow access to all files*, then come back and your documents appear.

If you have a computer, you can push the unzipped project instead; the workflow handles both.

Every build is signed with the same key (in `keystore/`), so a new APK installs over the old one and **keeps your library**.

### Build it yourself

```bash
# Requirements: JDK 17, Android SDK (API 34), Gradle 8.9
gradle assembleDebug
# APK: app/build/outputs/apk/debug/app-debug.apk
```

## Make it yours

| What | Where |
| --- | --- |
| About page text and book shelf | `app/src/main/assets/www/js/about.js` |
| Your photo | `raghu.jpg` next to the zip (or in `assets/www/`) |
| Themes and colours | `css/extra.css`, `css/extra3.css`, `js/theme.js` |
| Music moods | `js/music.js` |
| Version | `app/build.gradle` (`versionCode`, `versionName`) |

## Project layout

```
app/src/main/java/.../MainActivity.java   WebView shell: file picker, Open with, full screen, speech, save
app/src/main/assets/www/                  the whole app (HTML, CSS, JavaScript)
  js/parsers.js    EPUB, TXT, MD, HTML, DOCX, PDF text
  js/reader.js     reflow reader and PDF page viewer
  js/book.js       Book view: two-page spreads, page turns, zoom, all-pages grid
  js/curl.js       page-curl geometry
  js/ann.js        drawing tools and text highlights
  js/dict.js       offline dictionary lookup and saved words
  js/track.js      reading log, streaks, calendar and Stats screen
  js/quotes.js     quote finder, Home quote card, Quotes screen
  js/splash.js     welcome film and launch melody
  js/device.js     finds documents on the phone; Library screen, filters, sorting, folders
  js/views.js      home, search, shelf, book page
  js/theme.js      themes and reading styles
  js/music.js      generated calm music
  js/convert.js    export to PDF / Word / EPUB / text / Markdown / HTML
  js/listen.js     read aloud and save as audio
  data/            WordNet dictionary files and its licence
  lib/             pdf.js and JSZip (bundled, no CDN)
keystore/          fixed signing key (personal use)
```

## Built with

Android WebView shell (Java) · plain HTML, CSS and JavaScript · no frameworks, no build step for the web part.

## Credits and licences

- **WordNet 3.1**, © 2011 Princeton University, provides the dictionary data. Its licence is included in `app/src/main/assets/www/data/WORDNET-LICENSE.txt` and in the app under *About → Dictionary*.
- **[pdf.js](https://mozilla.github.io/pdf.js/)** (Mozilla) renders PDFs.
- **[JSZip](https://stuk.github.io/jszip/)** reads EPUB and Word files.
- The reading app itself, its design and its code are a personal project by **NerdyIntruder**, who also builds **NerdyTrades**, a quant-driven trading dashboard. Add a licence file to this repository if you want others to reuse it.

## About

Built by **Raghu (NerdyIntruder)** · Instagram [@nerdyintruder](https://www.instagram.com/nerdyintruder/)
