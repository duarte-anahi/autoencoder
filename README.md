# Character Autoencoder

**English** · [Español](README.es.md)

An autoencoder built with TensorFlow/Keras that compresses 7×5 pixel characters into a **2-dimensional latent space** and reconstructs them. Includes a denoising variant that removes random noise from corrupted characters.

![2D latent space](docs/latent-space.png)

## What's inside

1. **Dataset** — 32 characters (A–Z plus symbols) encoded as 7×5 bitmaps in hexadecimal, generated directly in the notebook.
2. **Autoencoder** — dense encoder that compresses each character to 2 values, and a decoder that reconstructs the 35 pixels. Trained for 200 epochs.
3. **Latent space visualization** — every character plotted by its 2D coordinates.
4. **Generation** — decoding an arbitrary point of the latent space to produce a new character.
5. **Denoising autoencoder** — same architecture, trained with noisy inputs and clean targets.

## Results

**Reconstruction:** loss decreases steadily from ~0.65 to ~0.21, and visually similar characters end up close to each other in the latent space.

**Denoising:** works well with low noise and breaks down with high noise.

| 5% noise | 30% noise |
|---|---|
| ![Denoising 5%](docs/denoise-05.png) | ![Denoising 30%](docs/denoise-30.png) |

*Rows: original · noisy input · reconstruction.*

With 30% noise (about 11 of 35 pixels flipped) the character's structure changes too much and the model outputs a different character. With only 32 training samples, the network memorizes the dataset instead of learning a general notion of "shape".

## Running it

Open the notebook in **Google Colab** or Jupyter and run all cells. No external files are needed.

## Tech stack

Python · TensorFlow · Keras · NumPy · Matplotlib
