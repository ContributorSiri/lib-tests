# Computer Vision: 2025 Final

- One A4 cheatsheet is allowed. Calculators are forbidden.

## 1 Multiple Choice Questions ($21$ pts)

Please choose **all correct choices** for each problem to get $3$ points. **Incorrect choice** or **no choice** will receive $0$ points; **missing choices** will receive $1$ point. 

1. Which filter(s) is (are) not able to shift the figure (a) to figure (b)?
    ![](/Images/Computer_Vision/1_1.jpg)
    (a) $\begin{pmatrix}0 & 0 & 0\\2 & 0 & 0\\0 & 0 & 0\end{pmatrix}$;     
    (b) $\begin{pmatrix}0 & 0 & 0\\0 & 0 & 2\\0 & 0 & 0\end{pmatrix}$;     
    (c) $\begin{pmatrix}0 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 0\\1 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 0\end{pmatrix}$;     
    (d) $\begin{pmatrix}0 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 1\\0 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 0\end{pmatrix}$.

2. Which of the following statements about convolution in image processing is true?     
    (a) Convolution involves flipping the filter in both dimensions and then applying cross-correlation.      
    (b) Convolution is not shift-invariant, meaning the output depends on the position of the neighborhood in the image.     
    (c) The convolution operation does not distribute over addition.    
    (d) Using a larger kernel in a Gaussian filter results in more smoothing.

3. Suppose we are using a Hough transform to do line fitting, but we notice that our system is detecting two lines where there is actually one in some example image. Which of the following is the most likely to alleviate this problem?       
    (a) Increase the size of the cells in the Hough transform.    
    (b) Decrease the size of the cells in the Hough transform.    
    (c) Sharpen the image.     
    (d) Make the image larger.

4. Which of the following statements about image classification and recognition tasks is true?  
    (a) Pose estimation is concerned with estimating the attributes of objects, such as color and size.  
    (b) Action rocognition is the task of determining the pose of each object in an image.  
    (c) Scene classification involves recognizing what type of scene is being shown in a picture.   
    (d) Detection is the task of identifying the presence of objects in an image.

5. What is the biggest benefit of image rectification for stereo matching?   
    (a) Epipoles are moved to the center of the image.  
    (b) Image contents are uniformly scaled to a desirable size.  
    (c) All epipolar lines intersect at the vanishing point.  
    (d) All epipolar lines are perfectly vertical.  
    (e) All epipolar lines are perfectly horizontal.

6. Which of the following is(are) a part(s) of the SIFT calculation pipeline?
    (a) Difference of Gaussians.  
    (b) Histogram of Gradients.  
    (c) Laplacian of Gaussians.  
    (d) Orientation Histogram.  
    (e) Image Pyramid.  
    (f) None of the above.

7. You start training your Neural Network but the loss is almost completely flat. What could be the cause?  
    (a) The learning rate is too low.  
    (b) The weight initialization scale is incorrectly set.  
    (c) The regularization strength is too high.  
    (d) The class distribution is very uneven in the dataset.  
    (e) None of the above.

## 2 True or False ($21$ pts)

For each problem, a correct answer is worth $1$ point, and the explanation is worth $2$ points.

1. Even if we use global average pooling after the last convolution layer in ResNet, we cannot train the model with input images of variable sizes.
2. The mean filter is a better tool to remove the impulse (salt and pepper) noise, comparing to the medium filter.
3. If the input to a CNN is a zero image (i.e., all pixel values are $0$), the class probabilities will come out uniform.
4. The regularization mechanism and choosing a larger model capacity are common approaches to alleviate underfitting.
5. During backpropagation, when the gradient flows backwards through sigmoid / tanh / ReLU activations, it cannot change sign.
6. Given $2$ cameras and their intrinsics and extrinsics, we can calculate the depth by $Z=\dfrac{fT}{d}$, where $f$ is the focal length, $T$ is the distance between two cameras, and $d$ is the disparity.
7. The Canny edge detector is a linear filter, because it uses the Gaussian filter to blur the image and then uses the linear filter to compute the gradient.

## 3 Short Answer Problems ($12$ pts)

1. List $3$ methods to prevent overfitting. ($3$)
2. Suppose we would like to use RANSAC to find circles in $\mathbb R^2$. Let $D=\{(x_i,y_i)\}_{1\le i\le n}$ be our data, and $I$ is the random seed group of points used in RANSAC.   
    (a) The next step of RANSAC is to fit a circle (a curve, not a filled circle!) to the points in $I$. Please formulate this as an optimization problem. That is, represent fitting a circle to the points as a problem of the form
        $$\min \sum_{i\in I} L(x_i,y_i,c_x,c_y,r),$$
    where $L$ is a function for you to determine which gives the distance from $(x_i,y_i)$ to the circle with center $(c_x,c_y)$ and radius $r$. ($2$)  
    (b) What might go wrong in solving the problem you came up with in (a) when $|I|$ is too small? ($2$)  
    (c) The next step in RANSAC is to determine what the inliers are, given the circle $(c_x,c_y,r)$. Using these inliers, we refit the circle and determine new inliers in an iterative fashion. Define mathematically what an inlier is for this problem. Mention any free variables. ($2$)

3. You are using K-means clustering in color space to segment an image. However, you notice that although pixels of similar color are indeed clustered together, the pixels in the same cluster are not spatially contiguous in the image. Describe a method to overcome this problem in the K-means framework. ($3$)

## 4 Long Answer Problems ($46$ pts)

### 4.1 Convolutional Architectures ($9$ pts)

### 4.2 Laplacian of Gaussians ($16$ pts)

### 4.3 Optical Flow ($10$ pts)

1. Derive the optical flow equation from the brightness constancy equation. Clearly state any assumption you make during derivation. ($3$)
2. Can the optical flow equation be solved given two consecutive frames without further assumption? Which values can be computed given two consecutive frames? Which values cannot be computed without additional information? Why? ($4$)
3. What is the aperture problem in optical flow? Please point out which method solves the problem, and explain how. ($3$)

### 4.4 Projective Geometry ($11$ pts)

Define a camera coordinate system which is only rotated and translated from a world coordinate system.

**Hint**: For any invertible matrix $A$ and vectors $x,y$, we have $(Ax)\times (Ay)=\det(A)(A^{-1})^T(x\times y)$.

1. Prove that parallel lines in the world reference system are still parallel in the camera reference system. ($2$)
2. Consider a unit square $pqrs$ in the world reference system, where $p,q,r,s$ are four points. Will the same square in camera reference system always have unit area? Prove or provide a counter example. ($3$)
3. Now consider affine transformations. Given some vector $p$, an affine transformation is defined as $A(p)=Mp+b$, where $M$ is an invertible matrix. Prove that under any affine transformation, the ratio of parallel line segments is invariant, but the ratio of non-parallel line segments is not invariant. ($3$)
4. Do the properties in the first three questions still hold under perspective projection? Justify your answers briefly. ($3$)