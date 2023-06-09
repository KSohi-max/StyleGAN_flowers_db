# StyleGAN_flowers

## Introduction

With the unprecedented advancements in computational optimization methods and physical hardware such as GPU computing, it comes to no surprise that the last decade has seen deep learning in widespread applications since its conception in the 70's. Some modern applications span the fields of medicine, art & music, finance, linguistics and even to some degree, STEM. Some of the greatest advancements have been made in image generation.

## Literature Review

In 2014, Goodfellow, I.J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., & Bengio, Y., proposed Generative Adversarial Network (GAN) – a deep neural network architecture capable of generating new data. The idea behind GAN was to make neural networks – a generator and a discriminator - compete against each other to improve performance (Géron, A., 2019). In the recent years, GAN had proven to be very successful in various computer vision applications such as image generation – producing photo-realistic images. However, generators used in the architecture were poorly understood and operated as black box models with little to no ability to control high-level attributes of images produced (Liu, Y., 2019). In addition to the lack of control in image modifications, GANs faced challenges such as difficulties in training known as mode collapse – gradual decrease in diversifications of the generator’s outputs (Géron, A., 2019).

To overcome the such challenges of GAN architecture, Nvidia team introduced StyleGAN in 2018 (Karras, T., Laine, S., & Aila, T., 2019). Through re-designing the generator architecture with the usage of style transfer techniques (Géron, A., 2019), Nvidia team allowed control of image synthesis process, further advancing the quality of the generated images. This modification in the architecture lead to ‘automatic, unsupervised separation of high-level attributes [e.g., pose, identity] from stochastic variation (e.g., freckles, hair) in the generated images’ and enabled ‘intuitive scale-specific mixing and interpolation operations’ (Karras, T. et al., 2019). Ultimately, the distinguishing features of StyleGAN were the Mapping Network – mapping the latent representation z into vector w - and the Synthesis Network – generating images with the added noise followed by Adaptive Instance Normalization (AdaIN) (Karras, T. et al., 2019). The added noise inputs were particularly important in adding stochasticity to each part of the image (Géron, A., 2019). StyleGAN has been trained on multiple image topics such as cats and cars (Karras, T. et al., 2019) and Image2StyleGAN (Abdal, R., Qin, Y., & Wonka, P., 2019) – converting colour images to StyleGAN vectors – and StyleGAN-Encoder (Nikitko, 2018) are some examples of literatures exploring StyleGAN. In 2020, Nvidia team re-visited the original StyleGAN architecture to identify and resolve multiple image quality issues with the original StyleGAN (Karras, T., Laine, S., Aittala, M., & Hellsten, J., 2019). They proposed changes in both model architecture and training methods to further improve image quality and advance training performance (Karras, T. et al., 2019).

Our goal of this project is to re-train the pre-trained Keras StyleGAN model (Mann, M., 2019) with flower_dataset in an attempt to produce photo-realistic images of flowers.

## Results

Figure 6: Last Trained image generated by StyleGAN - i200ii.jpg

