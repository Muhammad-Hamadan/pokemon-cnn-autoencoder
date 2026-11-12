\# Pokémon Denoising and CAPTCHA



A deep learning project that classifies Pokémon images with a convolutional neural network (CNN), removes noise from them with an autoencoder, and uses the classifier to run a simple image CAPTCHA.



\## Overview



1\. \*\*CNN classifier\*\*: identifies which of 10 Pokémon appears in an image.

2\. \*\*Autoencoder denoiser\*\*: takes noisy images and reconstructs clean versions.

3\. \*\*Image CAPTCHA\*\*: shows a target Pokémon and nine candidates, and the CNN picks the matching one.



\## Dataset



The dataset contains images of 10 Pokémon:



Bulbasaur, Charmander, Diglett, Dugtrio, Jigglypuff, Magikarp, Pikachu, Raichu, Squirtle, Starmie



\- Images are provided in `Pokemon-images.zip`.

\- Filenames begin with the Pokémon's name, followed by an underscore (for example, `Pikachu\_01.png`).

\- Files containing `aug` are augmented copies and are excluded from the CAPTCHA.



\## Project Structure



```

.

├── comp2211\_pa2.ipynb      # Main notebook with all code

├── comp2211\_pa2.py         # Script version of the notebook

├── cnn\_model.keras         # Trained CNN classifier

├── auto\_encoder.keras      # Trained autoencoder denoiser

├── Pokemon-images.zip      # Dataset

├── requirements.txt        # Python dependencies

└── README.md

```



\## Requirements



\- Python 3.13 or newer

\- The packages listed in `requirements.txt`



\## Setup

1\. Install the dependencies:



&#x20;  ```powershell

&#x20;  pip install -r requirements.txt

&#x20;  ```



2\. Extract the dataset:



&#x20;  ```powershell

&#x20;  Expand-Archive -Path Pokemon-images.zip -DestinationPath images

&#x20;  ```



3\. In the notebook, set `image\_dir` to the `images` folder.



\## Usage



1\. Start Jupyter and open the notebook:



&#x20;  ```powershell

&#x20;  jupyter notebook comp2211\_pa2.ipynb

&#x20;  ```



2\. Run the cells in order. The notebook:

&#x20;  - loads and preprocesses the images (resized to \[IMG\_SIZE]×\[IMG\_SIZE], scaled to \[0, 1])

&#x20;  - loads the trained CNN and autoencoder

&#x20;  - measures CNN accuracy on noisy and denoised images

&#x20;  - runs the CAPTCHA demo



To retrain the models, run the training cells before the `load\_model` lines.



\## Preprocessing



\- Images are converted from BGR to RGB.

\- Images are resized to \[IMG\_SIZE]×\[IMG\_SIZE].

\- Pixel values are divided by 255.0 to scale them to \[0, 1].

\- Noise is added to create the noisy inputs for the autoencoder.



\## Results



| Input           | CNN Accuracy |

|-----------------|--------------|

| Noisy images (Training Accuracy)  | \[82.80%]     |

| Denoised images | \[96.00%]     |



\## How the CAPTCHA Works



1\. A random Pokémon is chosen as the target.

2\. Two of its images are selected: one is shown at the top, and the other is placed among the choices.

3\. Eight images of other Pokémon are added as decoys, and the nine choices are shuffled.

4\. The CNN predicts the class of the top image, then selects the choice with the highest score for that class.

5\. The result is shown as "Passed" if the CNN picks the correct image, or "Failed" otherwise.



\## Limitations



\- Only 10 Pokémon classes are supported.

\- Images are small, which limits detail.

\- The CAPTCHA is a demonstration and is not secure against automated attacks.





