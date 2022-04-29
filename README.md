# Your Very Own Book Reading Assistant/Companion! 
*~ with realistic voice*



# Technical specifications 

### OVERVIEW


This repository resides a virtual assistant/companion and eBook reading app. The purpose of this App is to provide a user with an audio enabled user-interface with an integrated eBook reading functionality. The App itself is integrated with a virtual assistant that can interact with the user. Whether the user would want to change the voice pattern of the reader, pause, play, skip or change the book that the app is reading. The internal design of the virtual assistant will consist of a voice recognition model and a cutting-edge text to voice algorithm.

### TECHNOLOGIES USED

  

-   Speech recognition libraries: SpeechRecognition 3.8.1
-   Natural Language ToolKit: NLTK 3.6.2
-   Text to Speech for testing and development: pyttsx3
-   PDF export and transformation: PyPDF2
-   Text to Speech for Final release: Tacotron
-   Text to Speech Supporting model: MultiBand - MelGAN
-   Model Training manager and optimizer: Double Decoder Consistency (DDC)
-   Machine-learning python platforms: Tensorflow / PyTorch
-   Google Collab Pro Virtual Machines / Google Drive Cloud Storage

### Architechtural overview

There exist two main components within the system. The first component is the
voice-activated assistant and the second part is the deep learning text to voice (TTS)
algorithm.

![Main Diagram](https://github.com/ThomazWild/Book-Reading-Companion/blob/main/Main%20Diagram.png)



### Block Diagram

  ![Block Diagram](https://github.com/ThomazWild/Book-Reading-Companion/blob/main/BLOCK%20DIAGRAM.png)

Block Diagram showing more details on the architecture

### Design / Logical viewpoint

  

The below diagram contains all the design architecture and the logic of how the system works. It shows 2 main components: User Interface and the Internal systems. How they interact and trade information with each other. The Class diagram also contains information on all the attributes of each object within the system, functions,....

![Class Diagram](https://github.com/ThomazWild/Book-Reading-Companion/blob/main/classdiagram.png)

### Information viewpoint

  

The ER Diagram contains system design under information view point, what kind of information each of the entities within the system contains and what kind of relationship they have with each other in terms of information.

![ER Diagram](https://github.com/ThomazWild/Book-Reading-Companion/blob/main/ER.png)

### Interface viewpoint

  

Since this is an app dedicated to the blind and disabled people there won't be a visual user-interface. There only exists audio interface which the user interacts directly by using voice commands and listening to voice response from the virtual assistants. However, in order to provide best support for disabled people, there is a simple line to line user-interface which contains status and current interaction of the app which the user can see in case the assistant deviates from the user’s needs. For Blinded people, there can be a supporter who can look at the status screen occasionally and help them get used to the app in the future.

![Interface](https://github.com/ThomazWild/Book-Reading-Companion/blob/main/INTERFACE.png)

### Interaction Viewpoint

 
This is the interaction view point in forms of Sequence Diagram. It Shows the interaction of the app and how normal interaction between the user, assistant and its internal components is normally done and processed.

![Sequence Diagram](https://github.com/ThomazWild/Book-Reading-Companion/blob/main/Sequence%20Diagram.png)



### The Assistant

  

Virtual assistant features and logic of function defined as Python code where minimal libraries which are external are required. The assistant input is text as string values and from the string it can use the defined logical function to compare which branch of functioning it can use to reply. It can also interact with other components of the internal system such as the book library, the text to speech models, the speech recognition algorithm, the user information and the setting within itself, the setting in some cases and diagrams are plotted separately to view in higher details.

  

### The voice recognition

  

This component of the app converts the voice of the user into text which the assistant can use for logical functioning and reply to.

The library used for this application is the Python SpeechRecognition library. The SpeechRecognition library acts as a wrapper for several popular speech APIs and is very flexible. One of the used api is Google Web Speech API. The API coding itself is hard-coded into the SpeechRecognition library. And additionally, the SpeechRecognition python library can work either off or online giving it high versatility.

  

The flexibility of the SpeechRecognition python package made it an excellent choice for our purpose which is to create a virtual assistant.

  

### The Text to Speech Model (TTS)

  

The Implemented TTS model for this system includes 2 vocoders:

•  Tacotron
•  MultiBand-Melgan


Tacotron is a generator sub-linear model that allows the input of text to be
entered and then it generates (predict) the waveform (sound) which can be
generated from the texts.
In April 2017, Google published a paper: “Tacotron: Towards End-to-End Speech
Synthesis”, where they present a neural text-to-speech model that learns to
synthesize speech that is very close to the human voice for technology at that
time. However, they did not release their source code or training data. There have
been many successful and failed attempts to recreate and train this model from
other developers. Many models’ creator achieved success and decided to push it
to open-source which made it available to the public to research, develop and use.
Most of these Implementations are done on TensorFlow or PyTorch.
Tacotron in itself is a combination of two deep learning neural networks. One Is a
Deep learning model that predicts the Mel spectrogram frames from an input text
sequence which contains the spectrum of sounds frequencies and the other deep
learning model convert the spectrogram to the corresponding voice of the
speaker.



MultiBand-Melgan is an improved version of MelGAN. It offers much faster
waveform generation and of higher quality than its predecessor. These
improvements made the model more stable and have fewer artefacts within the
generated spectrum.

These 2 models are trained on the LJ Speech data set and saved to the servers.
Normally, even very advanced TTS models will suffer from slower inference time,
artefacts generated from untrained words, long input string, or the difficulty of the
language.
That is why these models will be trained based on Double Decoder Consistency
(DDC). It is used to mitigate these problems by acting on these observations to find a
suitable architecture middle ground.
Each time the system starts up. It will load all previous weights that are in the trained
deep learning models and put them into RAM. Every time the AI assistant speaks or
needed to read a book, it will call a certain commanding function. The system will then
put the input text into the models to get predictions of sounds and return the
generated sounds.

The data used for model training is the LJ speech data set. This speech data set is a
public domain resource consisting of 13,100 audio clips from a human speaker. Each
clip has its own transcription, and the length of each clip varies from 1 to 10
seconds. The total length of the entire audio data set is around 24 hours. This dataset was created from 2016 to 2017 by the LibriVox project.
Inside of the data file, there are two main components first is the audio data which is
in WAV format. The second part of the data set is the metadata which is stored in the
file transcripts.CSV.
In the audio data, every single audio file is on a mono channel with 16-bit at a sample
rate of 22,050Hz. And their information is contained in the metadata. The Metadata
file contains the ID of the corresponding WAV file, Transcription and Normalized
Transcription which are words spoken by the speaker


  

### TTS Models Storage

  

Within the system there also consists of a storage system for text-to-speech algorithms which contain many text-to-speech algorithms. Since originally this app was designed in mind to contain many text-to-speech algorithms which can have many accents, gender, nationality, etc… All of the models which are different have been trained and ready to use can be stored within this model storage. This model storage is stored on Google Drive and each of the models has its own folders and system of file.

  

### Book Library

  

The book libraries within the app at the current state contain only publicly available and public domain books which are available for use. The Book library is stored on the cloud network and cloud storage system on Google Drive. The library contains book names, number of pages and the contents of the book in pure text format.
