# DeepLearningProject25
Github repository for the deep learning project of me and Enrico for the 2025 DL course, on few shot classification
Given the Oxford Flower dataset, divided in Base and Novel classes, for the Base class we have k = 10 images for training for every class, instead for the novel ones we don't have any.
The aim is to find a way to improve CLIP zero shot  classification performance for the base class, without worsening (preferably improving) the performance on the novel classes.

# Starting approaches

We have two (or maybe more) possible ways to proceed:
- condition the model via trainable tokens ( prompt tuning ): the logic approach is to try to use Cocoop to improve the zero-shot performance of CLIP, and then maybe fine tune the weights of the prompt using the training dataset we have and possibly data augmentation/ generation
- tune small subset of parameters: use parameter efficient tuning using the training data and data augmentation/ generation on a small subset of parameters, a nice approach is layer normalization tuning, to allow the model to adapt to the domain transfer. Pros: can be very efficient since the number of parameters to tune is small, has shown great promise. Cons: we have to modify a bit more the architecture 

# Other possible approaches
-CLIP adapter: add a MLP on top of the visual/text encoder and learn the weight using the training data while keeping fixed the other parameters
Pros: easy to implement, less computationally expensive, we could find variants . Cons: not particularly original and risk of overfitting

- other approaches in the papers that we have on github that we still have to read/discuss
