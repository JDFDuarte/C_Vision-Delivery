
# OCRithmetic 
## Optical Character Recognition Calculator and Translator



What is OCR? 
It stands for **O**ptical **C**haracter **R**ecognition and involves the processing and analysis of visual data, generally images containing text.
The key tasks involve>
- preprocessing the images using techniques like noise reduction, binarization, and skew correction to enhance the image quality.
- Text detection by identifying regions in the image that contain text.
- Feature extraction by analysing the visual characteristics of characters and words to distinguish them from the background and from each other.

The goal of OCR is to transform text into a machine-readable format, which then allow the users to search or edit, but also allow the machine to further use this data.
It can also impact greatly efficiency and productivity since it automates data entry and document processing when compared to manual methods
Besides these applications, and among other benefits of OCR, it can also the need for physical storage space and allows for the preservation of historical documents, since these can then be accessed without manual contact even when the documents can no longer be handled safely. 

Wanting to explore the capabilities of OCR, we set ourselves to build a calculator and a translator, to leverage both digits and letters.

- **Why build an OCR calculator:**
It allows users to seamlessly convert handwritten or printed mathematical expressions into digital, computable formats. It can serve as a powerful educational aid, helping students check their work and practice problem-solving in a more interactive way. 

- **Why build an OCR translator:**  
There are many benefits that come from the conversion of handwritten text into digital, machine-readable formats. 
Digitized text from handwritten documents becomes searchable, making it easier to find specific information and translating it for ease of use. 
This can help users share their notes with others, regardless of language fluency.

So, to leverage both digit and letter identification, we built Convolutional Neural Networks from scratch that were able to correctly identify digits and letters (save for specific exceptions where the similarity of the characters is too high, depending on handwriting style).

But we also analyzed pre-existing solutions available to compare our CNN results. There are multiple solutions available, each with its strengths in different tasks. 
These were used so that we can familiarize ourselves with a diversified number of architectures available for the task of OCR, since the different solutions explored use different approaches.

These consist of:

- **Tesseract**
    - open source engine created by HP in the 80’s and maintained by Google¹  that uses Long Short-Term Memory (LSTM) neural networks in its latest versions for improved accuracy. 
It was used via PyTesseract is a Python wrapper that facilitates working with Tesseract within Python environments.


- **EasyOCR**
    - is a package for OCR tasks taht uses a Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN) hybrid architecture.
      - For feature extraction it relies on deep learning models like ResNet and VGG.  
      - For sequence labeling, it uses LSTM networks for interpretation of the extracted features’ sequence. 
      - Decoding and transcription of the labeled sequences to the recognized text is done using the Connectionist Temporal Classification (CTC) algorithm. ²

- **PaddleOCR**
    - toolkit that makes use of deep learning models to achieve fast and accurate results. It uses DBNet for text detection, CRNN (Convolutional Recurrent Neural Network) with Attention for text recognition in the identified regions.³

- **TrOCR**´
    - This model does not use CNN. It consists of two main components: **a pre-trained image Transformer as encoder and a pre-trained text Transformer as decoder**

        The input image is resized, then split into 16x16 pixel patches. These patches are fed into the image transformer encoder and the encoder is normally initialized with a pre-trained vision transformer (BEiT).
        The output of the encoder is passed to the text Transformer decoder which is typically initialized with a pre-trained language model like RoBERTa. The decoder generates wordpiece-level text based on the visual features that the encoder extracted. ⁴





A Streamlit app was built for visualization of the large version of Stage1 TrOCR and its demo added to the [presentation](./presentation.pdf). 

In the app, it is possible to input the mathematical expression by uploading an image, drawing an expression or using the device's camera to take a picture to an expression. 

After providing the input, it is possible to pass it to the model and obtain the result f the expression extracted. 

Additionally, a "Report Error" functionality was added so that the user can provide correction in case of incorrect prediction. This data is saved to a database. 

Due to limitations from Streamlit, the app is not deployed.  
|  
|  
|  
  




¹ Smith, R. (2007). An overview of the Tesseract OCR engine. Ninth International Conference on Document Analysis and Recognition (ICDAR 2007), 2, 629-633. https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/33418.pdf

² https://medium.com/@adityamahajan.work/easyocr-a-comprehensive-guide-5ff1cb850168

³ Jiang, Y., Lyu, Z., & Zeng, Y. (2021). PaddleOCR: Architecture. In DESOSA 2021. https://2021.desosa.nl/projects/paddleocr/posts/paddleocr-e2/


⁴ Li, Minghao & Lv, Tengchao & Cui, Lei & Lu, Yijuan & Florencio, Dinei & Zhang, Cha & Li, Zhoujun & Wei, Furu. (2021). TrOCR: Transformer-based Optical Character Recognition with Pre-trained Models. 10.48550/arXiv.2109.10282. 

