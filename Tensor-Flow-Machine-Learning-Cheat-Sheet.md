# TensorFlow Cheat Sheet: Basics

## Installation

To install TensorFlow, use pip:

```bash
pip install tensorflow
```

## Importing

Import TensorFlow in your Python code:

```python
import tensorflow as tf
```

## Tensors

Tensors are the fundamental building blocks in TensorFlow.

```python
# Create a tensor
tensor = tf.constant([1, 2, 3])

# Perform element-wise operations
result = tensor + 2
```

## Variables

Variables are mutable tensors used to hold and update model parameters.

```python
# Create a variable
var = tf.Variable(3.0)

# Update the variable
var.assign(4.0)
```

## Operations

TensorFlow supports various mathematical operations.

```python
# Basic operations
addition = tf.add(a, b)
subtraction = tf.subtract(a, b)
multiplication = tf.multiply(a, b)
division = tf.divide(a, b)

# Matrix operations
matrix_product = tf.matmul(matrix1, matrix2)
```

## Neural Networks

Building a simple neural network using TensorFlow's high-level APIs.

```python
from tensorflow.keras import layers, models

model = models.Sequential([
    layers.Dense(64, activation='relu', input_shape=(input_dim,)),
    layers.Dense(10, activation='softmax')
])

model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
```

## Training

Train a model using training data.

```python
model.fit(x_train, y_train, epochs=10, batch_size=32, validation_data=(x_val, y_val))
```

## Saving and Loading

Save and load model weights.

```python
# Save model
model.save('model.h5')

# Load model
model = tf.keras.models.load_model('model.h5')
```

## GPU Acceleration

Utilize GPU for accelerated training.

```python
# Check for GPU availability
print("GPU Available:", tf.test.is_gpu_available())

# Enable GPU memory growth
physical_devices = tf.config.experimental.list_physical_devices('GPU')
tf.config.experimental.set_memory_growth(physical_devices[0], True)
```

## Custom Operations

Define custom operations using TensorFlow's computation graph.

```python
@tf.function
def custom_operation(x):
    return tf.square(x) + 2 * x

result = custom_operation(5)
```

## Conclusion

This cheat sheet covers the basics of TensorFlow for machine learning. For more details, refer to the official [TensorFlow documentation](https://www.tensorflow.org/).

---
**Note:** This cheat sheet is a reference guide and might not cover all scenarios. Always refer to the official documentation and consult with experienced developers for complex projects.

Feel free to create a pull request and customize and format this cheat sheet according to your preferences.

