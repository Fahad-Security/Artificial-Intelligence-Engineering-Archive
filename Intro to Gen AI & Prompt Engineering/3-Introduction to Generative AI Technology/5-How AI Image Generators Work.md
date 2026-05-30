# Diffusion Models — The Technology Behind Modern AI Image Generation

This lesson explains how modern image generation systems work, including:

- Stable Diffusion
- DALL·E
- Imagen

It also connects these concepts to topics you have already learned, such as:

- Machine Learning
- Deep Learning
- Neural Networks
- Transformers
- Generative AI

---

# Why Are GANs Used Less Today?

Before Diffusion Models became popular, the most common image generation approach was:

# GAN (Generative Adversarial Network)

A GAN consists of two neural networks:

## 1. Generator

The Generator tries to create fake images.

Examples:

- Human faces
- Cars
- Cats

---

## 2. Discriminator

The Discriminator tries to determine whether an image is:

- Real
- Fake

---

The two networks compete against each other.

```text
Noise
  ↓
Generator
  ↓
Fake Image
  ↓
Discriminator
  ↓
Real or Fake?
```

Over time, both networks improve.

---

# The Problem with GANs

GANs suffer from several challenges.

## Mode Collapse

The Generator may discover one successful image pattern and repeatedly generate similar images.

Instead of producing millions of unique faces:

```text
Face A
Face A
Face A
Face A
```

The model becomes stuck producing similar outputs.

---

Other issues include:

- Difficult training
- Unstable optimization
- Sensitivity to hyperparameters

Because of these limitations, Diffusion Models became the dominant approach.

---

# The Brilliant Idea Behind Diffusion Models

Instead of telling a neural network:

> Draw a rabbit from scratch.

We tell it:

> Learn how to remove noise.

This turns out to be much easier.

---

# Training Phase

Suppose we start with an image of a rabbit.

```text
Rabbit
```

We gradually add noise.

```text
Rabbit + Noise
```

Then more noise.

```text
Rabbit + More Noise
```

Then even more.

```text
Rabbit + More More Noise
```

Until we end up with:

```text
Random Noise
```

---

Visually:

```text
Rabbit
 ↓
10% Noise
 ↓
30% Noise
 ↓
60% Noise
 ↓
100% Noise
```

This process is called:

# Forward Diffusion

The image is gradually corrupted by noise.

---

# What Does the Network Learn?

The network does not learn how to draw a rabbit directly.

Instead, it learns:

> What noise was added to the image?

The input becomes:

```text
Noisy Image
+
Time Step (T)
```

The network predicts:

```text
Estimated Noise
```

---

Then the noise can be removed.

```text
Noisy Image
-
Predicted Noise
=
Cleaner Image
```

---

# Why Predict Noise?

Predicting noise is mathematically easier.

Instead of asking:

```text
Draw a rabbit completely.
```

We ask:

```text
Tell me what should be removed.
```

This makes training more stable and reliable than GANs.

---

# How Is a New Image Generated?

Now comes the magic.

After training is complete, generation starts with:

```text
Random Noise
```

There is no image yet.

---

## Step 1

The network predicts noise.

```text
Noise
↓
Remove Noise
↓
Vague Shape
```

---

## Step 2

More noise is removed.

```text
Vague Shape
↓
Remove Noise
↓
Early Features
```

---

## Step 3

Additional noise is removed.

```text
Features
↓
Remove Noise
↓
Clearer Image
```

---

After dozens or hundreds of iterations:

```text
Noise
↓
↓
↓
Rabbit
```

---

This is why the method is called:

# Diffusion Model

Because it reverses the process of gradually adding noise.

---

# Where Does Text Come In?

A key question is:

How can the model generate:

> A frog on stilts

instead of a rabbit?

---

This is where Transformers enter the process.

The text:

```text
frog on stilts
```

is converted into an:

# Embedding

An embedding is a vector that represents the meaning of the text.

```text
Text
↓
Embedding
↓
Vector Representation
```

---

The embedding is then fed into the Diffusion Model.

```text
Noise
+
Text Embedding
↓
Diffusion Network
↓
Less Noise
```

---

At every denoising step, the model remembers:

> I am trying to generate a frog on stilts.

Not just any random image.

---

# Classifier-Free Guidance (CFG)

One of the most important innovations in modern image generation is:

# Classifier-Free Guidance

The model runs twice.

---

## First Run

With the prompt.

```text
"A frog on stilts"
```

---

## Second Run

Without the prompt.

```text
Nothing
```

---

The difference is computed.

```text
With Text
-
Without Text
=
Text Signal
```

---

The signal is amplified.

As a result, the generated image follows the prompt more closely.

---

Without guidance:

```text
An ordinary kitchen
```

---

With guidance:

```text
A muppet cooking in a kitchen
```

The image becomes much more aligned with the requested description.

---

# Connecting This to Previous Topics

Now the full picture becomes clear.

```text
Machine Learning
        ↓
Deep Learning
        ↓
Neural Networks
        ↓
Transformers
        ↓
GPT-Style Text Understanding
        ↓
Text Embeddings
        ↓
Diffusion Models
        ↓
Image Generation
```

---

# What Happens When You Enter a Prompt?

Example:

> "A cyberpunk rabbit wearing sunglasses"

The process looks like this:

```text
Text Prompt
↓
Transformer
↓
Embedding
↓
Diffusion Model
↓
Random Noise
↓
Less Noise
↓
Less Noise
↓
Less Noise
↓
Final Image
```

---

# Final Conclusion

Modern image generation systems such as Stable Diffusion, DALL·E, and Imagen do not directly draw images.

Instead, they:

1. Start with completely random noise
2. Convert text into mathematical embeddings
3. Use a Diffusion Model to remove noise step by step
4. Gradually reveal meaningful structures
5. Produce a final image that matches the text prompt

This combination of Transformers, Embeddings, and Diffusion Models is one of the most important breakthroughs behind today's AI image generation revolution.
