Singular Value Decomposition

["The SVD is absolutely a high point of linear algebra" (Gilbert Strang, Kai Borre)](https://books.google.com.sg/books?id=MjNwWUY8jx4C&pg=PA259)

This mathematical technique has been used across various industries and example applications include [recommender systems (Netflix prize)](http://www2.research.att.com/~volinsky/papers/ieeecomputer.pdf), [face and object recognition](http://www.iaarc.org/publications/fulltext/isarc2007-4.5_4_035.pdf), [risk modelling in equity options](http://www.orie.cornell.edu/engineering2/customcf/iws_events_calendar/files/Marco_Avellaneda_Presentation_10_16_14.pdf) and [identifying genes in brain imaging that make up Parkinson disease](http://www.ncbi.nlm.nih.gov/pubmed/12045141). 

SVD is a matrix factorisation and decomposes a matrix of any size into a  product of 3 matrices:

$$ A = U \Sigma V^T $$

$A$ : $n \times m$ : number of records as rows and number of dimensions as columns.    
$U$ : $n \times n$ : orthogonal matrix containing eigenvectors of $AA^T$.   
$\Sigma$ : $n \times m$ : singular values in the diagonal. Eigenvalues squared associated with $U$ and $V$.   
$V$ : $m \times m$ : orthogonal matrix containing eigenvectors of $A^TA$.

### Eigen to singular value decomposition
For a quick refresh, read [my post on eigenvectors and eigenvalues](http://scriptogr.am/alyssa/post/understanding-eigenvectors-and-eigenvalues-visually). SVD ties together the core concepts of linear algebra --- matrix transformations, subspaces, basis, eigens, symmetric matrices, orthogonalisation and factorisation. While this post attempts to summarise the key points, nothing beats going through the entire [MIT Linear Algebra lectures by Gilbert Strang](http://ocw.mit.edu/courses/mathematics/18-06-linear-algebra-spring-2010/). 

Eigenvalues $\lambda$ and eigenvectors $x$ are obtained by:
	$$Ax = \lambda x$$
rearranged, $$ A = Q \Lambda Q^{-1}$$.

E.g. 
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


