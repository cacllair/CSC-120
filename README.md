# CSC-120

1. What is the Fashion MNIST dataset?

    Fashion MNIST is a collection of 70,000 grayscales images ($28 \times 28$ pixels) across 10 clothing categories, such as sneakers, shirts, and bags. It was designed by Zalando Research as a direct, more challenging drop-in replacement for the classic handwritten digits MNIST dataset. Because it shares the same format but features more complex visual patterns, it has become the standard benchmark for testing basic computer vision and deep learning algorithms.

2. Why do we normalize image pixel values before training?

     Normalizing pixel values typically scaling them from [0,255] to a range like [0,1]ensures mathematical stability and faster training. By centering the data, you prevent large input values from causing "exploding gradients" and ensure that the optimization algorithm (like Gradient Descent) converges on a solution more efficiently. Essentially, it puts all features on a level playing field so the model can focus on learning patterns rather than struggling with inconsistent numerical scales.

3. List the layers used in the neural network and their functions.

     1. The Input Layer - This is the entry point for your data. It holds the raw pixel values of the $28 \times 28$ grayscale image.
     2. Convolutional Layers (Conv2D) - These layers use "filters" (small scanning windows) to look for patterns like edges, corners, or textures. Early layers find simple lines, while deeper layers combine those           lines into complex shapes like sleeves or shoe soles.
     3. Pooling Layers (MaxPooling) - These layers act as a "summarizer." They reduce the size of the image data (downsampling) by keeping only the most important (maximum) values in a small area.
     4. Flatten Layer - This layer takes the 2D "map" of features created by the previous layers and unrolls it into one long, 1D list of numbers.
     5. Dense Layers (Fully Connected) - These layers act as the "brain" or the logic center. Every neuron here is connected to every neuron in the previous layer. It looks at all the extracted features (sleeves,           buttons, laces) and tries to figure out which clothing item they belong to.
     6. The Output Layer - This is a final Dense layer with exactly 10 neurons (one for each clothing category).

4. What does an epoch mean in model training?

     An epoch is one complete pass of the entire training dataset through the neural network. During this cycle, the model examines every individual image once, makes predictions, and updates its internal weights based on the errors it made. Because learning complex patterns usually requires repetition, models are typically trained over multiple epochs; however, finding the right balance is key—too few epochs lead to a model that hasn't learned enough (underfitting), while too many can lead to a model that has simply memorized the data rather than understanding it (overfitting).

5. Compare the predicted label and actual label for the first test image.

     In the Fashion MNIST dataset, the first test image is an Ankle Boot (Label 9). When you compare the two, the actual label is the ground-truth category assigned by humans, while the predicted label is the category the model deems most likely based on its probability scores. For a well-trained model, both should match; if they don't, it’s usually because the model confused the boot with a similar category, like a sneaker or a sandal, highlighting where its visual "understanding" needs more work.

6. What could be done to improve the model’s accuracy?

     To improve a model's accuracy, you can upgrade its architecture to a Deep Convolutional Neural Network (CNN) with more layers to better capture complex clothing textures. Adding Dropout and Batch Normalization helps prevent the model from memorizing the training data (overfitting) and keeps the math stable. Finally, using Data Augmentation—which creates variations of images through slight rotations or zooms—forces the model to recognize items from different angles, making it much more robust and accurate when facing new, unseen images.
