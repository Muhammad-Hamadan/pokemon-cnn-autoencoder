# Pokémon Denoising and CAPTCHA

A deep learning project that classifies Pokémon images with a convolutional neural network (CNN), removes noise from them with an autoencoder, and uses the classifier to run a simple image CAPTCHA.

## Overview

1. **CNN classifier**: identifies which of 10 Pokémon appears in an image.
2. **Autoencoder denoiser**: takes noisy images and reconstructs clean versions.
3. **Image CAPTCHA**: shows a target Pokémon and nine candidates, and the CNN picks the matching one.

## Dataset

The dataset contains images of 10 Pokémon:

Bulbasaur, Charmander, Diglett, Dugtrio, Jigglypuff, Magikarp, Pikachu, Raichu, Squirtle, Starmie

- Images are provided in `Pokemon-images.zip`.
- Filenames begin with the Pokémon's name, followed by an underscore (for example, `Pikachu_01.png`).
- Files containing `aug` are augmented copies and are excluded from the CAPTCHA.

## Project Structure

```
.
├── comp2211_pa2.ipynb      # Main notebook with all code
├── comp2211_pa2.py         # Script version of the notebook
├── cnn_model.keras         # Trained CNN classifier
├── auto_encoder.keras      # Trained autoencoder denoiser
├── Pokemon-images.zip      # Dataset
├── requirements.txt        # Python dependencies
└── README.md
```

## Requirements

- Python 3.13 or newer
- The packages listed in `requirements.txt`

1. Extract the dataset:

   ```powershell
   Expand-Archive -Path Pokemon-images.zip -DestinationPath images
   ```

2. In the notebook, set `image_dir` to the `images` folder.

## Usage

1. Start Jupyter and open the notebook:
2. Run the cells in order. The notebook:
   - loads and preprocesses the images (resized to 64×64, scaled to [0, 1])
   - loads the trained CNN and autoencoder
   - measures CNN accuracy on noisy and denoised images
   - runs the CAPTCHA demo
To retrain the models, run the training cells before the `load_model` lines.