![Figure 6: Last Trained image generated by StyleGAN - i200ii.jpg](https://github.com/KSohi-max/StyleGAN_flowers_db/blob/main/Figures/Fig%206%20-%20i200ii.jpg)

In Figure 6 shown above, we can begin to differentiate the flowers from the foilage that surround the flower in the image. In addition, colours and shape of the flowers are more defined. The petals of the flowers can be seen very clearly and there is a lot more gentler/smoother shading of colours within the petals of the flowers.

While categories of generated flower images are randomly chosen in the code, as evident through the resulting image samples, some flower types are generated more often than the other. For instance, number of images generated that look similar to Watercress and Passion Flower are prominent in Figure 6. This is due to the imbalance in our dataset. Number of images stored per class in the VGG dataset [7] were not balanced and as a result, classes that contained higher number of image examples in the dataset were more dominantly selected by the generator.

For additional discussions on results, pleasee see [Final_SCS3546_008_TermProject_v200818.ipynb](https://github.com/KSohi-max/StyleGAN_flowers_db/blob/main/Final_SCS3546_008_TermProject_v200818.ipynb)

## Limitations

There are very specific limitations to this project (dataset and code) that need to be acknowledged as part of the analaysis of results for the above Keras-based StyleGAN model.

First, the Keras model publically available for StyleGAN (manicman1999) did not include specific mathematical/graphical interpretation for the results. Considerable time was allocated to cleaning and modifying the existing code and subsequently running it for 7 days. Further improvements that may help with the interpretation of results could include a numerical and graphical representation of improvements in images in a given interval of steps. This would allow for better discussion and analysis of the results for future model runs.

Second, the flower dataset is not ideal for results interpretation. In looking at Flickr- Faces-HQ (FFHQ) dataset, it would be somewhat intuitive to note if a human face image generated by GAN is not of proper proportions. Example, the nose is slightly off on the face or eyes are larger than anticipated, etc. These errors would allow for a visual cue to further investigate the results for issues or errors. But with flowers dataset the visual cues are not as intuitive as is the case with human faces. Flowers, in general, are easily mutable in nature depending on their environment and cross-breeding. So for this project, it was diffcult to note if the flower created by the styles were "complete". The only visual cue was resolution of the pictures and intuitive interpretation of how the petals and foilage changed from one step to the next. The results offer an abstraction of images that could exist in nature. Although there is generally symmetry in flower in nature, flowers are known to be asymmetric as well. So perhaps a more symmetric flower dataset if ran to million steps may yield better interpretable results. It is also important to note that the dataset size is significantly small when compared to the FFHQ which was 50K images. So the random selection of images as input into this model is limited. Additionally, in retrospect, it would have been wise to keep the 8 FC layers, as the relationships between the image properties of the flowers could be more complex than facial images.

Third, for GAN specifically, more time and computing power is required. Even after 7 days of running the model, the results are not conclusive. But doing a million steps would require 35 days of continuously running the model. This limitation also played into difficulties in interpreting the results as the images produced by StyleGAN still remain incomplete.

Fourth, fine-tuning parameters can help identify different styles in addition to above may produce better and inerpretable results.

Finally, styles could not be identified clearly with our model. Again, this may be attributed to the 5 FC layers used instead of the 8. More effort in coding and computing time would be helpful to further improve the model and produce results that would be intuitively interpretable even with the flower dataset.

## Conclusions

StyleGAN model has a significant number of facets within its code that can be manipulated to improve the learning process of the adversarial model. To ensure that they all work together to produce clear and interpretable results is a challenge. GAN models in themselves are not easy to manipulate but StyleGAN attempts to address these challenges to improve the adversarial learning process.

Nonetheless, other challenges remain that seem to impact the results beyond the challenges of code creation, like type of dataset, computing power, time allocated and intuitiveness of results interpretation.

Our model attempted to address some these challenges to produce results that do show improvements in StyleGAN produced images over time. Although we were unable to produce conclusive results similar to the ones in StyleGAN paper, we were able to mimic a few key aspects of this complex model in our project work.

## References

Abdal, R., Qin, Y., & Wonka, P. (2019). Image2StyleGAN: How to Embed Images Into the StyleGAN Latent Space?. International Conference on Computer Vision (ICCV). 4431-4440. doi: 10.1109/ICCV.2019.00453.

Brock, A., Donahue, J., & Simonyan, K. (2019). Large Scale GAN Training for High Fidelity Natural Image Syntehsis. International Conference on Learning Representations. Retrieved from https://arxiv.org/pdf/1809.11096.pdf.

Nikitko, D. (2018). Stylegan-Endocer. Github Repository, https://github.com/Puzer/stylegan-encoder.

Géron, A. (2019). Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow. Sebastopol, CA: O'Reilly.

Goodfellow, I.J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., & Bengio, Y. (2014). Generative adversarial nets. Advances in neural information processing systems. 2672-2680. Retrieved from https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf.

Karras, T., Laine, S., & Aila, T. (2019). A Style-Based Generator Architecture for Generative Adversarial Networks. Conference on Computer Vision and Pattern Recognition (CVPR). 4396-4405. doi: 10.1109/CVPR.2019.00453.

Karras, T., Laine, S., Aittala, M., & Hellsten, J. (2019). Analyzing and Improving the Image Quality of StyleGAN. Conference on Computer Vision and Pattern Recognition (CVPR). 8110-8119. Retrieved from https://arxiv.org/pdf/1912.04958.pdf.

Liu, Y. (2019). Controlled Modification of Generated (Style) GAN Latent Vectors. Retrieved from https://pdfs.semanticscholar.org/6af8/6e7d68f18b61af4ed18deecaef9de2e0ff85.pdf.

Mann, M. (2019). StyleGAN Made with Keras. GitHub Repository, https://academia.stackexchange.com/questions/14010/how-do-you-cite-a-github-repository.


