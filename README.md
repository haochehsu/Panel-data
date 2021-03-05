# Panel-data

The DGP has 400 obervations with 5 periods and 5 attributes. The true parameters including an intercept <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbeta%3D%281%2C+2%2C+3%2C+4%2C+5%29" 
alt="\beta=(1, 2, 3, 4, 5)">. The model is specified as following

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+y_i%3DX_i%5Cbeta%2BW_ib_i%2B%5Cepsilon_i" 
alt="y_i=X_i\beta+W_ib_i+\epsilon_i">

with <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+W_i%5Csubseteq+X_i" 
alt="W_i\subseteq X_i">, <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cepsilon_i%5Csim+N%280%2C%5Csigma%5E2+I_5%29" 
alt="\epsilon_i\sim N(0,\sigma^2 I_5)">, and <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+b_i%5Csim+N%280%2C+D%29" 
alt="b_i\sim N(0, D)"> where <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Csigma+%3D+1" 
alt="\sigma = 1"> and <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+D%3D1" 
alt="D=1">.

### Fixed effect estimation

A general fixed effects estimation includes two different approaches: mean-differencing and first-differencing.

- Mean-differencing:

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0Ay_%7Bit%7D+%26%3D+x_%7Bit%7D%27%5Cbeta+%2B+%5Calpha_i+%2B+%5Cepsilon_%7Bit%7D%5C%5C%0A%5Coverline%7By_i%7D+%26%3D+%5Coverline%7Bx_i%7D%27%5Cbeta+%2B+%5Calpha_i+%2B+%5Coverline%7B%5Cepsilon_i%7D%0A%5Cend%7Balign%2A%7D" 
alt="\begin{align*}
y_{it} &= x_{it}'\beta + \alpha_i + \epsilon_{it}\\
\overline{y_i} &= \overline{x_i}'\beta + \alpha_i + \overline{\epsilon_i}
\end{align*}">

Differencing the two equations yields

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+y_%7Bit%7D%5E%2A+%3D+x_%7Bit%7D%5E%7B%2A%27%7D%5Cbeta+%2B+%5Cnu_i" 
alt="y_{it}^* = x_{it}^{*'}\beta + \nu_i">

- First-differencing:

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0Ay_%7Bit%7D+%26%3D+x_%7Bit%7D%27%5Cbeta+%2B+%5Calpha_i+%2B+%5Cepsilon_%7Bit%7D%5C%5C%0Ay_%7Bi%2Ct-1%7D+%26%3D+x_%7Bi%2Ct-1%7D%27%5Cbeta+%2B+%5Calpha_i+%2B+%5Cepsilon_%7Bi%2Ct-1%7D%0A%5Cend%7Balign%2A%7D" 
alt="\begin{align*}
y_{it} &= x_{it}'\beta + \alpha_i + \epsilon_{it}\\
y_{i,t-1} &= x_{i,t-1}'\beta + \alpha_i + \epsilon_{i,t-1}
\end{align*}">

Subtracting the equations yields

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cwidetilde%7By_%7Bit%7D%7D+%3D+%5Cwidetilde%7Bx_%7Bit%7D%7D%27%5Cbeta+%2B+%5Ceta_%7Bit%7D" 
alt="\widetilde{y_{it}} = \widetilde{x_{it}}'\beta + \eta_{it}">

Running OLS, after dropping the intercept, the estimated coefficients are

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Chat%7B%5Cbeta%7D%3D%5C%7B1.9965%2C+2.9715%2C+4.0049%2C+4.9871%5C%7D" 
alt="\hat{\beta}=\{1.9965, 2.9715, 4.0049, 4.9871\}">

### Random effect estimation with MLE

The random effect is estimated with MLE with the following results:

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0A%5Chat%7B%5Cbeta%7D%26%3D%5C%7B1.0079%2C+2.0210%2C+3.0000%2C+3.9895%2C+4.9935%5C%7D%5C%5C%0A%5Chat%7BD%7D%26+%3D+1.0500%5C%5C%0A%5Chat%7B%5Csigma%5E2%7D+%26%3D+1.0500.%0A%5Cend%7Balign%2A%7D" 
alt="\begin{align*}
\hat{\beta}&=\{1.0079, 2.0210, 3.0000, 3.9895, 4.9935\}\\
\hat{D}& = 1.0500\\
\hat{\sigma^2} &= 1.0500.
\end{align*}">

### Random effect with Bayesian estimation

Starting with the priors,

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0Ab_i%26%5Csim+N%5Cleft%28+b_0%2C+C_0%5Cright%29%5C%5C%0AD%26%5Csim+IW%5Cleft%28+d_0%2C+D_0%5Cright%29%5C%5C%0A%5Csigma%5E2%26%5Csim+IG%5Cleft%28+%5Cdelta_0%2C+%5Cnu_0%5Cright%29%5C%5C%0A%5Cend%7Balign%2A%7D" 
alt="\begin{align*}
b_i&\sim N\left( b_0, C_0\right)\\
D&\sim IW\left( d_0, D_0\right)\\
\sigma^2&\sim IG\left( \delta_0, \nu_0\right)\\
\end{align*}">

