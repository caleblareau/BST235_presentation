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
transition-speed: slow
width: 1920
height: 1080
<br><br>
Kevin Cummiskey, Caleb Lareau, Matthew Ploenzke<br>
BST235-- Advanced Regression and Statistical Learning

<div class="footer" style="margin-top:-50px;background-color:transparent;"><SPAN STYLE="font-size:80%;font-weight:bold;">bit.ly/KCMbst235</a><br>December 12, 2016</SPAN></div>

Overview
========================================================
<br>
- Investigate sparsity through simulated gene sets
      - Group sparsity and correlation
      - Sparse coefficients versus sparse support vectors
      - Point estimate bias
      - Assess Prediction 
      <br><br><br>
- Consider various regularized linear and nonlinear models 
      - Lasso, Adaptive Lasso, SVM
- Consider both a linear and nonlinear underlying data-generating mechanism 
- Simulate gene sets with varying levels of correlation/effect sizes


 
========================================================
LASSO <br>
  - estimates not asymptotically normal
  - biased estimates for large parameters
  - bootstrap fails <br><br>
$$\hat{\beta}_{lasso} = \min_\beta \left\{ \left|\left|Y - X\beta\right|\right|^2 + \lambda \sum_{j = 1}^{p} \left|\beta_j\right| \right\}$$ <br><br>

  
Group LASSO <br>
  - estimates not asymptotically normal, biased
  - adds L1-L2 penalty to impose grouping <br><br>
$$\scriptsize \hat{\beta}_{group} = \min_\beta \left\{ \left|\left|Y - X\beta\right|\right|^2 + \lambda \sum_{j = 1}^{p} \left| \left|\beta_j\right|\right|_{G_j} \right\}$$<br><br>

  
 
========================================================
Adaptive LASSO
  - estimates asymptically normal
  - decreasing bias for increasing parameter estimates
  - oracle property <br><br>
$$\scriptsize \hat{\beta}_{Alasso} = \min_\beta \left\{ \left|\left|Y - X\beta\right|\right|^2 + \lambda \sum_{j = 1}^{p} w_j\left|\beta_j\right| \right\} \qquad w_j = \left|1/\hat{\beta}_j\right|^v$$<br><br>

Support Vector Machine
  - constructs optimal hyperplanes in transformed spaces
  - boundary determined by points near boundary (support vectors)<br><br>
$$\scriptsize \hat{\beta}_{svm} = \min_\beta \left\{ \sum_{i=1}^N \left[1-y_i f(x_i) \right]_+ + \frac{\lambda}{2}\left|\left|\beta\right|\right| \right\}$$

Interactive Demo
========================================================

Lasso - Linear Data Generation
========================================================
<br><br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/L1small.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>Linear Model Specification</figcaption></DIV>
</DIV>
***
<br><br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/L1big.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>Nonlinear Model Specification</figcaption></DIV>
</DIV>

Lasso - Non-Linear Data Generation
========================================================
<br><br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/L1small.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>Linear Model Specification</figcaption></DIV>
</DIV>
***
<br><br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/L1big.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>Nonlinear Model Specification</figcaption></DIV>
</DIV>

Group Lasso - Linear Model Specification 
========================================================
<br>
<img src="bst235_pres-figure/unnamed-chunk-1-1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="1080px" style="display: block; margin: auto;" />

SVM linear kernel
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/svmLin.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/svmLin.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>

SVM sparsity - Linear kernel
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/PCplot_model5.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/PCplot_model5.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>


SVM Quadratic kernel
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/svmQuad.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/svmQuad.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>

SVM sparsity - Quadratic kernel
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/PCplot_model6.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/PCplot_model6.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>

SVM Gaussian kernel
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/svmRBF.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/svmRBF.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>

SVM sparsity - Gaussian kernel
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/PCplot_model7.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/PCplot_model7.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>

Importance of parameter tuning
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/ErrorPlot_offset.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>Offset=1000</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/ErrorPlot.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>Offset=0</figcaption></DIV>
</DIV>

Model comparison
========================================================
<br><br>

<DIV ALIGN=CENTER>
<img src="images/lin/ErrorPlot_offset.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Linear Data Simulation)</figcaption></DIV>
</DIV>
***
<br><br>

<DIV ALIGN=CENTER>
<img src="images/nonlin/ErrorPlot.png" width="80%" height="80%" />
<DIV ALIGN=CENTER><figcaption>(Nonlinear Data Simulation)</figcaption></DIV>
</DIV>

Bootstrap No Correlation
========================================================
<br>
<DIV ALIGN=CENTER>
<img src="images/kev/bootstrapTable1new.png" width="80%" height="80%" />
</DIV>

Bootstrap Correlated Predictors
========================================================
<br>
<DIV ALIGN=CENTER>
<img src="images/kev/bootstrapTable2new.png" width="80%" height="80%" />
</DIV>
- Bootstrap fails with LASSO

Conclusion
========================================================
<br>
- Group sparsity resolved under group lasso but not lasso
- L2 loss + L1 regularization = sparse coefficients
- Hinge loss + L1 regularization = sparse support vectors
- Lasso point estimates are biased and Adaptive lasso resolves this for large effect sizes

<br><br>
- Underlying data and choice of model is vital for accurate statistical inferences
  - We've created an interactive platform to build intuition

Citations
========================================================
<br>
[1] Chatterjee, A., and S. N. Lahiri. "Rates of convergence of the adaptive LASSO estimators to the oracle distribution and higher order refinements by the bootstrap." The Annals of Statistics 41.3 (2013): 1232-1259.

[2] Cortes, Corinna, and Vladimir Vapnik. "Support-vector networks." Machine learning 20.3 (1995): 273-297.

[3] Tibshirani, Robert. "Regression shrinkage and selection via the lasso." Journal of the Royal Statistical Society. Series B (Methodological) (1996): 267-288.

[4] Yuan, Ming, and Yi Lin. "Model selection and estimation in regression with grouped variables." Journal of the Royal Statistical Society: Series B (Statistical Methodology) 68.1 (2006): 49-67.

[5] Zou, Hui. "The adaptive lasso and its oracle properties." Journal of the American statistical association 101.476 (2006): 1418-1429.

Thanks
========================================================
