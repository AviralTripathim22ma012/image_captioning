# Image Captioning
The process of creating a textual description of a picture using artificial 
intelligence tools like computer vision and natural language processing 
is known as image captioning. 
**ResNet50:** It is a CNN architecture that was developed by Microsoft 
Research for image recognition tasks. It belongs to the family of 
Residual Networks (ResNets) which introduced the concept of skip 
connections to improve the training of very deep neural networks.
**LSTM:** (Long Short-Term Memory) which is a type of recurrent neural 
network (RNN), they have the ability to remember information over a 
long period of time and selectively forget information that is no longer 
needed.
## Why I chose ResNet50 for encoder architecture?
 ResNet50's High Accuracy: ResNet50 is very accurate in image 
classification tasks. 
 Efficient Encoding: ResNet50 is a relatively lightweight
architecture that can efficiently encode images into feature 
vectors, making it a good choice for large datasets.
 ResNet50 has been pretrained on large image datasets such as 
ImageNet, meaning it has already learnt to recognize a wide 
variety of objects and features. This makes it easier to fine-tune
the network for image captioning tasks.
## Why I chose LSTM for decoder architecture?
 LSTM's Sequence Modeling: Using an LSTM as a decoder can help 
to generate more coherent and structured captions that take into 
account the context of previous words.
 Ability to Handle Variable-Length Sequences: LSTM is capable for 
generating captions of varying lengths for different images.
 Data Preprocessing: This entails resizing the picture and turning 
the caption into a string of words.
 The ResNet50 model is then employed to extract high-level 
features from the image. The ResNet50 model produces a 
collection of feature vectors that each represent a different area 
of the image.
 Sequence Modelling: An LSTM network creates the caption by 
taking the feature vectors from the ResNet50 model and feeding 
them into it. 
 Training: A dataset of image-caption pairs is used to train the 
LSTM network. The goal is to reduce the discrepancy between the 
expected and real captions.
 Inference: A fresh image is processed using the ResNet50 model 
to extract its features, and the LSTM network then creates a 
caption based on these data. Word by word, the caption is 
created using samples from the probability distribution produced 
by the LSTM network for each word.

## Evaluation
I have modified the pre-existing BLEU matrix to evaluate my model, in 
which instead of using the corresponding captions for the image in the 
dataset, I am captioning the image myself (human_caption) and then 
comparing the model generated captions and my caption
Steps for evaluation:
1- Generate a caption for any image from the dataset, using the 
model
2- Look at the image and caption it yourself
3- Repeat the process for 10 images, and store the model generated 
caption in generated_captions list, and your thought off captions 
in human_captions list.
4- Find the BLEU score for each element in these lists, indivisually
5- Take the average of all the BLEU scores

## Why the 2 scores differ so much?
The reason for the significant difference in the BLEU scores obtained 
from the two approaches is due to the different ways in which they 
calculate the score.
 The 2nd approach uses the corpus_bleu function from NLTK, 
which calculates the BLEU score for the entire corpus of 
generated captions. This method uses a weighted average of the 
individual n-gram precisions to calculate the overall score.
 On the other hand, the 1st approach calculates the BLEU score for 
each generated caption individually, by comparing it to its 
corresponding reference caption. The individual BLEU scores are 
then averaged to get the final score. This method does not use 
any weighting factors and treats each generated caption 
independently.
