# Introduction
- Although adding color to a page can make it more visually appealing, using the wrong color combination or relying solely on color to convey information can end up making things more difficult to perceive and understand for some users. 
  
## Color Contrast
- A contrast ratio is the difference in brightness between two colors expressed as a ratio. White text on a white background would have lowest ratio (1:1), while black text on a white background would have the highest (21:1).
- Contrast ratios refer to both normal text as well as images of text.
- There are two different conformance level for contrast ratio and they both have different rules for normal and large text.
- Normal text is defined as text with a font size that’s less than 18 points/24px (or less than 14 points/18.66px for bold text)
- Large text is defined as text with a font size that is at least 18 points/24px (or at least 14 points/18.66px for bold text).
- 1) Level AA (minimum) requires a contrast ratio of at least 
      - 4.5:1 for normal text.
      - 3:1 for large text.
- 2) Level AAA (enhanced) requires a contrast ratio of at least 
      - 7:1 for normal text 
      - 4.5:1 for large text.
- There are exceptions to both of these rules that dont need to follow contrast ratio rule:
  - Incidental text, such as text that just happens to be within an image that has other significant visual content, or text that is purely decorative.
  - Text that is part of an inactive or disabled user interface component, such as a button that is disabled and has a lowered opacity.
  - Text that is part of a logo or brand name.
- Now you might be thinking, "its such a pain to calculate contrast ratio",but there is a tool for it, it's called [WebAIM](https://webaim.org/resources/contrastchecker/). Just enter the HEX code of the foreground and background colors and it calculates what conformance levels, if any, the contrast ratio passes.