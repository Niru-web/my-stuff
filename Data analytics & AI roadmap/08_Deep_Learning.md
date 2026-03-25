# 🧠 Deep Learning

#deep-learning #neural-networks #pytorch #transformers #cnn #advanced

> 📖 **What is this?**
> Deep Learning uses artificial neural networks with many layers to learn complex patterns. It powers image recognition, language models (ChatGPT), speech recognition, and generative AI.

---

## 🎯 Why Deep Learning?

- Powers: ChatGPT, DALL-E, self-driving cars, medical imaging AI, voice assistants
- Automatically learns features — no manual feature engineering required
- State-of-the-art for images, text, audio, and video data
- Essential skill for AI Engineering and ML Engineer roles

---

## 📦 Key Concepts

### 1. Neural Networks — The Basics

```
Input Layer → Hidden Layers → Output Layer
     ↑               ↑              ↑
  (features)   (learned patterns)  (prediction)
```

- **Neuron** — weighted sum of inputs + activation function
- **Weights & Biases** — parameters learned during training
- **Activation Functions:**
  - **ReLU** — `max(0, x)` — most common for hidden layers
  - **Sigmoid** — outputs 0–1 — used for binary classification
  - **Softmax** — outputs probabilities summing to 1 — used for multi-class
- **Forward Pass** — compute prediction from input to output
- **Loss Function** — measures prediction error (MSE, CrossEntropy)
- **Backpropagation** — compute gradients using chain rule
- **Gradient Descent** — update weights to minimize loss

### 2. Training Deep Networks

| Hyperparameter | What it Controls |
|----------------|-----------------|
| Learning Rate | Step size for weight updates (too high = diverge, too low = slow) |
| Batch Size | Samples per gradient update (32–256 typical) |
| Epochs | Full passes through training data |
| Dropout | Randomly zero neurons to prevent overfitting |
| Batch Norm | Normalize layer inputs — stabilizes + speeds training |

**Optimizers:** SGD → Momentum → RMSProp → **Adam** (most commonly used)

### 3. Convolutional Neural Networks (CNNs)

> Designed for **image data**

- **Convolution Layer** — apply filters to detect edges, textures, shapes
- **Pooling Layer** — reduce spatial dimensions (MaxPool, AvgPool)
- **Fully Connected Layer** — final classification head
- **Feature Maps** — learned representations at each layer

**Popular Architectures:**
- VGG16 — simple, deep (16 layers)
- ResNet — skip connections solve vanishing gradients
- EfficientNet — best accuracy/efficiency trade-off

### 4. Recurrent Neural Networks (RNNs)

> Designed for **sequential data** (text, time series, audio)

- **RNN** — maintains hidden state across time steps
- **LSTM** — Long Short-Term Memory; handles long-range dependencies
- **GRU** — Gated Recurrent Unit; simpler and faster than LSTM
- **Vanishing Gradient Problem** — why plain RNNs fail on long sequences

### 5. Transformers & Attention

> The architecture behind GPT, BERT, and all modern LLMs

- **Self-Attention** — each token attends to all other tokens in context
- **Multi-Head Attention** — run attention in parallel across heads
- **Positional Encoding** — inject position information (no recurrence)
- **BERT** — encoder-only; used for understanding tasks (classification, NER)
- **GPT** — decoder-only; used for generation tasks (text, code)
- **Fine-tuning** — adapt a pre-trained model to your specific task

### 6. Transfer Learning

> Don't train from scratch — use pre-trained models!

```python
from torchvision import models
import torch.nn as nn

# Load pre-trained ResNet50
model = models.resnet50(pretrained=True)

# Freeze all layers
for param in model.parameters():
    param.requires_grad = False

# Replace final layer for your task
model.fc = nn.Linear(2048, num_classes)
```

### 7. Generative AI

- **GANs** — Generator vs Discriminator compete; used for image synthesis
- **VAEs** — Variational Autoencoders; learn compressed data representations
- **Diffusion Models** — iterative denoising; powers Stable Diffusion, DALL-E
- **LLMs** — Large Language Models: GPT-4, Claude, Gemini, Llama

---

## 🌍 Real-World Examples

- **ResNet detects** tumors in X-rays with radiologist-level accuracy
- **LSTM powers** real-time speech-to-text in voice assistants (Siri, Alexa)
- **GPT-4 generates** working code, legal summaries, and creative writing
- **CNNs in Tesla's** autopilot detect lanes, vehicles, and pedestrians at 60fps
- **Diffusion models** generate photorealistic images from text prompts

---

## 🛠️ Tools & Technologies

- **PyTorch** — most popular for research and production (recommended)
- **TensorFlow / Keras** — Google's DL framework (easier for beginners)
- **Hugging Face Transformers** — pre-trained NLP/vision models library
- **Google Colab / Kaggle** — free GPU notebooks (essential for DL)
- **Weights & Biases (W&B)** — visualize training curves, compare runs
- **ONNX** — framework-agnostic model export for deployment
- **torchvision / torchtext** — data utilities for images and text

```python
import torch
import torch.nn as nn

class SimpleNN(nn.Module):
    def __init__(self):
        super().__init__()
        self.net = nn.Sequential(
            nn.Linear(784, 256),
            nn.ReLU(),
            nn.Dropout(0.3),
            nn.Linear(256, 128),
            nn.ReLU(),
            nn.Linear(128, 10)
        )
    
    def forward(self, x):
        return self.net(x)

model = SimpleNN()
optimizer = torch.optim.Adam(model.parameters(), lr=1e-3)
criterion = nn.CrossEntropyLoss()
```

---

## ✅ Mini Practice Tasks

1. Build a fully connected neural network to classify MNIST digits (target: 97%+)
2. Train a CNN on CIFAR-10 — achieve 70%+ test accuracy
3. Use pre-trained ResNet50 with transfer learning on a custom 5-class image dataset
4. Use Hugging Face to load `distilbert-base-uncased` and classify sentiment
5. Fine-tune a small GPT-2 model on a text dataset of your choice

---

## 🔗 Internal Links

- [[07_Machine_Learning|→ Machine Learning]]
- [[01_Mathematics|→ Mathematics (backprop needs calculus)]]
- [[09_MLOps|→ MLOps (deploy your DL models)]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

You can build deep learning models. Now learn how to deploy and maintain them in production!

**→ [[09_MLOps|MLOps]]**

> 💡 **Start Smart:** Don't train from scratch. Use pre-trained models and transfer learning. It's faster, cheaper, and often performs better than training from zero — especially with limited data.
