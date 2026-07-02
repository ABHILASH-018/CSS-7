# CSS Assignment 7: Button Hover Effects with CSS Transforms

## What this project is about
For this assignment, I built a simple landing page for a fictional laundry service called **Laundry Wallah**. The main goal was to practice using CSS `transform` properties, specifically combining `scale()` and `rotate()` to make a cool hover effect on a button. 

I've got a header, a hero section with a big button, and a simple footer. The button is where I did all the transform tests.

---

## How to run it
1. Make sure `index.html`, `styles.css`, and the `washingmachine.png` image are all in the same folder.
2. Just double-click `index.html` to open it in Chrome or any browser.
3. Hover your mouse over the blue "Book a service today!" button to see it scale up and tilt.
4. If you click and hold it, it shrinks down slightly to feel like an actual click.

---

## What I learned & what confused me (My Learning Process)

I'm actually really proud of how the button turned out, but I ran into a few annoying issues while building this:

### 1. The "Overwriting Transforms" Trap
At first, I tried to write my CSS like this because it made logical sense to separate them:
```css
.btn-primary:hover {
    transform: scale(1.08);
    transform: rotate(3deg);
}
```
But when I hovered, the button *only* rotated and didn't scale up at all. I spent about 15 minutes trying to figure out why the scale wasn't working. Then I realized (after some googling) that CSS doesn't merge transform declarations—the second `transform` property just completely overwrote the first one. 
To fix it, I had to chain them on the same line:
```css
transform: scale(1.08) rotate(3deg);
```
Once I did that, it worked perfectly!

### 2. Getting the animation to look smooth
Without transition, the button just snapped instantly to the new size and angle. It looked super janky and cheap. 
I added:
```css
transition: transform 0.3s ease;
```
That made the growth and rotation smooth. But then I realized the hover background color change (`#0095ff` to `#0084e0`) and the shadow were still snapping instantly while the shape was animating slowly. It looked really weird.
To fix it, I ended up chaining multiple transitions in one property:
```css
transition: transform 0.3s ease, background-color 0.3s ease, box-shadow 0.3s ease;
```
This made all three changes (size/angle, color, and shadow glow) fade in together, which looks way more polished.

### 3. Designing the click (:active) state
For the click state, I wanted it to feel like you're actually pressing a real button down. I used `scale(0.98)` to shrink it slightly.
Initially, I left the `rotate(3deg)` on the active state too, but when I tested it in the browser, clicking a tilted button felt really unstable and weird. It didn't feel satisfying. I decided to remove the rotation entirely on `:active` so it snaps back to a straight angle when clicked. It feels much more solid this way.

### 4. Layout & Mobile Issues
- **Inline vs block element**: I originally just styled the `<a>` tag directly. But I noticed the padding and scale transforms were behaving weirdly (sometimes overlapping other text). I remembered that `<a>` tags are inline by default, so I had to set `display: inline-block` to make the margins/paddings and transforms behave properly.
- **Mobile Navbar**: When I shrunk the screen, the navbar links were overlapping the logo. Since this is a CSS-only project and I didn't want to write a bunch of complex JavaScript for a hamburger menu, I made a compromise: I hid the middle links on mobile screens (under `576px`) and just kept the logo and username button. It's clean and doesn't break the layout.
- **Full-width Button**: On mobile, the button was hard to tap, so I added a media query to make it `width: 100%` so you can easily tap it with your thumb.

---

## Files in the project
- `index.html` - The structure of the page (with my notes).
- `styles.css` - Where all the styles, flexbox layout, and button transform/transitions live.
- `washingmachine.png` - The graphic illustration in the hero section.