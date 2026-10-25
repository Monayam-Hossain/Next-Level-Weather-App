# 🌦️ NextLevel Weather

**A modern, animated, and intelligent weather application built with the latest React ecosystem.**

NextLevel Weather provides real-time weather conditions for any city globally or your exact current location. It goes beyond basic data by offering beautiful, context-aware Lottie animations, dynamic UI theming, and smart, actionable lifestyle recommendations based on the current weather. 

Powered entirely by the free **Open-Meteo APIs**, it requires **zero API keys** to get started.

[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)


---

## ✨ Features

### 1. 🔍 Smart Search & Geolocation
- **Global City Search:** Instantly search for any city worldwide with an intuitive, auto-suggesting search bar.
- **One-Click Geolocation:** Use your browser's native geolocation API to fetch weather for your exact current location instantly.
- **Recent Searches:** *(Optional/Planned)* Keeps track of your recent searches for quick access.

### 2. 🌡️ Comprehensive Weather Overview
Displays critical, real-time meteorological data including:
- Current Temperature & "Feels Like" temperature.
- Atmospheric Humidity percentage.
- Wind Speed and direction.
- High/Low temperatures for the day.

### 3. 🎬 Animated Weather Scenes
- **Lottie Animations:** High-quality, lightweight vector animations that bring the weather to life (e.g., falling rain, drifting clouds, blowing snow).
- **Dynamic Theming:** The entire UI background and color palette shift dynamically to match the weather condition (e.g., warm oranges for sunny days, cool blues for rain).
- **Distinct Night Mode:** A specialized, beautiful dark theme specifically for clear nights, ensuring the app looks great 24/7.

### 4. 💡 Smart Recommendations
Context-aware advice engine that tells you what to do based on the weather:
- 🌧️ **Rain:** "Don't forget your umbrella and waterproof shoes!"
- 🌨️ **Snow:** "Bundle up! Watch out for icy roads."
- 🌫️ **Fog:** "Drive carefully and use your fog lights."
- ☀️ **Hot:** "Stay hydrated and wear sunscreen."
- 🥶 **Cold:** "Layer up with a heavy coat and gloves."
- 😌 **Comfortable:** "Perfect weather for a walk or outdoor activities!"

### 5. 📱 Responsive & Polished UX
- **Mobile-First Design:** Fully optimized Tailwind CSS layout that looks perfect on phones, tablets, and desktops.
- **Loading States:** Beautiful skeleton loaders and spinners to keep the UI engaging while data fetches.
- **Error Handling:** Graceful fallbacks and user-friendly error messages if the network fails or location is denied.
- **SPA Routing:** Seamless navigation without page reloads using React Router.

---

## 🛠️ Tech Stack

This project is built using the absolute latest versions of the modern web ecosystem:

| Category | Technology | Version | Purpose |
| :--- | :--- | :--- | :--- |
| **Core UI** | React | `19.x` | Component-based UI library |
| **Build Tool** | Vite | `8.x` | Lightning-fast dev server and bundler |
| **Styling** | Tailwind CSS | `4.x` | Utility-first CSS framework (via `@tailwindcss/vite`) |
| **Routing** | React Router | `8.x` | Declarative client-side routing |
| **Animations** | lottie-react | `latest` | Rendering complex After Effects animations |
| **Icons** | Lucide React | `latest` | Beautiful, consistent SVG icons |
| **Data** | Open-Meteo API | `N/A` | Free, open-source weather & geocoding data |
| **Code Quality**| ESLint | `10.x` | Static code analysis and linting |

---

## 🏁 Getting Started

Follow these steps to get a local copy up and running.

### Prerequisites
- **Node.js:** v18.0.0 or higher (v20+ recommended)
- **npm** or **yarn** or **pnpm**

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/nextlevel-weather.git
   cd nextlevel-weather