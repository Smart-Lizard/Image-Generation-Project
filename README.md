**Aiding Medical Diagnosis through Image Synthesis and Classification**

I have developed a system that enables medical practitioners to generate visual representations of medical conditions based on textual descriptions of diagnoses. This is achieved by fine-tuning a Stable Diffusion model using Low-Rank Adaptation (LoRA) on a domain-specific medical imaging dataset. To assess the quality of the generated images, I trained a supervised image classification model, using ResNet18, on that same dataset. This classification model then serves as an evaluation metric by comparing generated images against real medical images. For this specific implementation of my project, I am using the MedMNIST dataset. More specifically, the PathMNIST subset within that dataset.

Metrics used to quantify results are accuracy, AUC, confusion matrix, precision, recall, and F1 score.
A quick summary of the results achieved in this project:
Classification model has a final accuracy of 99.76%, and an Area Under Curve (AUC) of 1.000.
Best version of trained stable diffusion has an F1 score of 0.6778.

**Classification**

I started off by training a classification model within the ChestMNIST dataset, which is another subset within MedMNIST. However, the results from training were quite low and undesirable, as the model could not effectively detect diseases that were prevalent within x-rays of chests. This turned out to be because of the low data difference between different labels of images. Finding a better distributed dataset was crucial, as with the PathMNIST dataset, the model turned out to be very successful.

For more details and results, refer to the file named "classification.pdf" within the "results" folder of the repository. It includes graphs, process, and results.

**Generation**

I transferred a script that trains Low-Rank Adaptation (LoRA) on Stable diffusion from Hugging Face to a colab notebook for increased control of training. From there, I created different versions, improved the code, and tweaked parameters until I got the training to provide results that were desirable. The generation model can now successfully generate images for each label correctly, albeit it will be wrong some of the time. This issue will be mitigated through the constant checking from the high-accuracy classification model. In a system, if an issue is to be found in the generated image, the classification model will let the generation model regenerate the image until it gets it right.

For more details and results, refer to the file named "generation.pdf" within the "results" folder of the repository. It includes graphs, process, and results.