the updating processes are:

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cbegin%7Balign%2A%7D%0A%5Cleft%5B+b_i%7C%5Cbeta%2C+y%2C+D%2C+%5Csigma%5E2%5Cright%5D%26%5Csim+N%5Cleft%28+%5Chat%7Bb_i%7D%2C+%5Chat%7BC_i%7D%5Cright%29+%5C+%5Cforall+i%3D1%2C...%2Cn.+%5C+%5C+%5C+%5Ctext%7B+where+%7D+%5C+%5Chat%7BC_i%7D%3D%5Cleft%28+D%5E%7B-1%7D+%2B+%5Cdfrac%7BW_i%27+W_i%7D%7B%5Csigma%5E2%7D%5Cright%29%5E%7B-1%7D+%5C+%5C+%5Ctext%7Band%7D+%5C+%5C+%5Chat%7Bb_i%7D%3D%5Chat%7BC_i%7D%5Cleft%28%5Cdfrac%7BW_i%5Cleft%28+y_i-X_i%5Cbeta%5Cright%29%7D%7B%5Csigma%5E2%7D%5Cright%29%5C%5C%0A%5Cleft%5B+D%7C+%5C%7Bb_i+%5C%7D%5Cright%5D%26%5Csim+IW+%5Cleft%28+d_0%2Bn%2C+%5Cleft%5B+%5Csum_%7Bi%3D1%7D%5En+b_i+b_i%27%5Cright%5D%5E%7B-1%7D%5Cright%29%5C%5C%0A%5Cleft%5B+%5Csigma%5E2%7Cy%2C%5Cbeta%2C+%5C%7B+b_i%5C%7D%5Cright%5D+%26%5Csim+IG%5Cleft%28%5Cdfrac%7B%5Cnu_0%2BnT%7D%7B2%7D%2C+%5Cdfrac%7B%5Cdelta_0%2B%5Csum_%7Bi%3D1%7D%5En+e_i%27+e_i%7D%7B2%7D%5Cright%29+%5C+%5C+%5C+%5Ctext%7Bwhere+%7D+%5C+e_i%3Dy_i-X_i%5Cbeta-W_ib_i%5C%5C%0A%5Cleft%5B+%5Cbeta%7Cy%2C+D%2C+%5Csigma%5E2%5Cright%5D%26%5Csim+N%5Cleft%28%5Chat%7B%5Cbeta%2C+%5Chat%7BB%7D%7D%5Cright%29+%5C+%5C+%5C+%5Ctext%7Bwhere+%7D+%5C+%5Chat%7B%5Cbeta%7D%3D%5Cleft%28+B_0%5E%7B-1%7D+%2B+%5Csum_%7Bi%3D1%7D%5En+x_i%27+%5Cleft%28+W_i+D++W_i%27+%2B+%5Csigma%5E2+I_T%5Cright%29%5E%7B-1%7D%5Cright%29%5E%7B-1%7D%5C%5C%0A%26%5Ctext%7Band%7D+%5C+%5Chat%7B%5Cbeta%7D+%3D+%5Chat%7BB%7D%5Cleft%28B_0%5E%7B-1%7D%5Cbeta_0%2B%5Csum_%7Bi%3D1%7D%5En+x_i%27+%5Cleft%28+W_i+D+W_i%27%2B%5Csigma%5E2+I_T%5Cright%29%5E%7B-1%7D+y_i%5Cright%29.%0A%5Cend%7Balign%2A%7D" 
alt="\begin{align*}
\left[ b_i|\beta, y, D, \sigma^2\right]&\sim N\left( \hat{b_i}, \hat{C_i}\right) \ \forall i=1,...,n. \ \ \ \text{ where } \ \hat{C_i}=\left( D^{-1} + \dfrac{W_i' W_i}{\sigma^2}\right)^{-1} \ \ \text{and} \ \ \hat{b_i}=\hat{C_i}\left(\dfrac{W_i\left( y_i-X_i\beta\right)}{\sigma^2}\right)\\
\left[ D| \{b_i \}\right]&\sim IW \left( d_0+n, \left[ \sum_{i=1}^n b_i b_i'\right]^{-1}\right)\\
\left[ \sigma^2|y,\beta, \{ b_i\}\right] &\sim IG\left(\dfrac{\nu_0+nT}{2}, \dfrac{\delta_0+\sum_{i=1}^n e_i' e_i}{2}\right) \ \ \ \text{where } \ e_i=y_i-X_i\beta-W_ib_i\\
\left[ \beta|y, D, \sigma^2\right]&\sim N\left(\hat{\beta, \hat{B}}\right) \ \ \ \text{where } \ \hat{\beta}=\left( B_0^{-1} + \sum_{i=1}^n x_i' \left( W_i D  W_i' + \sigma^2 I_T\right)^{-1}\right)^{-1}\\
&\text{and} \ \hat{\beta} = \hat{B}\left(B_0^{-1}\beta_0+\sum_{i=1}^n x_i' \left( W_i D W_i'+\sigma^2 I_T\right)^{-1} y_i\right).
\end{align*}">

The estimated parameters are

<img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Chat%7B%5Cbeta%7D%3D%5C%7B1.0176%2C+2.0090%2C+2%2C0068%2C+3.9987%2C+4.9888%5C%7D" 
alt="\hat{\beta}=\{1.0176, 2.0090, 2,0068, 3.9987, 4.9888\}">.

The sampling process can be illustreated in the following graph:

