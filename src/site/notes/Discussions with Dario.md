---
{"dg-publish":true,"permalink":"/discussions-with-dario/","tags":["collaboration","duke-nus","discussion"],"noteIcon":""}
---

## Notes

### Dario's understanding of the literature
Dario has read several papers on SVD being used to find gene regulatory networks in biological systems. These are some of his comments on it.
1. Sparsity is the norm in biology if we look at the gene correlation networks. Standard SVDs do not have this property built in them as the singular vectors we get as the correlation of genes tends to mix up everything with everything. So we need to implement (or design by ourselves) algorithms to remove unnecessary correlations and make it into a much more refined network graph. 
2. There are a lot of SVD-related algorithms that are implemented in gene regulatory networks (a lot of literature on the web).
3. If we are implementing SVD or even tensor networks, we require a lot of post-processing of data to make meaningful biological networks. 

### Tensor networks and how to apply them in gene regulatory networks 
Dario summarized how tensor networks analyze the gene and cell data. The goal of tensor networks is to decompose a multi-dimensional tensor, our data in this case, into a sum of small 1D tensor networks that only have a direct product relation between the entries within the subspace to another space. The technical term used here is that the bond dimension of the tensor network is 1. If we manage to do that, then the single dimension tensors we get in the gene index shall correspond to the correlated genes of interest, the tensors in the cell index shall correspond to the cells that are affected by this set of genes, and the patients will probably say about the existence of this networks in another human being and be able to classify the individual as a healthy/sick person. 

### Bond dimension in tensor networks
- The concept of bond dimension in tensor networks is explained through a neat example
(NEED THE WHITE BOARD PICS!)
### SVD need not be unique
Dario gave simple proof that the singular vectors that we generate in our SVD need not be unique although the singular values are.

Consider a case where we have a singular decomposition of the form: 
$$
M = U D V'
$$
with U, and V as the orthogonal singular vector matrices and D as the diagonal matrix. Consider an invertible matrix $\Sigma$ with the property $[D, \Sigma]=0$ (i,e) it commutes with the diagonal matrix. Then we can rewrite the above expression as: 
$$
\begin{align}
M &= UDV'\\
&= UD\Sigma\Sigma^{-1}V' \\
&= U\Sigma D\Sigma^{-1}V' \\
&= \tilde{U} D \tilde{V}'
\end{align}
$$
We have now defined a new set of orthogonal vector matrices that result in the same matrix $M$. Hence, the SVD of a matrix is not unique in general. 


> [!example] 
> A quick example of a non-diagonal $\Sigma$ and a diagonal matrix $D$ that commutes: 
>$$
> \left[\begin{array}{lll}
7 & 2 & 0 \\
0 & 1 & 0 \\
0 & 0 & 4
\end{array}\right]\left[\begin{array}{lll}
3 & 0 & 0 \\
0 & 3 & 0 \\
0 & 0 & 2
\end{array}\right]=\left[\begin{array}{lll}
3 & 0 & 0 \\
0 & 3 & 0 \\
0 & 0 & 2
\end{array}\right]\left[\begin{array}{lll}
7 & 2 & 0 \\
0 & 1 & 0 \\
0 & 0 & 4
\end{array}\right]=\left[\begin{array}{lll}
21 & 6 & 0 \\
0 & 3 & 0 \\
0 & 0 & 8
\end{array}\right]
$$

