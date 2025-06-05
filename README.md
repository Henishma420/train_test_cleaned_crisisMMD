# train_test_cleaned_crisisMMD
Preprocessing of the CrisisMMD Dataset for Multi-Modal Classification The CrisisMMD dataset, a well-established benchmark for crisis-related multi-modal classification tasks, comprises both text and image data collected from social media (primarily Twitter) during real-world disasters. 

The primary objective of this dataset is to enable the development of AI models that can classify social media content as informative or non-informative, and further categorize informative content into specific disaster-related classes.

Dataset Overview For this project, I have meticulously cleaned and preprocessed the dataset to make it suitable for training multi-modal machine learning models. The processed dataset consists of a total of 18,082 tweets, each uniquely identified by a tweet_id. Each tweet is associated with both textual and visual data.

🔤 Text Preprocessing Each tweet’s text was preprocessed using standard Natural Language Processing (NLP) techniques. I used a transformer-based tokenizer (such as BERT) to tokenize the text. For every tweet, the following features were extracted:

Input IDs: Tokenized representation of the tweet, suitable for transformer models.

Attention Masks: Binary mask indicating actual tokens vs. padding.

Label Text (label_text): Binary label — 1 if the tweet is informative, 0 if non-informative.

🖼️ Image Preprocessing Each tweet's associated image was processed using a pre-trained ResNet model to extract high-level visual features. These were flattened into 2048-dimensional feature vectors, spanning columns image_feature_0 to image_feature_2047.

Additionally, each image was annotated with a binary label (label_image), indicating whether the image content is informative (1) or non-informative (0).

🌍 Disaster Type Labeling Informative tweets are further annotated with a fine-grained disaster category ranging from 0 to 6:

{'california_wildfires': 0, 'hurricane_harvey': 1, 'hurricane_irma': 2, 'hurricane_maria': 3, 'iraq_iran_earthquake': 4, 'mexico_earthquake': 5, 'srilanka_floods': 6} This supports more detailed classification tasks beyond binary relevance.

🧪 Dataset Splitting and Saving The fully preprocessed dataset has been split into training and testing sets using an 80-20 split:

Training Set: 14,465 samples

Testing Set: 3,617 samples

Total: 18,082 samples

Both the training and testing datasets, including textual and visual features, have been saved as .pt files, making them directly usable in PyTorch-based deep learning workflows.

📊 Final Dataset Schema Column Name Description tweet_id Unique tweet ID (0 to 18,081) text Raw tweet text input_ids Token IDs from BERT tokenizer attention_mask Binary attention mask for padding label_text Informative (1) or Non-informative (0) for text disaster_label Disaster type label (0 to 6) image_feature0-2047 ResNet-extracted image features (2048-dimensional vector) label_image Informative (1) or Non-informative (0) for image

The link to the dataset: https://huggingface.co/datasets/Henishma/train_test_cleaned_crisisMMD
