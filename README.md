# Nirog Health

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?style=flat-square&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Netlify](https://img.shields.io/badge/Deployed_on-Netlify-00C7B7?style=flat-square&logo=netlify&logoColor=white)

---

## 🚀 Overview

**Nirog Health** is an AI-powered healthcare assistant designed to bridge the gap between symptom onset and informed medical guidance. Users report their symptoms through an accessible interface, and a trained machine learning classification model returns the most probable disease along with relevant health guidance — no medical background required.

The name *Nirog* (नीरोग) is a Sanskrit/Hindi word meaning "free from disease" or "good health" — a name that reflects the core mission of the project.

The problem it solves is tangible: millions of people lack immediate access to a doctor, yet early awareness of a potential condition can dramatically improve outcomes. Nirog makes preliminary health intelligence accessible to anyone with a browser or a phone.

---

## ✨ Features

- **Symptom-based Disease Prediction** — Accepts structured symptom input and maps it to one of 40+ disease categories using a trained ML classifier.
- **AI Health Guidance** — Alongside each prediction, users receive actionable health information for the detected condition.
- **Robust Symptom Encoding** — Handles sparse or incomplete symptom sets by converting free-form selections into model-ready feature vectors, maintaining reliable predictions even with partial input.
- **3D Interactive UI** — Immersive three-dimensional interface elements powered by Three.js and React Three Fiber.
- **Responsive & Accessible Design** — Built with Radix UI primitives and Tailwind CSS, ensuring accessibility and consistent cross-device experience.
- **Mobile App Support** — Capacitor integration enables native Android app packaging from a single codebase.
- **Dark / Light Theme** — User-selectable theming via `next-themes`.
- **Data Visualizations** — Health data and prediction confidence displayed through Recharts dashboards.
- **Animated Transitions** — Smooth, polished micro-interactions via Framer Motion.
- **Docker Support** — Containerised deployment ready out of the box.
- **Netlify Deployment** — Configured for instant static + serverless deployment.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, TypeScript 5, Vite 7 |
| **Styling** | Tailwind CSS 3, tailwindcss-animate, @tailwindcss/typography |
| **UI Components** | Radix UI (full suite), shadcn/ui patterns, Lucide React icons |
| **3D Graphics** | Three.js, @react-three/fiber, @react-three/drei |
| **Animation** | Framer Motion |
| **Routing** | React Router DOM v6 |
| **Data Fetching** | TanStack Query (React Query v5) |
| **Forms** | React Hook Form, Zod, @hookform/resolvers |
| **Charts** | Recharts |
| **Backend** | Express 5, Node.js, serverless-http |
| **Mobile** | Capacitor v8 (Android) |
| **ML Pipeline** | Python, Scikit-learn, Pandas, NumPy |
| **ML Interface** | Streamlit / Flask |
| **Testing** | Vitest |
| **Package Manager** | pnpm |
| **Deployment** | Netlify, Docker |

---

## 📦 Installation

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- [pnpm](https://pnpm.io/) v10 or higher (`npm install -g pnpm`)
- [Python](https://python.org/) 3.9+ (for the ML backend)

### 1. Clone the Repository

```bash
git clone https://github.com/pandeylakshya207-max/Nirog-Health.git
cd Nirog-Health
```

### 2. Install Frontend Dependencies

```bash
pnpm install
```

### 3. Set Up the ML Backend

The ML prediction service is a Python module. Set it up in a separate terminal:

```bash
cd ml-backend        # or the relevant Python directory
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Copy the example environment file and fill in your values:

```bash
cp .env.example .env
```

See the [⚙️ Configuration](#️-configuration) section for all available variables.

### 5. Start the Development Server

```bash
# Frontend + Express server
pnpm dev

# ML backend (Streamlit)
streamlit run app.py

# or Flask
python app.py
```

The application will be available at `http://localhost:5173` by default.

---

## ▶️ Usage

### Running the Web Application

```bash
pnpm dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Building for Production

```bash
# Build both client and server bundles
pnpm build

# Start the production server
pnpm start
```

### Running with Docker

```bash
docker build -t nirog-health .
docker run -p 3000:3000 nirog-health
```

### Building the Android App

Ensure you have [Android Studio](https://developer.android.com/studio) installed, then:

```bash
pnpm build
npx cap sync android
npx cap open android
```

### Using the Disease Predictor

1. Open the application in your browser.
2. Navigate to the **Symptom Checker** section.
3. Select all symptoms you are experiencing from the provided list.
4. Submit the form to receive an AI-generated disease prediction.
5. Review the accompanying health guidance and recommended next steps.

> **Disclaimer:** Nirog Health is intended for informational purposes only and does not constitute professional medical advice. Always consult a qualified healthcare provider for diagnosis and treatment.

---

## 📁 Project Structure

```
Nirog-Health/
├── src/                        # Application source code
│   ├── components/             # Reusable UI components (Radix UI-based)
│   ├── pages/                  # Route-level page components
│   ├── hooks/                  # Custom React hooks
│   ├── lib/                    # Utility functions and helpers
│   └── server/                 # Express server entry point
├── ml-backend/                 # Python ML pipeline (Scikit-learn)
│   ├── app.py                  # Streamlit / Flask API entry point
│   ├── model/                  # Trained classifier and encoders
│   └── data/                   # Training datasets
├── public/                     # Static assets
├── capacitor.config.ts         # Capacitor (mobile) configuration
├── components.json             # shadcn/ui component registry config
├── netlify.toml                # Netlify deployment configuration
├── tailwind.config.ts          # Tailwind CSS configuration
├── vite.config.ts              # Vite client build configuration
├── vite.config.server.ts       # Vite server build configuration
├── tsconfig.json               # TypeScript compiler options
├── .prettierrc                 # Code formatting rules
├── .dockerignore               # Docker build exclusions
└── package.json                # Project metadata and scripts
```

---

## ⚙️ Configuration

Create a `.env` file in the project root. The following environment variables are supported:

| Variable | Description | Required |
|---|---|---|
| `VITE_API_URL` | Base URL for the ML prediction API | Yes |
| `PORT` | Port for the Express server (default: `3000`) | No |
| `ML_MODEL_PATH` | Path to the serialised Scikit-learn model file | Yes (ML backend) |
| `NODE_ENV` | Runtime environment (`development` / `production`) | No |

Example `.env`:

```env
VITE_API_URL=http://localhost:8501
PORT=3000
NODE_ENV=development
```

---

## 🧪 Testing

Nirog Health uses [Vitest](https://vitest.dev/) for unit and integration testing.

```bash
# Run all tests once
pnpm test

# Run tests in watch mode
pnpm vitest

# Type-check without emitting
pnpm typecheck
```

To format code before committing:

```bash
pnpm format.fix
```

---

## 🤝 Contributing

Contributions are welcome and appreciated. Please follow these steps:

1. **Fork** the repository and create your branch from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** and ensure the code is well-tested.

3. **Lint and format** your code:
   ```bash
   pnpm format.fix
   pnpm typecheck
   ```

4. **Run the test suite** and make sure all tests pass:
   ```bash
   pnpm test
   ```

5. **Commit** using a clear, descriptive message:
   ```bash
   git commit -m "feat: add severity scoring to prediction output"
   ```

6. **Push** to your fork and open a **Pull Request** against the `main` branch.

Please open an issue first for significant changes so the scope can be discussed before implementation.

---

## 🐛 Troubleshooting

**`pnpm install` fails with a Node version error**
Ensure you are running Node.js v18 or higher. Use [nvm](https://github.com/nvm-sh/nvm) to manage versions:
```bash
nvm install 18 && nvm use 18
```

**ML backend returns a connection error**
Verify that the Python service is running and that `VITE_API_URL` in your `.env` matches the address and port it is listening on.

**Capacitor Android build fails**
Run `npx cap sync android` after every production build to keep native assets in sync. Ensure Android Studio and the Android SDK are properly installed.

**Blank screen on first load**
Clear your browser cache or try an incognito window. If the issue persists, check the browser console for any build-related errors and confirm the `pnpm build` step completed without warnings.

**Port already in use**
Change the `PORT` variable in `.env`, or kill the process occupying the default port:
```bash
lsof -ti:3000 | xargs kill
```

---

## 📄 License

This project is licensed under the [MIT License](./LICENSE). You are free to use, modify, and distribute this software with attribution.

---

## 🙌 Acknowledgements

- [Radix UI](https://www.radix-ui.com/) — Unstyled, accessible component primitives.
- [shadcn/ui](https://ui.shadcn.com/) — Component patterns and design system conventions.
- [Scikit-learn](https://scikit-learn.org/) — The ML classification backbone of the prediction engine.
- [Three.js](https://threejs.org/) & [React Three Fiber](https://docs.pmnd.rs/react-three-fiber) — 3D rendering in the browser.
- [Framer Motion](https://www.framer.com/motion/) — Production-grade animation library.
- [TanStack Query](https://tanstack.com/query) — Asynchronous state management.
- [Vite](https://vite.dev/) — Lightning-fast frontend tooling.
- [Capacitor](https://capacitorjs.com/) — Cross-platform native runtime.

---

## 📬 Contact

**Lakshya Pandey** — ML Engineer | Python · Scikit-learn · Healthcare AI

[![Email](https://img.shields.io/badge/Email-pandeylakshya207%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:pandeylakshya207@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/YOUR_LINKEDIN)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit-111?style=flat-square&logo=vercel&logoColor=white)](https://YOUR_PORTFOLIO_SITE)

**Aaryan Sharma** — UI/UX & Integration

For bug reports and feature requests, please [open an issue](https://github.com/pandeylakshya207-max/Nirog-Health/issues).

---

> *"The goal isn't a working model — it's a tool that helps someone make a better health decision."*
