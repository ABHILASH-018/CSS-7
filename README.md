# CSS-7 — Button Hover Effects with CSS Transforms

## About This Project

This is a simple landing page for **Laundry Wallah**, a fictional laundry service. The main goal of this assignment was to learn how CSS `transform` functions — specifically `scale()` and `rotate()` — can be combined to create engaging button hover effects.

The page has a header with navigation, a hero section with a call-to-action button, and a footer. The button is where all the transform magic happens.

---

## How to Set Up and View

1. **Download or clone** this repository to your computer.
2. Make sure all three files are in the same folder:
   - `index.html`
   - `styles.css`
   - `washingmachine.png`
3. **Open `index.html`** in any web browser (Chrome, Firefox, Edge, etc.) by double-clicking it.
4. **Hover over the blue "Book a service today!" button** to see the transform effects in action.
5. **Click and hold** the button to see the `:active` press-down effect.

No build tools, servers, or installations needed — it's just plain HTML and CSS.

---

## What I Learned About CSS Transforms

### `scale()` — Making Things Bigger or Smaller

- `scale(1)` keeps the element at its normal size.
- `scale(1.08)` makes it 8% larger — I used this on hover to make the button feel like it's popping towards you.
- `scale(0.98)` makes it slightly smaller — I used this on `:active` (when you click and hold) to simulate a button being physically pressed down.

### `rotate()` — Tilting an Element

- `rotate(3deg)` tilts the element 3 degrees clockwise.
- Positive values go clockwise, negative values go counter-clockwise.
- I kept the rotation small (3 degrees) because anything bigger looks sloppy on a button. It just adds a subtle playful touch.

### Combining Them Together

The key thing I learned is that **you can only have one `transform` property per selector**. If you try to write two separate `transform` lines, the second one will overwrite the first. So to use both, you chain them:

```css
transform: scale(1.08) rotate(3deg);
```

This applies both effects at the same time — the button grows *and* tilts when you hover over it.

### Making It Smooth with `transition`

Without `transition`, the hover effect snaps instantly — it doesn't look good. Adding this line:

```css
transition: transform 0.3s ease;
```

...tells the browser to animate the change over 0.3 seconds using an "ease" timing curve (starts slow, speeds up, then slows down at the end). I also transition `background-color` and `box-shadow` so everything changes together.

---

## File Structure

```
CSS-7/
├── index.html          — The page structure (HTML)
├── styles.css          — All styling and hover animations (CSS)
├── washingmachine.png  — Hero section image
└── README.md           — This file
```

---

## Technologies Used

- HTML5
- CSS3 (Transforms, Transitions, Flexbox, Grid)
- Google Fonts (Poppins)