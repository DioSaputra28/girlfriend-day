# 💝 Girlfriend Day Celebration Website

A romantic and interactive website created to celebrate Girlfriend Day, featuring beautiful animations, music, and heartfelt messages.

## 🌟 Features

- **Interactive Hero Section** with animated text and romantic quotes
- **Music Player** with custom controls
- **Photo Gallery** showcasing special memories
- **Blooming Flower Animation** that responds to scroll
- **Responsive Design** works beautifully on all devices
- **Modern Tech Stack** using Vue 3, TypeScript, and Tailwind CSS v4

## 🚀 Technologies Used

- **Vue 3** - Progressive JavaScript Framework
- **TypeScript** - Type-safe development
- **Tailwind CSS v4** - Utility-first CSS framework
- **Vite** - Next generation frontend tooling
- **@tailwindcss/vite** - Official Tailwind CSS plugin for Vite

## 🛠️ Installation

1. Clone the repository:
```bash
git clone https://github.com/DioSaputra28/girlfriend-day.git
cd girlfriend-day
```

2. Install dependencies:
```bash
npm install
```

3. Run the development server:
```bash
npm run dev
```

4. Build for production:
```bash
npm run build
```

## 📁 Project Structure

```
girlfriend-day/
├── src/
│   ├── components/
│   │   ├── HeroSection.vue
│   │   ├── GirlfriendDaySection.vue
│   │   ├── MusicSection.vue
│   │   ├── PhotoGallery.vue
│   │   └── BloomingFlower.vue
│   ├── assets/
│   │   └── lagu.mp3
│   ├── App.vue
│   ├── main.ts
│   └── style.css
├── public/
├── index.html
├── vite.config.ts
├── tailwind.config.js
└── package.json
```

## 🎨 Customization

### Changing Colors
The color scheme can be customized in `src/style.css` under the `@theme` section:

```css
@theme {
  --color-pink-500: #ec4899;
  --color-rose-500: #f43f5e;
  /* Add your custom colors here */
}
```

### Adding Photos
To add or change photos in the gallery, edit the `photos` array in `src/components/PhotoGallery.vue`.

### Changing Music
Replace the audio file in `src/assets/lagu.mp3` with your preferred song.

## 💕 Special Thanks

Created with love for Shofia Jasmine on Girlfriend Day 2024.

## 📝 License

This project is open source and available under the [MIT License](LICENSE).
