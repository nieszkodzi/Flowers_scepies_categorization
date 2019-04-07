# Categorization of 10 species of flowers.

0 - Geranium <br/>
1 - Rose<br/>
2 - English marigold<br/>
3 - Viola<br/>
4 - Daisy<br/>
5 - Trillium<br/>
6 - Iris<br/>
7 - Dandelion<br/>
8 - Dahlia<br/>
9 - Tiger lily<br/>

### LeNet - basic CNN 
LeNet-5, a pioneering 7-level convolutional network by LeCun (1998), that classifies digits, was applied by several banks to recognise hand-written numbers on checks (cheques) digitized in 32x32 pixel greyscale inputimages.


A simple model with LeNet architecture with no optymalization:

Model: "sequential_1"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_1 (Conv2D)            (None, 92, 92, 6)         456       
_________________________________________________________________
max_pooling2d_1 (MaxPooling2 (None, 46, 46, 6)         0         
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 42, 42, 16)        2416      
_________________________________________________________________
max_pooling2d_2 (MaxPooling2 (None, 21, 21, 16)        0         
_________________________________________________________________
flatten_1 (Flatten)          (None, 7056)              0         
_________________________________________________________________
dense_1 (Dense)              (None, 120)               846840    
_________________________________________________________________
dense_2 (Dense)              (None, 84)                10164     
_________________________________________________________________
dense_3 (Dense)              (None, 10)                850       
=================================================================
Total params: 860,726
Trainable params: 860,726
Non-trainable params: 0
________________________________

Loss and accuracy on validation set:
[0.7582451105117798, 0.8666666587193806]

Loss and accuracy on test set:
[5.569315592447917, 0.3000000029802322]

Confusion Matrix
   0  1  2  3  4  5  6  7  8  9
0  1  1  0  0  0  0  0  0  1  0
1  0  0  0  0  0  0  2  0  1  0
2  0  0  3  0  0  0  0  0  0  0
3  0  0  0  1  0  0  2  0  0  0
4  0  0  0  1  2  0  0  0  0  0
5  0  0  0  1  0  0  0  0  0  2
6  0  0  0  2  0  0  1  0  0  0
7  0  0  0  2  0  0  0  1  0  0
8  2  0  0  0  0  0  1  0  0  0
9  0  1  2  0  0  0  0  0  0  0

Classification Report
                  precision    recall  f1-score   support

        Geranium       0.33      0.33      0.33         3
            Rose       0.00      0.00      0.00         3
English merigold       0.60      1.00      0.75         3
           Viola       0.14      0.33      0.20         3
           Daisy       1.00      0.67      0.80         3
        Trillium       0.00      0.00      0.00         3
            Iris       0.17      0.33      0.22         3
       Dandelion       1.00      0.33      0.50         3
          Dahlia       0.00      0.00      0.00         3
      Tiger Lily       0.00      0.00      0.00         3

       micro avg       0.30      0.30      0.30        30
       macro avg       0.32      0.30      0.28        30
    weighted avg       0.32      0.30      0.28        30
    
   
   I generated training and validation set again, but this time I added data augmentation. Keras ImageDataGenerator class allows us to change our data set in many ways, for example:
* random rotation 
* zoom
* horizontal and vertical flip
* rescale
* width and heigth shift
* brightness
* shear
* fill points outside the boundaries of the input

Model structure doesn’t changed.

Loss and accuracy on validation set:

[0.5392090400060018, 0.8666666746139526]

Loss and accuracy on test set:

[3.2363916714986165, 0.40000000298023225]

Confusion Matrix
   0  1  2  3  4  5  6  7  8  9
0  2  0  0  0  0  0  1  0  0  0
1  0  0  0  0  0  0  2  0  1  0
2  0  0  3  0  0  0  0  0  0  0
3  1  0  0  2  0  0  0  0  0  0
4  0  0  0  0  3  0  0  0  0  0
5  0  0  0  3  0  0  0  0  0  0
6  0  0  0  2  0  0  1  0  0  0
7  0  0  0  2  0  0  0  1  0  0
8  1  0  0  0  0  0  1  0  0  1
9  0  1  2  0  0  0  0  0  0  0

Classification Report
                  precision    recall  f1-score   support

        Geranium       0.50      0.67      0.57         3
            Rose       0.00      0.00      0.00         3
English merigold       0.60      1.00      0.75         3
           Viola       0.22      0.67      0.33         3
           Daisy       1.00      1.00      1.00         3
        Trillium       0.00      0.00      0.00         3
            Iris       0.20      0.33      0.25         3
       Dandelion       1.00      0.33      0.50         3
          Dahlia       0.00      0.00      0.00         3
      Tiger Lily       0.00      0.00      0.00         3

       micro avg       0.40      0.40      0.40        30
       macro avg       0.35      0.40      0.34        30
    weighted avg       0.35      0.40      0.34        30
    
    
Model 11:
* optimizer - Nadam
* learning rate - 0.001
* kernel initializer - random uniform
* dropout - 0.2
* batch size - 64
* epochs – 200
Loss and accuracy on validation set:
[0.2186492343743642, 0.9666666547457378]

Loss and accuracy on validation set:
[4.798649152119954, 0.3333333363135656]

Confusion Matrix
   0  1  2  3  4  5  6  7  8  9
0  1  0  0  0  0  0  1  0  1  0
1  0  1  0  0  0  0  2  0  0  0
2  0  0  3  0  0  0  0  0  0  0
3  0  0  0  1  0  0  2  0  0  0
4  0  0  0  2  1  0  0  0  0  0
5  0  0  0  2  0  1  0  0  0  0
6  0  0  0  2  0  0  1  0  0  0
7  0  1  0  1  0  1  0  0  0  0
8  0  0  0  0  0  0  1  0  1  1
9  0  1  2  0  0  0  0  0  0  0


Model 10:
* optimizer - Nadam
* learning rate - 0.001
* kernel initializer - randm uniform
* dropout - 0.01
* batch size - 16
* epochs – 300
Loss and accuracy on validation set:
[0.4692219098409017, 0.900000003973643]

Loss and accuracy on validation set:
[3.958401330312093, 0.4333333392937978]
Confusion Matrix
   0  1  2  3  4  5  6  7  8  9
0  1  0  0  0  0  0  0  0  2  0
1  0  0  0  0  0  0  3  0  0  0
2  0  0  3  0  0  0  0  0  0  0
3  0  0  0  2  0  0  1  0  0  0
4  0  0  0  0  3  0  0  0  0  0
5  0  0  0  1  0  2  0  0  0  0
6  0  0  0  2  0  0  1  0  0  0
7  0  0  0  0  0  2  0  1  0  0
8  1  1  0  0  0  0  1  0  0  0
9  0  0  3  0  0  0  0  0  0  0

### Transfer learning- VGG16
The architecture of VGG16: the input layer takes an image in the size of (224 x 224 x 3), and the output layer is a softmax prediction on 1000 classes. From the input layer to the last max pooling layer (labeled by 7 x 7 x 512) is regarded as the feature extraction part of the model, while the rest of the network is regarded as the classification part of the model.

Loss and accuracy on validation set:
[1.0710324843724568, 0.799999992052714]
Loss and accuracy on validation set:
[4.070439561208089, 0.36666666766007744]
Confusion Matrix
   0  1  2  3  4  5  6  7  8  9
0  0  0  0  0  0  0  0  0  3  0
1  0  2  0  0  0  0  0  0  1  0
2  0  0  3  0  0  0  0  0  0  0
3  0  0  0  1  1  0  0  1  0  0
4  2  0  0  0  1  0  0  0  0  0
5  1  0  0  1  0  1  0  0  0  0
6  0  0  0  2  0  0  0  0  1  0
7  0  0  1  0  1  0  0  0  1  0
8  0  0  0  1  0  0  0  0  2  0
9  0  0  2  0  0  0  0  0  0  1

Classification Report
                  precision    recall  f1-score   support

        Geranium       0.00      0.00      0.00         3
            Rose       1.00      0.67      0.80         3
English merigold       0.50      1.00      0.67         3
           Viola       0.20      0.33      0.25         3
           Daisy       0.33      0.33      0.33         3
        Trillium       1.00      0.33      0.50         3
            Iris       0.00      0.00      0.00         3
       Dandelion       0.00      0.00      0.00         3
          Dahlia       0.25      0.67      0.36         3
      Tiger Lily       1.00      0.33      0.50         3

       micro avg       0.37      0.37      0.37        30
       macro avg       0.43      0.37      0.34        30
    weighted avg       0.43      0.37      0.34        30
