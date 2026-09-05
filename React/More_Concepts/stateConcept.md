# Managing States with Context API
- The React Context API is a built-in feature that lets you share state globally across your component tree without manually passing props through every level—a problem known as "prop drilling."
- Let's imagine this through a simple C program

# Prop Drilling
- This is an example of prop drilling

```
#include <stdio.h>

void userAvatar(int userId) {
    printf("User ID: %d\n", userId); // Finally used here!
}

void navbar(int userId) {
    userAvatar(userId); // Unused parameter, just passing it along
}

void header(int userId) {
    navbar(userId);     // Unused parameter, just passing it along
}

int main() {
    int userId = 42;
    header(userId);
    return 0;
}
```

- As you can see, to use `userId` in `userAvator`, we have to pass it down several other functions, It has several disadvantages
- Like, if we changes a single function that is in middle, it could break the entire application
- This is why we use context API

# 
