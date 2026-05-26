# Deep Learning Architectures — Summary

Deep Learning relies on different **architectures**, and each one is designed for specific tasks such as images, text, generation, and translation.

---

## 1. Convolutional Neural Networks (CNN)

CNNs are mainly used for **image data** and grid-like structured data.

### How it works:
- **Convolution Layer:** Detects features like edges and shapes  
- **ReLU:** Adds non-linearity to improve learning  
- **Pooling:** Reduces the size of the data  
- **Fully Connected Layer:** Produces the final output  

### Applications:
- Image recognition  
- Object detection  
- Medical and industrial classification  

---

## 2. Recurrent Neural Networks (RNN)

RNNs are designed for **sequential data** such as text and speech.

### How it works:
- Maintains an internal “memory” of previous inputs  
- Processes data step by step  

### Problem:
- Difficulty remembering long-term dependencies (Vanishing Gradient problem)

### Solution:
- **LSTM (Long Short-Term Memory)**  
- **GRU (Gated Recurrent Unit)**  

### Applications:
- Machine translation  
- Text analysis  
- Speech recognition  

---

## 3. Generative Adversarial Networks (GAN)

GANs are used to **generate new data** similar to real data.

### Components:
- **Generator:** Creates fake data  
- **Discriminator:** Distinguishes real from fake data  

### Idea:
- Both networks compete to improve each other’s performance  

### Applications:
- Realistic image generation  
- Human face creation  
- Image editing  

---

## 4. Transformers

Transformers are the most powerful and modern architecture, especially for **Natural Language Processing (NLP)**.

### Core Idea:
- Uses the **Attention Mechanism**
- Processes data in parallel instead of sequentially  

### Advantages:
- Faster than RNNs  
- Better understanding of word relationships  

### Applications:
- Translation  
- Chatbots  
- Text summarization  

---

## 5. Encoder–Decoder Architecture

Used for **sequence-to-sequence transformation** tasks.

### How it works:
- **Encoder:** Converts input into a meaningful representation  
- **Decoder:** Converts representation into output  

### Applications:
- Machine translation  
- Text summarization  
- Speech-to-text conversion  

---

# Quick Summary

| Architecture | Best For |
|--------------|----------|
| CNN | Images and computer vision |
| RNN | Sequential data (text, speech) |
| GAN | Data and image generation |
| Transformers | Natural language processing and modern AI |
| Encoder–Decoder | Translation and data transformation |

---

# Main Idea

Each deep learning architecture is designed for a specific type of problem:

- **Images → CNN**  
- **Text → RNN / Transformers**  
- **Generation → GAN**  
- **Translation & Conversion → Encoder–Decoder**
