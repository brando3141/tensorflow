# Introduction

Let's get you up and running with TensorFlow!

But before we even get started, let's give you a sneak peek at what TensorFlow
code looks like in the Python API, just so you have a sense of where we're
headed.

Here's a little Python program that makes up some data in three dimensions, and
then fits a plane to it.

```python
import tensorflow as tf
import numpy as np

# Make 100 phony data points in NumPy.
x_data = np.float32(np.random.rand(2, 100)) # Random input
y_data = np.dot([0.100, 0.200], x_data) + 0.300

# Construct a linear model.
b = tf.Variable(tf.zeros([1]))
W = tf.Variable(tf.random_uniform([1, 2], -1.0, 1.0))
y = tf.matmul(W, x_data) + b

# Minimize the squared errors.
loss = tf.reduce_mean(tf.square(y - y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)
train = optimizer.minimize(loss)

# For initializing the variables.
init = tf.initialize_all_variables()

# Launch the graph
sess = tf.Session()
sess.run(init)

# Fit the plane.
for step in xrange(0, 201):
    sess.run(train)
    if step % 20 == 0:
        print step, sess.run(W), sess.run(b)

# Learns best fit is W: [[0.100  0.200]], b: [0.300]
```

The first part of this code builds the data flow graph.  TensorFlow does not
actually run any computation until the session is created and the `run`
function is called.

To whet your appetite further, we suggest you check out what a classical
machine learning problem looks like in TensorFlow.  In the land of neural
networks the most "classic" classical problem is the MNIST handwritten digit
classification.  We offer two introductions here, one for machine learning
newbies, and one for pros.  If you've already trained dozens of MNIST models in
other software packages, please take the red pill.  If you've never even heard
of MNIST, definitely take the blue pill.  If you're somewhere in between, we
suggest skimming blue, then red.

<div style="width:100%; margin:auto; margin-bottom:10px; margin-top:20px; display: flex; flex-direction: row">
 <a href="../tutorials/mnist/beginners/index.md" title="MNIST for ML Beginners tutorial">
   <img style="flex-grow:1; flex-shrink:1; border: 1px solid black;" src="blue_pill.png" alt="MNIST for machine learning beginners tutorial" />
 </a>
 <a href="../tutorials/mnist/pros/index.md" title="Deep MNIST for ML Experts tutorial">
   <img style="flex-grow:1; flex-shrink:1; border: 1px solid black;" src="red_pill.png" alt="Deep MNIST for machine learning experts tutorial" />
 </a>
</div>
<p style="font-size:10px;">Images licensed CC BY-SA 4.0; original by W. Carter</p>

If you're already sure you want to learn and install TensorFlow you can skip
these and charge ahead.  Don't worry, you'll still get to see MNIST -- we'll
also use MNIST as an example in our technical tutorial where we elaborate on
TensorFlow features.

## Recommended Next Steps
* [Download and Setup](../get_started/os_setup.md)
* [Basic Usage](../get_started/basic_usage.md)
* [TensorFlow Mechanics 101](../tutorials/mnist/tf/index.md)


<div class='sections-order' style="display: none;">
<!--
<!-- os_setup.md -->
<!-- basic_usage.md -->
-->
</div>

