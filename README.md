# ImageCaptioningModel
# Image Caption Generator

## Problem Definition

<b>Problem:</b> Visually impaired individuals face challenges in accessing and understanding visual content like images.

<b>Objective:</b> To develop an image captioning system that can automatically generate accurate and meaningful captions for images to aid visually impaired individuals in understanding the content by recognizing objects, and generate coherent and accurate textual descriptions.

## Dataset

The Flickr 8K dataset is a collection of 8,000 images that are each paired with five different textual descriptions, for a total of 40,000 captions. The images were chosen from six different Flickr groups, and tend not to contain any well-known people or locations, but were manually selected to depict a variety of scenes and situations.

## Data Analysis

Following are a few observations from the Flickr 8k dataset:

<b>Caption Analysis:</b> 
<ol>
  <li>Unique words vocabulary: 9630.</li>
  <li>Average caption length: 10-12 words.</li>
  <li>Mean caption length: 11.78.</li>
  <li>Standard deviation of caption length: 3.8.</li>
  <li>Maximum caption length: 38.</li>
  <li>The most common words in the captions include "man", "woman", "girl", "water", "black", "white", "boy", and "front". Figure 1 shows the wordcloud of the Flicker8K corpus.</li>
</ol>

<b>Image Analysis:</b>
<ol>
  <li>The dataset contains a collection of 8000 images.</li>
  <li>The images in the Flickr 8k dataset cover a wide range of topics and subjects, including landscapes, people, animals, buildings, and more.</li>
  <li>The images in the dataset are of different sizes, with the average image size being around 400x300 pixels.</li>
</ol>

## Experimental Setup

<b>Model Architectures:</b> We experimented with five different models for image captioning:
<ol>
  <li>VGG (architecture) with RNN (Recurrent Neural Network)</li>
  <li>VGG with LSTM (Long Short-Term Memory)</li>
  <li>Inception (architecture) with LSTM</li>
  <li>Inception (architecture) with 2 LSTM layers</li>
  <li>Inception with LSTM and GRU (Gated Recurrent Unit)</li>
</ol>

### Image Processing

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594947-9adafd8b-86c0-49b5-8578-41a9a37828a2.png">

### Caption Processing

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594970-7a68900d-b88b-438c-867b-a1ea3bafc476.png">

### Model Creation

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594986-42eb5904-435a-486a-a446-37f1dee6c371.png">

### Baseline and Final Model Architecture Comparision

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594752-1c947d42-4e33-47e3-ad13-d198b5ac3d97.png">

<b>Model Training:</b> The models were trained for 10 epochs, with a batch size of 32. We used the Adam optimizer with a learning rate of 0.001 and a categorical cross-entropy loss function to optimize the models.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594633-a71739b7-a783-4857-9260-b238aac76cc1.png">

The two graphs represent comparison of two models' training and validation loss curves during the training process. As training progresses for the final model, the training loss decreases at a faster rate than the validation loss, resulting in an increasing gap between the two curves, which may suggest overfitting. The baseline model shows the training loss initially being higher than the validation loss until the 2nd epoch. After the 2nd epoch, the training loss continues to decrease, while the validation loss remains almost constant, indicating a possible learning plateau for the validation dataset.

<b>Evaluation Metric:</b> We evaluated the quality of generated captions using the BLEU (Bilingual Evaluation Understudy) score. The BLEU score compares generated text to one or more reference texts and provides a score between 0 and 1, with a higher score indicating better alignment with the reference text(s). BLEU scores were calculated for n-grams of length 1 to 4 (BLEU-1, BLEU-2, BLEU-3, and BLEU-4).

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594613-d4bed066-8409-403f-b725-1cdf892a09a4.png">

Our results show that the Inception architecture with LSTM and GRU layers achieved the best performance in terms of BLEU scores of <b>0.48</b>.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/33513926/236594578-ca7a23fc-5075-4675-89e7-dcf475365dce.png">

## Error Analysis

Error analysis to examine the differences between the models and their impact on the generated captions:
<ol>
  <li>Inception's efficient handling of images by capturing both local and global features, whereas VGG focuses on depth with small kernels.</li>
  <li>The combination of LSTM and GRU layers in capturing complex relationships between image features and generated captions, compared to RNNs, which suffer from the vanishing gradient problem.</li>
  <li>The higher complexity of the Inception-LSTM-GRU model, allowing it to capture intricate patterns, while being mindful of potential overfitting and the need for regularization.</li>  
</ol>

## Future Scope

<ol>
  <li>Enhanced Accuracy: Continued advancements in deep learning techniques, such as transformer-based models like GPT-3, will likely lead to increased accuracy and descriptiveness in generated captions.</li>
  <li>Multimodal Approaches: Exploring multimodal approaches that combine image features with other modalities such as text, audio, or user interactions can lead to more comprehensive and context-aware captions.</li>
  <li>Attention Mechanisms: Investigating advanced attention mechanisms, such as self-attention or transformer-based attention, can enhance the model's ability to focus on relevant image regions and generate more precise and detailed captions.</li>
</ol>

## Conclusion

In conclusion, the Inception v3 architecture-based LSTM and GRU layers-based image captioning system displayed superior performance, achieving higher BLEU scores in comparison to other models. Improved accuracy was made possible by capturing complicated correlations between image features and captions. Future improvements in Inception v3's fine-tuning and research into multimodal methods have the potential to substantially improve the precision and descriptiveness of picture captioning systems.
