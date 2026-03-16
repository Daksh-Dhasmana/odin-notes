## Several functions in css ##

# 1. Calc()#
- helps us to calculate space for a particular element relative to other element occupied space.
- It's purpose is to figure out how much space is left after other elements have "claimed" their spot.
- Syntax: `property:calc(expression)`.

# 2. min()#
- It takes a list of values seperated by commas and returns the smallest one.
- eg:`width:min(150px, 100%)`- it checks if 100% of parent's width is smaller than 150px, if yes then it will       resize to that 100%, if no then it will remain 150px.
- You can also do Basic math inside this without use of calc().

# 3. Max()#
- Vice versa of min().
- It is most useful when viewing window is exceptionally small or user uses browser's zoom features.

# 4. Clamp()#
- It is a great way to make elements fluid and responsive
- Syntax: `clamp(MIN,IDEAL,MAX)`
- It takes 3 values: Min(the minimum floor),Ideal(default value), Max(the maximum celing).
- Uses Ideal value at first and if it scales, then it uses Max and Min to set the ceiling.