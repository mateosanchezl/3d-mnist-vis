# 3D MNIST Neural Network Visualizer

An immersive 3D web application that reveals the inner workings of a deep neural network as it learns to recognize handwritten digits from the MNIST dataset.

## Features

- **3D Visualization**: Explore the neural network as a tangible 3D structure using orbit controls
- **Real-time Training**: Watch the network learn with animated forward propagation and backpropagation
- **Glass Box AI**: See input voxels, hidden neurons, weight connections, and output probabilities
- **Interactive Controls**: Adjust learning rate, batch size, and animation speed
- **Live Metrics**: Track loss and accuracy with real-time charts

## Architecture

```
Input Layer (784 voxels) → Hidden Layer 1 (128 neurons) → Hidden Layer 2 (64 neurons) → Output Layer (10 digits)
```

## Tech Stack

- **React 18** with TypeScript
- **React Three Fiber** for declarative 3D rendering
- **TensorFlow.js** for WebGL-accelerated machine learning
- **Zustand** for high-performance state management
- **Vite** for fast development builds

## Getting Started

### 1. Install dependencies

```bash
npm install
```

### 2. Download MNIST Dataset

The MNIST dataset must be downloaded separately. Create the data folder and download the files:

```bash
mkdir -p public/data
cd public/data
```

Download these 4 files from the MNIST database or any mirror:

| File                      | Description                      |
| ------------------------- | -------------------------------- |
| `train-images.idx3-ubyte` | Training images (60,000 samples) |
| `train-labels.idx1-ubyte` | Training labels                  |
| `t10k-images.idx3-ubyte`  | Test images (10,000 samples)     |
| `t10k-labels.idx1-ubyte`  | Test labels                      |

**Alternative download sources:**

- [Kaggle MNIST](https://www.kaggle.com/datasets/hojjatk/mnist-dataset)

If files are compressed (`.gz` or `.zip`), extract them first.

### 3. Start development server

```bash
npm run dev
```

### 4. Build for production

```bash
npm run build
```

## Controls

- **Drag**: Rotate the view
- **Scroll**: Zoom in/out
- **Right-click drag**: Pan the camera

## Visual Encoding

- **Cyan lines**: Positive weights
- **Magenta lines**: Negative weights
- **Line brightness**: Weight magnitude
- **Neuron glow**: Activation intensity
- **Green output**: Correct prediction
- **Red output**: Incorrect prediction

## Performance Notes

Due to the high number of neural connections (~62,000), the visualizer uses:

- Instanced rendering for efficient GPU utilization
- Connection subsampling to maintain 60 FPS
- Weight thresholding to hide weak connections
- Web Worker for training to keep the UI responsive
