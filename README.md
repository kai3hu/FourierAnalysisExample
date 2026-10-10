# Fourier Drawing Machine

An interactive page that draws closed shapes with chains of turning circles (epicycles). Each chain is a Fourier series.

## How it works

The program treats one lap of a closed curve as one period, from t = 0 to 2π. Then it writes each coordinate as a Fourier series:

```
x_N(t) = a₀ + Σ (a_k cos kt + b_k sin kt),   k = 1 … N
y_N(t) = c₀ + Σ (c_k cos kt + d_k sin kt),   k = 1 … N
```

- The top chain sets x. The left chain sets y.
- The pen is where the two dashed guide lines cross.
- Circle k has radius √(a_k² + b_k²) and turns k times per lap.

The program calculates all coefficients one time, directly from 1024 sample points. It does not adjust them by trial and error. For each N, the Fourier coefficients give the smallest mean-square error. The page shows the maximum sampled error as a percentage of the shape height.

## Features

- Change N from 1 to 200 and see the error change.
- Select a shape: butterfly, heart, or star.
- Draw your own shape. The program closes the line and draws it with circles.
- Show or hide the circles and the original shape.

## Things to try

- **Heart:** its formula has only 4 frequencies. At N = 4, the error is almost 0.
- **Star:** sharp corners need many high-frequency circles. The error decreases slowly.
- **N = 1:** every shape becomes an ellipse.

## Fourier beyond drawing

`examples.html` has seven interactive examples. In each one, the signal is not periodic. The example shows how to make it periodic, and how that choice controls the error.

1. **JPEG:** mirror extension gives the DCT. Compare it with direct repeat (DFT), and compress an image in 8×8 blocks.
2. **MP3 / AAC:** overlapping sine windows (MDCT) remove the jumps at block edges.
3. **Spectrum analysis:** a Hann window reduces leakage.
4. **Heat equation:** odd extension gives a sine series. Each term decays as e^(−k²π²t).
5. **Spectral methods:** a derivative in frequency space is a multiplication by ik.
6. **Time series:** remove the trend, then find the seasonal peak.
7. **Fourier transform:** let the period go to infinity.

## Run it

Open `index.html` or `examples.html` in a browser. The page has no build step and no dependencies.

To publish with GitHub Pages: go to **Settings → Pages**, select the `main` branch and the root folder, then save.

## License

MIT. See [LICENSE](LICENSE).
