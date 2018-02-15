# Deep learning to identify the brain MRI contrast
## Background
We developed a deep learning (DL) algorithm with neutral networks to automatically infer the contrast of a MRI scan based on image intensity of multiple sagittal slices.  The DL algorithm consisted of an initial convolutional neural network (CNN), which inferred the contrast on a single slice of the MRI, and a subsequent dense neural network (DNN), which relied on the CNN output to infer a contrast for the entire MRI volume.  

We made the implementation openly available here on GitHub, and developed the algorithm in [Python](https://www.python.org) with a [Theano](http://deeplearning.net/software/theano/) backend and compiled on [Keras](https://keras.io).  Keras is a high-level software package that provides extensive flexibility to easily design and implement DL algorithms.  We emperically selected all the parameters that defined the network architecture, including the number and type of layers, the number of layer nodes, and C, the number of final possible contrasts.  

## Implementation
We developed two sequential neural networks to identify the brain MRI contrast.  The first network was a convolutional neural network that inferred the modality on a sagittal slice.  The second network combined the result generated by the first nerwork to infer the modality on the entire volume.

We have uploaded Python scripts that can be used to reproduce our results.  Unfortunately the data cannot be released for the public but we expect our results to be reproducible.  The Python scripts can be used to (1) define the neural network (NN) acrhitecture, (2) train the NN, and (3) test the NN.

### Define the neural network
The [modality.save_NNarch_toJson.py](https://github.com/ricardopizarro/MRI-contrast/blob/master/src/modality.save_NNarch_toJson.py) script was used to define the architectures of the two networks and save them as .json string files to later be loaded during the training and testing phase.  The architecture can be modified to meet different requirements including data size, number of classes (MRI contrast) to model, and architecture parameters.  
```
$ python modality.save_NNarch_toJson.py
```
Upon execution this script saves .json files that specify the neural network acrhitecture.

