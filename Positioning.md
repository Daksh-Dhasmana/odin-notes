## Absolute Positioning##
- Syntax:-`position:absolute`
- Allows us to position an element at an exact place on screen "without" disturbing other elements.
- It removes that particular element from normal flow of document.
- Controls: Use top, bottom, left, and right to move it.
- The "Ghost" Rule: It removes the element from the normal document flow. Other elements act like it doesn't exist and will slide under it.
- The "Anchor" Rule: It positions itself relative to the nearest position: relative parent. (If no parent is relative, it anchors to the whole screen).
- Use Cases:- Overlays (a dark tint over a background).
            - Modals/Pop-ups (floating over the page).
            - Badges (like a "New" tag on a product image).
            - Tooltips (text that appears above a button).
    
## Fixed Positioning##
- Are also removed from normal flow of docs
- They are fixed relative to viewport(viewing area of browser).
- You tell it where to position itself and it stays there as user scrolls.
- Controls: `top`,`left`,`right`,`bottim`
- The element with fixed positioning will stay there as user scrolls
- Use Cases:- nav bars, float chat buttons.

## Sticky Positioning##
- It Scrolls with rest of content until to the limit you "set"



