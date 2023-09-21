Emotion Analysis in Call Center Conversations

Overview:

This repository contains code and resources for a project focused on improving customer service quality and agent performance in call centers through emotion analysis. The primary objective is to detect and understand the underlying emotions of both customers and call center agents using deep neural networks.

Project Description:

Data Preprocessing:
- Audio denoising: The project begins with audio denoising to improve the quality of the audio data. An autoencoder is employed for this purpose.
- Speaker diarization: Speaker diarization involves a sequential process of segmentation, feature extraction, and spectral clustering to distinguish between different speakers in the conversation.

Emotion Classification:
- Traditional machine learning algorithms like Support Vector Machines (SVM), Gaussian Mixture Models (GMM), and Hidden Markov Models (HMM) are commonly used for emotion classification. However, this project takes a deep learning approach to enhance classification accuracy and robustness.
- The deep neural network model is trained to classify emotions such as happiness, anger, sadness, frustration, and more from the spoken content of call center conversations.

Datasets:
- The project utilizes two datasets: Interactive Emotional Dyadic Motion Capture (IEMOCAP) and CallHome, which provide diverse and real-world conversation data for analysis.

Results:
- Audio denoising using an autoencoder results in an average Signal to Noise Ratio (SNR) of 6.69 dB, with a maximum SNR of 9 dB and a minimum SNR of 4.73 dB.
- Speaker diarization achieves an accuracy of 76.2% through manual annotation.
- The deep neural network model aims to further improve emotion classification accuracy.

Potential Applications:
- This research holds significant potential in various applications, including:
  - Call center performance enhancement.
  - Customer satisfaction evaluation.
  - Agent training and feedback.
- Emotion analysis can enable call centers to promptly identify and address customer issues, leading to an improved customer experience and increased customer loyalty.
