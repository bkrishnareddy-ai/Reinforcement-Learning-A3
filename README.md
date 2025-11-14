# 📘 Deep Q-Network (DQN) for Atari Pong  
**Course:** CSCN8020 – Reinforcement Learning Programming  
**Student:** *Krishna Reddy Bovilla*  
**Student ID:** *9050861*

---

## 🌐 Project Repository
GitHub: **https://github.com/bkrishnareddy-ai/Reinforcement-Learning-A3.git**

---

## 📝 Project Description

This project implements a **Deep Q-Network (DQN)** agent capable of learning to play **Atari Pong** from **raw pixel input** using reinforcement learning.  
The implementation faithfully follows the original DeepMind DQN design, including:

- Experience Replay  
- Target Network  
- Convolutional Q-Network  
- Frame Preprocessing (Grayscale → Resize → Normalize)  
- Frame Stacking for temporal representation  
- ε-Greedy Exploration Strategy  

The project also includes **three controlled hyperparameter experiments** and a **full training analysis**, complete with plots and commentary.

---

# 🛠️ Installation & Environment Setup

## 1️⃣ Clone the Repository
```bash
git clone https://github.com/bkrishnareddy-ai/Reinforcement-Learning-A3.git
cd Reinforcement-Learning-A3
```

---

## 2️⃣ Create a Python Environment

### ✔ Using Conda
```bash
conda create -n dqn-pong python=3.10 -y
conda activate dqn-pong
```

### ✔ Using venv
```bash
python -m venv dqn-pong
source dqn-pong/bin/activate   # Mac/Linux
dqn-pong\Scripts\activate    # Windows
```

---

## 3️⃣ Install Dependencies

### Required Python Packages
```bash
pip install -q gym==0.26.2
pip install -q ale-py==0.7.5
pip install -q "autorom[accept-rom-license]"
AutoROM --accept-license
pip install torch numpy matplotlib tqdm
```

After installation, **AutoROM must be run** to download and install Atari ROMs.

---

# ▶️ Running the Notebook

Launch Jupyter and open the main notebook:

```bash
jupyter notebook
```

Open:

```
assignment3.ipynb
```

---

# 📁 Project Structure

```
Reinforcement-Learning-A3/
│
├── assignment3_utils.py          # Frame preprocessing functions
├── assignment3.ipynb    # Main notebook with full pipeline
├── requirements.txt                    # Required libraries
├── README.md                     # Documentation
└── report.pdf                    # Final assignment report (optional)
```

---

# 🧠 Model Architecture (DeepMind DQN)

### Input  
- 4 stacked grayscale frames (84 × 80)

### Convolutional Feature Extractor  
| Layer | Filters | Kernel | Stride | Activation |
|-------|----------|-----------|------------|--------------|
| Conv1 | 32 | 8×8 | 4 | ReLU |
| Conv2 | 64 | 4×4 | 2 | ReLU |
| Conv3 | 64 | 3×3 | 1 | ReLU |

### Fully Connected  
- FC1: 512 units (ReLU)  
- Output: 6 Q-values representing Pong actions  

This architecture mirrors the original Deep Q-Network used by DeepMind.

---

# 🧪 Experimental Configurations

Three training configurations were tested for 100 episodes each:

| Experiment | Batch Size | Target Update |
|------------|-------------|----------------|
| **Baseline** | 8 | Every 10 episodes |
| **Batch Size 16** | 16 | Every 10 episodes |
| **Target Update 3** | 8 | Every 3 episodes |

---

# 📊 Visualization & Analysis

The notebook generates:

### ➤ Individual Plots
- Score per episode  
- Moving average of last 5 episodes  

### ➤ Combined Comparison Plots
- Baseline vs. Batch 16 vs. Target Update 3 (score)
- Baseline vs. Batch 16 vs. Target Update 3 (moving average)

These help illustrate how hyperparameters affect learning.

---

# 🏁 Summary of Findings

### 🔹 Best Configuration  
✔ **Batch size: 8**  
✔ **Target update: 10**  

### 🔹 Why It Works Best
- Most stable reward behaviour  
- Preserves gradient sensitivity  
- Avoids oversmoothing from large batches  
- Avoids instability from overly frequent target updates  

### 🔹 Other Findings
- **Batch size 16** slowed learning  
- **Target update 3** caused unnecessary oscillations  

---


# 🙌 Acknowledgements

This project was developed for **CSCN8020 – Reinforcement Learning Programming**,  
Mohawk College.

---

# 🎉 End of README

