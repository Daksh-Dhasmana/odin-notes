# How to install Tailwing
- Setting Up Tailwind CSS in a Vite + React Project
Follow these four steps to install and start using Tailwind CSS in your Vite + React application.

**Step 1: Install Tailwind CSS**
- Open your terminal in VS Code inside your project's root folder and run:
```
npm install -D tailwindcss @tailwindcss/vite
```
**Step 2: Configure vite.config.js**
- Open vite.config.js in the root of your project and update it to include the @tailwindcss/vite plugin:
```
import { defineConfig } from 'vite'
import react from '@vitejs.plugin-react'
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
})
```
***Step 3: Add the Tailwind Directive to index.css***
- Open `src/index.css`, delete any existing default styles, and add this single line at the very top:

```
@import "tailwindcss";
```
**Step 4: Start Your Development Server**
- Restart your server to apply the changes:
```
npm run dev
```