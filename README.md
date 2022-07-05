# OpenCV
Traffic Signs Recognition

RIRV Project assignment: Traffic sign analysis
The goal of the project task was the detection of traffic signs. This type of technology is used in newer types of cars and in
self-driving cars. It serves the driver or the computer in the car to know how to react in a certain way in traffic according to what is detected
traffic sign.
In this project, it was performed using a neural network. This means that the "knowledge" of this model will be acquired through a certain learning process. For that learning
we need a suitable dataset. For the purposes of this project, a German dataset with more than 50,000 images distributed in 44 classes is used.
Each class indicates a separate traffic sign. The dataset can be downloaded from the following link (https://sid.erda.dk/public/archives/daaeac0d7ce1152aea9b61d9f1e19370/published-archive.html)
The most important parts of the code, i.e. the layers for creating the model:

-> 2D convolution -> using the filter, we convert the image S(x,y) into the image S'(x,y) in such a way that for a certain pixel or the area around it (depending on the size of the kernel) we calculate
some new values. If, for example, the core size is 3x3, it means that we take into account the values of 9 pixels, which we add up and divide by
1/total number of core pixels, i.e. in this case 9 (1/9). It is used to smooth the image.

-> MaxPool2D -> compression layer used to reduce size, increase calculation speed. A certain core is taken from which the highest value is taken
and moves by a defined number of steps along each dimension (height and width)

-> Dropout -> a technique to prevent overloading of neural networks. It randomly selects neurons and their corresponding networks and disables them. This allows us to
that the network does not rely on individual neurons and thus forces all other neurons to learn to generalize better.

-> Flatten -> is used to make multidimensional input one dimensional which is usually used in transition ie sent from convolution layer to fully connected
layer (we turn the matrix into a vector).

-> Dense -> fully connected layer, such as all neurons in the previous layer are connected to all neurons in the next layer. It is used when there may be a connection between
any feature with any feature in the data point. It is often used after Flatten, i.e. at the end of the network. It connects all inputs of a layer to each of its own
neurons using a linear combination followed by an activation function (softmax).

Activation functions:
They define output from nodes based on inputs or sets of inputs

-> relu -> non-linear activation function that acts on multilayer neural networks, its main advantage is that it does not activate all neurons simultaneously.

-> softmax -> activation function mainly used to assign decimal values to each class in a multi-class problem i.e. produces certain probabilities
which picture belongs to

The rest of the code relates to precision calculations, graphs and the GUI used to run the project.
Conclusion:
The mentioned Dataset does not use all traffic signs for the purposes of the project. The model does not work perfectly because the ratio of the number of images of individual classes is not equal. He recognizes some signs better,
and some not. To show the functionality of the model, a trainset with images with a color depth of 24 bits (8 bits per RGB channel) was used, but if, for example, a screenshot is taken from the professor's video
then that image has a color depth of 32 bits (RGB + alpha channel) and the model will not work. For the model to function correctly, the image needs to be converted to a 24-bit color depth.
