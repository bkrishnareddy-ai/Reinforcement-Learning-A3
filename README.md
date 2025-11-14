
# 📘 Deep Q-Network (DQN) for Atari Pong  
**Course:** CSCN8020 – Reinforcement Learning Programming  
**Student:** *Krishna Reddy Bovilla*  
**Student ID:** *9050861*

---

## 🌐 Project Repository
GitHub: **https://github.com/bkrishnareddy-ai/Reinforcement-Learning-A3.git**

---

# 📝 Project Description

This project implements a **Deep Q-Network (DQN)** agent trained to play **Atari PongDeterministic-v4**.  
The agent learns directly from **raw pixel input**, using key DeepMind DQN components:

- Convolutional Deep Q-Network  
- Experience Replay  
- Target Network (periodically updated)  
- 4-Frame Stacking (temporal state information)  
- Frame Preprocessing (grayscale → resize → normalize)  
- ε-Greedy Exploration  

The project also includes three controlled experiments analyzing how **batch size** and **target network update frequency** affect learning performance.

---

# 🛠️ Installation & Environment Setup

Follow the steps below to set up the correct environment for running Atari Pong with DQN.

---

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

### ✔ Using Python venv
```bash
python -m venv dqn-pong
source dqn-pong/bin/activate     # Mac/Linux
dqn-pong\Scripts\activate      # Windows
```

---

# 3️⃣ Install Dependencies

You can install dependencies using **either Method A (manual)** or **Method B (`requirements.txt`)**.

---

## 📌 Method A — Manual Installation (Recommended)

### Install core Atari packages:
```bash
pip install -q gym==0.26.2
pip install -q ale-py==0.7.5
pip install -q "autorom[accept-rom-license]"
```

### Install Atari ROMs:
```bash
AutoROM --accept-license
```

### Install PyTorch + supporting packages:
```bash
pip install torch numpy matplotlib tqdm opencv-python Pillow
```

---

## 📌 Method B — Install Everything Using `requirements.txt`

Run:
```bash
pip install -r requirements.txt
```

Then install ROMs:
```bash
AutoROM --accept-license
```

⚠️ **AutoROM must be run at least once** or Pong will not load.

---

# 📁 Project Structure

```
Reinforcement-Learning-A3/
│
├── assignment3_utils.py          # Frame preprocessing utilities
├── assignment3.ipynb    # Full training & experiments notebook
├── requirements.txt              # Package requirements
├── .gitignore                    # Ignored files
├── README.md                     # Documentation
└── report.pdf                    # (Optional) Full written report
```

---

# 🧠 Deep Q-Network Architecture

### 🔹 Input
- 4 stacked grayscale frames (84 × 80)

### 🔹 Convolutional Layers
| Layer | Filters | Kernel | Stride | Activation |
|-------|----------|-----------|------------|--------------|
| Conv1 | 32 | 8×8 | 4 | ReLU |
| Conv2 | 64 | 4×4 | 2 | ReLU |
| Conv3 | 64 | 3×3 | 1 | ReLU |

### 🔹 Fully Connected
- FC1: 512 units  
- Output: 6 Q-values  

This architecture matches the original DeepMind DQN design.

---

# 🧪 Experiments Performed

Three configurations were tested for 100 episodes:

| Experiment | Batch Size | Target Update Rate |
|------------|-------------|----------------------|
| **Baseline** | 8 | 10 episodes |
| **Batch Size 16** | 16 | 10 episodes |
| **Target Update 3** | 8 | 3 episodes |

All results were plotted and analyzed.

---

# 📊 Training Results & Plots

The notebook generates:

### ✔ Score per episode  
### ✔ 5-episode moving average  
### ✔ Combined score comparison  
### ✔ Combined moving-average comparison  

These visualizations allow evaluating stability and performance of each configuration.

---

# 🏁 Key Findings

✔ **Best Configuration:**  
- **Batch Size = 8**  
- **Target Update = 10 episodes**

❌ Larger batch size (16) → Slower learning  
❌ Very frequent target updates (3) → More oscillations, no improvement  

---

# 📚 References

- Mnih et al., *Playing Atari with Deep Reinforcement Learning*  
- Arcade Learning Environment  
- OpenAI Gym Atari  
- PyTorch Documentation  

---

# 🙌 Acknowledgements
Developed as part of **CSCN8020 – Reinforcement Learning Programming**,  
Mohawk College.

---

# 🎉 End of README
