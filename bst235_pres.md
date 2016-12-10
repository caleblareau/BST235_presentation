<style>
.footer {
    color: black;
    background: #E8E8E8;
    position: fixed;
    top: 90%;
    text-align:center;
    width:100%;
}
.midcenter {
    position: fixed;
    top: 50%;
    left: 50%;
}
.small-code pre code {
  font-size: 1em;
}

.reveal h3 {
  word-wrap: normal;
  -moz-hyphens: none;
}
.reveal h1 {
  word-wrap: normal;
  -moz-hyphens: none;
}
</style>

Assessing sparsity through a simulation study
========================================================
autosize: true  
transition-speed: slow
<br><br>
Kevin Cummiskey, Caleb Lareau, Matthew Ploenzke<br>
BST235-- Advanced Regression and Statistical Learning

<div class="footer" style="margin-top:-50px;background-color:transparent;"><SPAN STYLE="font-size:80%;font-weight:bold;">https://bit.ly/KCMbst235</a><br>December 12, 2016</SPAN></div>

Introduction
========================================================
<br>
Goal
- Investigate sparsity through simulated gene sets
      - Group sparsity and correlation
      - Sparse coefficients versus sparse support vectors
      - Point estimate bias
      - Assess Prediction 
<br>
Plan
- Consider various regularized linear and nonlinear models 
      - Lasso, Adaptive Lasso, SVM
- Consider both a linear and nonlinear underlying data-generating mechanism 
- Consider gene sets with varying levels of correlation
- Consider gene sets with varying levels of effect size


Models
========================================================
<br>
- LASSO
$$\hat{\beta}_{lasso} = \min_\beta \left\{ \left|\left|Y - X\beta\right|\right|^2 + \lambda \sum_{j = 1}^{p} \left|\beta_j\right| \right\}$$
- Adaptive LASSO
$$\hat{\beta}_{Alasso} = \min_\beta \left\{ \left|\left|Y - X\beta\right|\right|^2 + \lambda \sum_{j = 1}^{p} w_j\left|\beta_j\right| \right\} \qquad w_j = \left|1/\hat{\beta}_j\right|^v$$
- Support Vector Machine
$$\hat{\beta}_{svm} = \min_\beta \left\{ \sum_{i=1}^N \left[1-y_i f(x_i) \right]_+ + \frac{\lambda}{2}\left|\left|\beta\right|\right| \right\}$$

Models - Key Properties
========================================================
<br>
- LASSO
  - estimates not asymptotically normal
  - biased estimates for large parameters
  - bootstrap fails

- Adaptive LASSO
  - estimates asymptically normal
  - less bias for large parameter estimates
  - oracle property 
 
***
- Support Vector Machine
  - constructs optimal hyperplanes in transformed spaces
  - boundary determined by points near boundary (support vectors)
  
Gene set correlation
========================================================
<br>
- Caleb could on the fly simulate this and demonstrate the app
- N=500, p = 5 "super-gene" sets of 5 genes defined with correlation structure...
- discuss linear vs nonlinear data generating mechanism

Predictor sparsity
========================================================
<br>
- heatmap under lasso vs group lasso varying effect size - caleb
- again could be done outside the presentation to take up time

Predictor sparsity
========================================================
<br>
- heatmap under lasso vs group lasso varying correlation - caleb

Lasso - No interaction effects
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/L1small.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/L1small.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

Lasso - Interaction effects
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/L1big.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/L1big.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

Adaptive Lasso - No interaction effects
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/ALsmall.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/ALsmall.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

Adaptive Lasso - Interaction effects
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/ALbig.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/ALbig.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

Group Lasso - no interaction effects
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/grpLasso_coeffs.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/lin/grpLasso_error.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/grpLasso_coeffs.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
<img src="images/nonlin/grpLasso_error.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

SVM linear kernel
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/svmLin.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/svmLin.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

SVM Quadratic kernel
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/svmQuad.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/svmQuad.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>
SVM Gaussian kernel
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/svmRBF.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/svmRBF.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

Importance of parameter tuning
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/ErrorPlot_offset.png" width="50%" height="50%" />
<figcaption>Offset=1000</figcaption>
<img src="images/lin/ErrorPlot.png" width="50%" height="50%" />
<figcaption>Offset=0</figcaption>
</DIV>

Model comparison
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/ErrorPlot_offset.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/ErrorPlot.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

SVM sparsity - Linear kernel
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/PCplot_model5.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/PCplot_model5.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

SVM sparsity - Quadratic kernel
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/PCplot_model6.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/PCplot_model6.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

SVM sparsity - Gaussian kernel
========================================================
<DIV ALIGN=CENTER>
<img src="images/lin/PCplot_model7.png" width="50%" height="50%" />
<figcaption>Linear</figcaption>
<img src="images/nonlin/PCplot_model7.png" width="50%" height="50%" />
<figcaption>Nonlinear</figcaption>
</DIV>

Point estimate bias
========================================================
<br>
- bootstrap confidence intervals table - kevin

Conclusion
========================================================
<br>
- Group sparsity resolved under group lasso but not lasso
- L2 loss + L1 regularization = sparse coefficients
- Hinge loss + L1 regularization = sparse support vectors
- Lasso point estimates are biased and Adaptive lasso resolves this for large effect sizes
- The data generating mechanism is important for model specification

Thanks!
======================================================== 

