# Exclusive Reproduction! From FFT Frequency Domain Features to Fully Connected Graph Classification: A Rolling Bear Fault Diagnosis Model Based on the GCN of Graph Convolutional Neural Networks

Preface\tIn the research of rolling bearing fault diagnosis, most traditional deep learning methods directly input one-dimensional vibration signals into CNN, LSTM or Transformer models for classification. Although these methods are simple to implement, they often only focus on the local waveform changes or sequential dependencies of signals, lacking in the mining of the correlation structure between samples. The reproducibility in this period is a fault diagnosis method with more characteristics of graph learning: Graph Convolutional Neural Network (GCN)-based rolling bearing fault diagnosis model. This method does not simply feed each signal as an independent sample into the network, but first converts the raw vibration signals into frequency domain features, then organizes multiple frequency domain samples into a graph structure. Through GCN, it mines the correlation relationships between sample nodes, ultimately accomplishing fault category recognition. (Effective, can be studied for reference!) )
1. Model Introduction
\tx = [x1, x2, ..., x1024]  
After FFT, a 1024-dimensional frequency domain magnitude spectrum is obtained as the input feature for the graph nodes.
1.2 Graph node construction
Node Feature = FFT Spectral Vector
Node label = Failure category label
In other words, the model does not directly input a single signal into the classifier; instead, it organizes multiple frequency domain samples into a graph structure, allowing the GCN to perform feature propagation within the graph.
\t1.3 \tConstruction of Fully Connected Graphs\tThe method used in the paper adopts a fully connected graph structure. Each graph contains multiple nodes, with each node connected to every other node in pairs. The purpose of this is to allow nodes in the same graph to fully exchange feature information, allowing the model to learn association patterns between samples. The graph structure can be represented as: Node 1 ↔ Node 2, Node 1 ↔ Node 3, ..., Node i ↔ Node j. The edge weights are defaulted to 0-1 weights, meaning that if there is a connection, the weight of the edge will be 1.
\t1.4 \tGCN Classification Model\tThe model employs two layers of graph convolutional layers for feature extraction, followed by two layers of fully connected layers for classification. The parameters are as follows:
2. Bearing Data Loading and Preprocessing
2.1 Import Data
Referencing the previous article, preprocess the fault classification 10 for the dataset of bearings from Case Western Reserve University:
Supports reading common CSV format data:
\tEach line = 1024 sample points + 1 label
\tSuitable for well-organized CWRU ten-category data, can also be extended to other bearing fault datasets.
2.2 Data Preprocessing
The main steps are as follows:
(1) Use non-overlapping sampling to divide the original vibration signal into multiple segments of 1024 subsamples;
(2) Utilize the Fast Fourier Transform to convert the subsample vibration signal into a frequency domain signal; (3) Use the subsample frequency domain signal as nodes, the spectrum as node features, and the fault type as node labels. Then, construct a fully connected graph with 10 nodes, where each pair of nodes has an undirected edge with a weight of 0-1; (4) After randomly shuffling the constructed fully connected graph dataset, divide it into a training set and a test set in a ratio of 6:4.
(5) Construct a GCN model, extracting node features through two graph convolutional layers and classifying features through two fully connected layers.
(6)Train the GCN model using the training set, and use the error backpropagation algorithm to adjust the learnable parameters of the GCN model;
 (7)After training is completed, input the test set into the final GCN and output the diagnostic results.
3. FFT-GCN Fault Diagnosis Model
3.1 Define the network model, set parameters, and train the model
50 epochs, accuracy 100%, the FFT-GCN network classification effect is significant, it can extract important features from fault signal characteristics for model recognition, the effect is obvious!
3.2 Model evaluation
 (1)Accuracy, Precision, Recall, F1 Score
 (2)Fault 10 classification confusion matrix:
 (3)Classification label visualization
 (4)Model training after t-SNE feature visualization:
Click to download: complete original data, Python code
END
2. Friends who like this can click to follow, give the article a "like", share on WeChat groups or discuss in groups
Previously excellent content
Rapid publication papers | Based on 2D-SWinTransformer+1D-CNN-SENet parallel fault diagnosis model
Bearing life prediction major update! Added CNN-BiGRU-Attention model collection + rich visualization charts
Multimodal - Fault Diagnosis | Large kernel convolution opens a new era of visuals!
Strong! Direct write in one zone! Based on SSA+Informer-SENet fault diagnosis model
Multisource information fusion: Data layer fusion + feature layer fusion fault diagnosis model!

## Images

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
