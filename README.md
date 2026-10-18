# A little something for you

A single-page birthday site: a cinematic opening, a letter that unfolds out of an envelope, and a gallery you can fill with real photographs.

Everything she reads lives in one file. There is no backend, account, or database.

## Run it

```bash
npm install
npm run dev
```

Open the local address Vite prints (usually `http://localhost:5173`).

To create the folder you can deploy:

```bash
npm run build
npm run preview
```

The built site is in `dist/`. Netlify, Vercel, or Cloudflare Pages can host that folder and give you a public link.

## Make it hers

Edit `src/data/birthdayConfig.ts`.

- Set `herName`. Every `[HER NAME]` in the letter, headlines, and envelopes updates from that one value.
- Rewrite the letter, the six quality cards, the wishes, and the final note so they sound like you. The included lines are a sincere starting point, not a record of anything that happened.
- Do not leave a line in if it is not true.

### Photographs

Put image files in `public/images/memories/`, then describe them in the `memories` array:

```ts
export const memories = [
  {
    image: "/images/memories/photo.jpg",
    caption: "A little moment worth remembering",
    date: "",
    description: "",
    layout: "portrait",
  },
]
```

- `image` is the public path.
- `caption` sits under the frame and in the lightbox.
- `date` is optional. Leave it `""` to hide it.
- `description` is an optional note shown only when the photo is opened.
- `layout` is `"portrait"`, `"landscape"`, or `"tall"`.

The three images already in the gallery are rose illustrations so the layout is visible. They are not photographs of anyone. Delete those entries when you add real photos.

If `memories` is an empty array, the page shows ornamental frames instead.

### Background

The site ships with a painted burgundy rose garden at `public/images/burgundy-roses.svg`.

To use your own floral image, save it as `public/images/burgundy-roses.jpg` and set:

```ts
backgroundImage: "/images/burgundy-roses.jpg",
```

### Music

Music never plays by itself. To add a song, put an mp3 in `public/audio/` and set:

```ts
musicFile: "/audio/your-song.mp3",
```

Leave `musicFile` as `""` and the music button stays hidden. If the file is missing, the button hides after it fails to load.

## What’s on the page

1. Opening line, then an envelope that opens into the rest of the site.
2. Birthday introduction.
3. The handwritten letter. “Read again” replays the unfolding.
4. Memory gallery. Click a photograph for the lightbox. Arrow keys move between photos. Escape closes it.
5. “Little things that make you, you.” Each card opens on click or keyboard focus.
6. Wishes, revealed as you scroll.
7. A last envelope.

A thin gold line at the top shows scroll progress. On a wider screen, small dots on the right jump between sections.

The layout is built for phones first, then tablets and desktops. If the visitor has reduced motion turned on, the envelopes open without the long animation and the drifting petals stay still.
