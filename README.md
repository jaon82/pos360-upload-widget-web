# Upload Widget Web

A React-based file upload widget with drag-and-drop support, image compression, and real-time upload progress tracking.

## Features

- Drag-and-drop file upload zone
- Client-side image compression (converts to WebP, resizable up to 1000×1000px)
- Real-time upload progress with circular progress indicator
- Cancel and retry individual uploads
- Collapsible/minimized widget with animated border when uploads are in progress
- Upload list with per-item status (progress, success, error, canceled)

## Tech Stack

- **React 19** with TypeScript
- **Vite** — build tool and dev server
- **Zustand** + **Immer** — state management
- **Tailwind CSS** — styling
- **Radix UI** — accessible UI primitives (Collapsible, Progress, ScrollArea)
- **Motion (Framer Motion)** — animations
- **react-dropzone** — drag-and-drop file input
- **Axios** — HTTP client with upload progress support

## Getting Started

### Prerequisites

- Node.js 18+
- A running backend API at `http://localhost:3333` with a `POST /uploads` endpoint that accepts `multipart/form-data` and returns `{ url: string }`

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

### Build

```bash
npm run build
```

### Preview production build

```bash
npm run preview
```

## Project Structure

```
src/
├── components/          # UI components
│   ├── upload-widget.tsx                  # Root widget (collapsible, animated)
│   ├── upload-widget-dropzone.tsx         # Drag-and-drop file input
│   ├── upload-widget-header.tsx           # Widget header with overall progress
│   ├── upload-widget-minimized-button.tsx # Minimized state button
│   ├── upload-widget-title.tsx            # Widget title
│   ├── upload-widget-upload-item.tsx      # Individual upload row
│   ├── upload-widget-upload-list.tsx      # Scrollable list of uploads
│   └── ui/
│       ├── button.tsx                     # Reusable button component
│       └── circular-progress-bar.tsx      # SVG circular progress indicator
├── http/
│   └── upload-file-to-storage.ts          # Axios upload request
├── store/
│   └── uploads.ts                         # Zustand store for upload state
└── utils/
    ├── compress-image.ts                  # Client-side WebP image compression
    ├── download-url.ts                    # URL download helper
    └── format-bytes.ts                    # Byte size formatting
```

## API

The widget expects a backend endpoint:

```
POST http://localhost:3333/uploads
Content-Type: multipart/form-data

Body: { file: <File> }
Response: { url: string }
```
