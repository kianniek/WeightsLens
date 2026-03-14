# WeightsLens

> **Visualize, Compare, and Audit your Neural Network weights in the browser.**

WeightsLens is an open-source web tool designed to bridge the gap between abstract training logs and the raw numerical reality of your models. It provides a visual interface for `.safetensors`, `.pth`, and `.gguf` files.

## Core Functionalities

### 1. Model Upload & Parsing
Support for industry-standard formats with automatic metadata extraction.
* **Supported Formats:** `.safetensors`, `.pth`, `.onnx`, `.bin`, `.h5`.
* **Metadata:** Displays layer shapes, data types (FP32, FP16, INT4), and parameter counts.

### 2. Comparative Analysis (The "Diff" Mode)
Compare two models side-by-side. WeightsLens aligns layers by name and calculates:
- **$\Delta W$ (Weight Difference):** $W_{fine\_tuned} - W_{base}$
- **Cosine Similarity:** Measure how much the directional orientation of weights changed.
- **Magnitude Shift:** Identify which layers were "frozen" vs. which were heavily updated.

### 3. Advanced Visualizations
- **Heatmaps:** Diverging color scales (Red/Blue) for weight magnitudes.
- **Distribution Ridges:** Watch how weight histograms shift across different layers.
- **Sparsity Maps:** Instantly see the percentage of zeroed-out weights (crucial for pruning).

## Getting Started

### Prerequisites
- Python 3.9+ (Backend)
- Node.js 18+ (Frontend)

### Installation
1. **Clone the repo:**
   ```bash
   git clone [https://github.com/your-username/weightslens.git](https://github.com/your-username/weightslens.git)
   cd weightslens
   ```
Setup Backend:

```bash
cd backend
pip install -r requirements.txt
python main.py
```
Setup Frontend:

```bash
cd frontend
npm install
npm run dev
```

# Tech Stack
Frontend: React + Three.js (WebGL) + D3.js
Backend: FastAPI + Safetensors + NumPy
Processing: ONNX Runtime for architecture graph generation

# Privacy & Security
WeightsLens processes files locally or on your private server. By default, no model data is uploaded to third-party cloud storage, ensuring your proprietary weights remain secure.
