# Emotion Analysis in Call Center Conversation Audio Data

**Overview:**

This repository contains code and resources for a project focused on improving customer service quality and agent performance in call centers through emotion analysis. The primary objective is to detect and understand the underlying emotions of both customers and call center agents using deep neural networks.

![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/Overview.png?raw=true)

**Project Description:**

**Data Preprocessing:**
- **Audio Denoising:** The project begins with audio denoising to improve the quality of the audio data. An autoencoder is employed for this purpose.
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/Autoencoder.png?raw=true)
- **Speaker Diarization:** Speaker diarization involves a sequential process of segmentation, feature extraction, and spectral clustering to distinguish between different speakers in the conversation.
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/SPD.png?raw=true)
- - **Segmentation Process:**

  - **Voice Activity Detection (VAD):** VAD is a critical component of the segmentation process. It involves detecting periods of speech (voice activity) in the audio and distinguishing them from non-speech segments. In this project, we utilize Google's webrtcvad library for VAD detection.

  - **Features:** Perceptual Linear Predictive (PLP) coefficients are used as the primary features for VAD. These coefficients are derived from the audio signal and are particularly well-suited for capturing human speech characteristics.

  - **Segmentation Criteria:** The segmentation process begins whenever there is a pause or silence in the audio. VAD is employed to identify these pauses, helping to define the boundaries between distinct audio segments.
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/Segmentation_audio.png?raw=true)

- - **Feature Extraction:**
  - After segmenting the audio files, feature extraction is performed on the segmented chunks.
  - Acoustic features such as MFCCs, their first-order derivatives, and second-order derivatives are used as features.
  - The dimension of the feature vector for each frame is xi ∈ R^39×1.
    ![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/FEAT.png?raw=true)

    **Universal Background Model (UBM):**

  - To convert MFCCs into a super vector, a Universal Background Model (UBM) is employed.
  - The UBM is a Gaussian Mixture Model (GMM) trained on extensive audio data. It is speaker-independent and represents features that are not dependent on the speaker.
  - The UBM is trained using the Expectation Maximization (EM) algorithm.
  - Each chunk uses 16 Gaussian mixtures. The UBM includes a weight vector π ∈ R^16×1, means matrix µ ∈ R^16×39, and covariance matrices Σ ∈ R^39×39 for each mixture component.
  ![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/GMMRep.png?raw=true)


    **Adaptation from Universal Background Model (UBM):**

  - Given the UBM, it is adapted to each audio chunk. This adaptation is typically done using a Gaussian Mixture Model (GMM) that models the distribution of the         audio chunk's MFCC features.
  - The GMM adaptation is performed using Maximum a Posteriori (MAP) adaptation by adjusting the means of the UBM's Gaussian components.
  - The means from the UBM serve as initial values for the means of individual GMMs (chunks) and are updated at every iteration using the EM algorithm.
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/UBM_for_audio.png?raw=true)
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/GMM_for_chunk.png?raw=true)

- - **Spectral Clustering**
  - Spectral clustering is employed in the project.
  - Unlike traditional clustering methods that operate directly on the data space, spectral clustering leverages the spectral properties of an affinity matrix           computed from the data.
  - Spectral clustering is particularly useful for clustering data that doesn't exhibit well-defined geometric shapes in the input space.
  
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/Spectral_Clustering.png?raw=true)


**Emotion Classification:**
- Traditional machine learning algorithms like Support Vector Machines (SVM), Gaussian Mixture Models (GMM), and Hidden Markov Models (HMM) are commonly used for emotion classification. However, this project takes a deep learning approach to enhance classification accuracy and robustness.
- The deep neural network model is trained to classify emotions such as happiness, anger, sadness, frustration, and more from the spoken content of call center conversations.

**Datasets:**
- The project utilizes two datasets: Interactive Emotional Dyadic Motion Capture (IEMOCAP) and CallHome, which provide diverse and real-world conversation data for analysis.

**Results:**
- Audio denoising using an autoencoder results in an average Signal to Noise Ratio (SNR) of 6.69 dB, with a maximum SNR of 9 dB and a minimum SNR of 4.73 dB.
- Speaker diarization achieves an accuracy of 76.2% through manual annotation.
![Overview](https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/blob/main/Images/Accuracy%20table.png?raw=true)
- The deep neural network model aims to further improve emotion classification accuracy.

**Listen to Speaker Diarization results:**

https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/assets/130117726/d50b2df6-15a7-455c-befe-f383ea8af573

https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/assets/130117726/31ab46fd-a02b-406b-b91e-c02251cf6abd

https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/assets/130117726/ad8ae450-bec9-409f-a22c-de9d3772ee71

https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/assets/130117726/ce45021a-f45a-4d79-889a-b7aac4dbf26a

https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/assets/130117726/14e03663-5106-49bc-a3bf-db04b40f1f43

https://github.com/Basheer22EE65R19/Emotion_Analysis_of_Call_Center_Conversation_Audio_data/assets/130117726/43f4def9-95e2-420b-8662-b5e4e60cf308

**Potential Applications:**
- This research holds significant potential in various applications, including:
  - Call center performance enhancement.
  - Customer satisfaction evaluation.
  - Agent training and feedback.
- Emotion analysis can enable call centers to promptly identify and address customer issues, leading to an improved customer experience and increased customer loyalty
- The method used for Speaker Diarization can also be used for speaker recognition which includes speaker enrollment and verification


