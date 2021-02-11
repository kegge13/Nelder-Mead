# Nelder-Mead
multi-threaded Nelder-Mead optimisation, written in fpc
 ----------------------------------------------------
 Based on adaptive Nelder-Mead with dimension-dependent parameters.
 Fuchang Gao, Lixing Han: Implementing the Nelder-Mead simplex algorithm with adaptive parameters
 Comput Optim Appl, DOI 10.1007/s10589-010-9329-3 [2011]

 A vertex is a vector consisting of the parameters of the function to be optimised. The length is fDim.
 The Nelder-Mead optimisation creates a simplex of fDim+1 vertices using variations on the initial vertex.
 This simplex crawls through the fDim-dimensional space using the results of a given error function.
 For this reason the simplex can be seen as a amoebe (a jellyfish like bacteria).
 The error function is called with a (fDim) vertex and is expected to calculate the difference between
 data and the function to be optimised. The user is responsible for the error function.

 The Nelder-Mead optimisation does never end by itself. Therefore the user has to decide on when
 the result is good enough using:
 -score of the error function
 -rate of change of the error function
 -limits on cycles
 -limits on time
 -limits on restarts

 This implementation can run in single-thread mode with just one amoebe and in multi-threaded mode with
 a separate amoebe in each of the started threads. When all amoebes are done the best amoebe will be reported.
 Any restarts will be done with this best result as initial vertex.
 The error function must be thread-save when running in multi-thread mode: it must preserve read-only access
 to all underlying data since multiple threads will call the error function within their own thread.
 ---
 This unit is published under the GNU Lesser General Public License v3 (LGPL-3.0).
 https://tldrlegal.com/license/gnu-lesser-general-public-license-v3-%28lgpl-3%29
