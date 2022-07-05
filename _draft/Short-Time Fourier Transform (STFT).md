# A Survey on Signal Transform: from FT to DWT

Fourier transform provides the frequency information of signal over the entire time. For situations in which frequency components vary over time, the Fourier transform only provides the average frequency information over the entire signal duration. Sometimes, the time-localized frequency information is expected and STFT can be utilized. 

## Mathematical analysis

Consider an $N$-point signal $x[n]$. The discrete Fourier transform (DFT) $X[k]$ is given by
$$
\begin{cases}
\displaystyle X[k]=\sum_{n=0}^{N-1}x[n]\mathrm{e}^{-\mathrm{j}\frac{2\pi k}{N}n},\quad &k=0,...,N-1
\\
\displaystyle x[n]=\frac{1}{N}\sum_{k=0}^{N-1}X[k]\mathrm{e}^{\mathrm{j}\frac{2\pi k}{N}n},\quad &k=0,...,N-1
\end{cases}
$$
where $X[k]$ can be seen as the **inner product** of signal vector $\boldsymbol{x}$ and discrete cosine signal with digital frequency $\frac{2\pi k}{N}$ and $x[n]$ can be seen as the a weighted sum of discrete cosine signal of different frequency. STFT is a sequence of transforms of as windowed signal based on DFT. Given a $L$-point window function $g[n]$, the STFT pair of $x[n]$ is given by 
$$
\begin{cases}
\displaystyle X_{STFT}[k,l]=\sum_{n=-\infty}^{+\infty}x[n]g[n-k]\mathrm{e}^{-\mathrm{j}\frac{2\pi l}{N}n}\\
\displaystyle x[n]=\sum_k\sum_lX_{STFT}[k,l]g[n-k]\mathrm{e}^{-\mathrm{j}\frac{2\pi l}{N}n}
\end{cases}
$$
$X_{STFT}$ has two variables that denote time and discrete frequency indices, respectively. Hence, STFT can be represented by a time-frequency plane with intensity.

## Simulation

To be completed...