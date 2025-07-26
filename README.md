# ♿ Web Ally Widget

A lightweight, plug-and-play **accessibility widget** for websites, offering features like dark mode, text spacing, dyslexic-friendly fonts, high contrast, color-blind mode, and more — all built using **Vue.js**.

This project was built as part of an assignment and demonstrates awareness of inclusive design and accessibility principles. It is optimized for real-world integration and expandability.

---

## Features

-  Toggleable Accessibility Menu
-  Dark Mode
-  Increased Text Spacing
-  Readable Font (OpenDyslexic)
-  High Contrast Mode
-  Color Blind Mode
-  Highlighted Links
-  Global Reset Option (resets all accessibility preferences)
-  All options toggle live, without reload

---

## Setup Instructions
1. *Clone the repository*:
 
        git clone https://github.com/iamharshit19/Web-ally-widget.git
       cd Web-ally-widget
2. Install dependencies:

        npm install
3. Run development server:

       npm run dev

Make sure you have Node.js (v16+) and npm installed.

## Implementation Choices Explained
1. Framework: Vue.js (Vite)
Chosen for its component-based structure, reactive data handling, and ease of prototyping.

Vite provides a fast dev environment and build tooling.

2. Component Design
FloatingButton.vue: A circular floating icon for accessing the accessibility menu.

MenuPanel.vue: The actual settings panel containing toggles for various features.

3. Accessibility Features via CSS Classes
Each setting (dark mode, high contrast, etc.) adds a specific class (.dark-mode, .high-contrast, etc.) to the body tag.

This ensures global and consistent styling.

Uses CSS custom properties (for color-blind mode) for easy theme updates.

4. Font Choice: OpenDyslexic
A dyslexia-friendly font to improve readability for users with learning difficulties.

Loaded locally from the assets/ folder.

5. Color-Blind Friendly Mode
Implements color palettes known to be distinguishable by users with common forms of color vision deficiency.

Ensures links and buttons are visually distinct.

6. Global Reset Button
Minimal icon-based reset in the bottom corner.

Clears all accessibility classes and resets the UI state.

7. Live Feedback for Screen Readers (Optional/Expandable)
Infrastructure is ready for adding ARIA live regions to notify screen readers when changes are made.

## Folder Structure
    ├── public/
    ├── src/
    │   ├── assets/
    │   ├── components/
    │   │   ├── FloatingButton.vue
    │   │   └── MenuPanel.vue
    │   └── App.vue
    ├── index.html
    ├── README.md
    └── package.json
## Screenshot
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9f9a66bc-2d49-4b14-9c74-cb15848d72ed" />
