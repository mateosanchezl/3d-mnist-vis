# 3D MNIST Neural Network Visualizer

**DISCLAIMER** - As a fun test, I got Opus 4.5 to basically one-shot this whole project!

An immersive 3D web application that reveals the inner workings of a deep neural network as it learns to recognize handwritten digits from the MNIST dataset.

## 🚀 Live Demo

**[3d-mnist-vis.vercel.app](https://3d-mnist-vis.vercel.app)**

## Features

- **3D Visualization**: Explore the neural network as a tangible 3D structure using orbit controls
- **Real-time Training**: Watch the network learn with animated forward propagation and backpropagation
- **Glass Box AI**: See input voxels, hidden neurons, weight connections, and output probabilities
- **Interactive Controls**: Adjust learning rate, batch size, and animation speed
- **Live Metrics**: Track loss and accuracy with real-time charts

## How It Works

The app runs a real neural network entirely in your browser using TensorFlow.js. Training happens in a Web Worker to keep the UI responsive at 60 FPS.

### Architecture

```
Input Layer (784 voxels) → Hidden Layer 1 (128 neurons) → Hidden Layer 2 (64 neurons) → Output Layer (10 digits)
```

### Training Flow

1. **Initialize** - Loads the MNIST dataset (~55MB) and creates a fresh neural network
2. **Forward Pass** - Input image flows through the network, activations pulse through each layer
3. **Prediction** - Output layer shows probabilities for digits 0-9
4. **Backpropagation** - If wrong, error flows backward (shown with red tint)
5. **Weight Updates** - Connection colors update as weights change

### Visual Encoding

| Element             | Meaning              |
| ------------------- | -------------------- |
| **Cyan lines**      | Positive weights     |
| **Magenta lines**   | Negative weights     |
| **Line brightness** | Weight magnitude     |
| **Neuron glow**     | Activation intensity |
| **Green output**    | Correct prediction   |
| **Red output**      | Incorrect prediction |

## Tech Stack

- **React 19** with TypeScript
- **React Three Fiber** for declarative 3D rendering
- **TensorFlow.js** for WebGL-accelerated machine learning
- **Zustand** for high-performance state management
- **Vite** for fast development builds

## Controls

- **Drag**: Rotate the view
- **Scroll**: Zoom in/out
- **Right-click drag**: Pan the camera

## Local Development

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build
```

The MNIST dataset is included in the repo, so no additional setup is required.

## Performance Notes

Due to the high number of neural connections (~100,000), the visualizer uses:

- Instanced rendering for efficient GPU utilization
- Connection subsampling to maintain 60 FPS
- Weight thresholding to hide weak connections
- Web Worker for training to keep the UI responsive

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## License

MIT
