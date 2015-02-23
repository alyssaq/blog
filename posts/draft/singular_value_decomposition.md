Singular Value Decomposition

["The SVD is absolutely a high point of linear algebra" (Gilbert Strang, Kai Borre)](https://books.google.com.sg/books?id=MjNwWUY8jx4C&pg=PA259)

This mathematical technique has been used across various industries and example applications include [recommender systems (Netflix prize)](http://www2.research.att.com/~volinsky/papers/ieeecomputer.pdf), [face and object recognition](http://www.iaarc.org/publications/fulltext/isarc2007-4.5_4_035.pdf), [risk modelling in equity options](http://www.orie.cornell.edu/engineering2/customcf/iws_events_calendar/files/Marco_Avellaneda_Presentation_10_16_14.pdf) and [identifying genes in brain imaging that make up Parkinson disease](http://www.ncbi.nlm.nih.gov/pubmed/12045141). 

## Definition
SVD is a matrix factorisation and decomposes a matrix of any size into a  product of 3 matrices:

$$ A = U S V^T $$

$A$ : $n \times m$ : number of records as rows and number of dimensions as columns.    
$U$ : $n \times n$ : orthogonal matrix containing eigenvectors of $AA^T$.   
$S$ : $n \times m$ : singular values in the diagonal. Square root of eigenvalues associated with $AA^T$ or $A^TA$ (its the same).   
$V$ : $m \times m$ : orthogonal matrix containing eigenvectors of $A^TA$.

SVD ties together the core concepts of linear algebra --- matrix transformations, subspaces, basis, eigens, symmetric matrices, orthogonalisation and factorisation. While this post attempts to provide a high-level grasp of SVD, the full proofs and background are best obtained from the entire [MIT Linear Algebra lectures by Gilbert Strang](http://ocw.mit.edu/courses/mathematics/18-06-linear-algebra-spring-2010/). 

## Example matrix
For this post, Im going to use the same matrices from [my post on eigenvectors and eigenvalues](http://scriptogr.am/alyssa/post/understanding-eigenvectors-and-eigenvalues-visually). We have a matrix $x = \begin{bmatrix}
-10 & -10 & 20 & 20\\\
-10 & 20 & 20 & -10
\end{bmatrix}$ and a transformation matrix $A = \begin{bmatrix}
1 & 0.3 \\\
0.45 & 1.2
\end{bmatrix}$. In the plot below, the dashed square shows $x$ as the corners and the transformed matrix $Ax$ as the solid shape.

![transformed_plot](https://alyssaq.github.io/blog/images/eigens-transformation_matrix.png)

This the example that we will be working with:
<pre><code class="language-python">
In[1]:
A = np.matrix([[1, 0.3], [0.45, 1.2]])
U, s, V = np.linalg.svd(A)

Out[1]:
U:[[-0.58189652 -0.81326284]
   [-0.81326284  0.58189652]]
s:[ 1.49065822  0.71444949]
V:[[-0.63586997 -0.77179621]
   [-0.77179621  0.63586997]]

# Verify calculation of A=USV
In[2]:  np.allclose(A, U * np.diag(s) * V)
Out[2]: True
</code></pre>
## Geometric interpretation
Transformation of a matrix by $U S V^T$ can be visualised as a _rotation and reflection_, _scaling_, _rotation and reflection_.

We can see this first transformation of rotation and reflection by multiplying $V^T$ and $x$:
![transformed_plot](https://alyssaq.github.io/blog/images/svd_Vx.png)

Notice the swap of colours red-blue and yellow-green indicating a reflection on the x-axis.



Eigenvalues $\lambda$ and eigenvectors $x$ are obtained by:
	$$Ax = \lambda x$$
rearranged, $$ A = Q \Lambda Q^{-1}$$.

In this decomposition, $A$ must be a square matrix.	
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    extensions: ["tex2jax.js"],
    jax: ["input/TeX", "output/HTML-CSS"],
    tex2jax: {
      inlineMath: [ ['$','$']],
      displayMath: [ ['$$','$$']],
      processEscapes: true
    },
    "HTML-CSS": { availableFonts: ["TeX"] }
  });
</script>
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>  


