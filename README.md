# Hand Prediction Model for Unity

Hey there! We’re thrilled you’re here. This is the quick start guide for using our hand prediction model in Unity. 

Detailed information of the model can be found in our paper. If you use this work, please cite our paper:

> ```
> Nisal Menuka Gamage, Deepana Ishtaweera, Martin Weigel, and Anusha Withana. 2021.
> So Predictable! Continuous 3D Hand Trajectory Prediction in Virtual Reality.
> In The 34th Annual ACM Symposium on User Interface Software and Technology (UIST '21).
> Association for Computing Machinery, New York, NY, USA, 332–343.
> https://doi.org/10.1145/3472749.3474753
> ```

## Test Procedure

### Requirements:

- Unity Editor version: 2022.3.18f1 (tested)
- MathNet.Numerics.5.0.0 (for prediction algorithm)
- Oculus XR Plugin (for Meta Quest headsets)

### Quick Start:

1. Add root folder to Unity project's Assets.
2. Designed for Meta Quest headsets (configurable for others).

## Scripts Overview

### 1. `HandPredictionModelMatrix.cs`
Implements a trajectory prediction model for hand motion in virtual reality, based on Gamage et al.'s method. The model uses past hand positions to estimate future displacement using a 5th-order polynomial function with velocity, acceleration, jerk, snap, and crackle terms.

**Key Features:**
- Matrix-based computation of predicted displacement.
- Adjustable sampling and prediction intervals.
- Includes analytical functions for overshoot and velocity prediction.
- Requires MathNet.Numerics for matrix operations.

**Dependencies:**
- MathNet.Numerics.LinearAlgebra (install via NuGet for Unity)

### 2. `HandPositionPredictor.cs`
Applies the prediction model from `HandPredictionModelMatrix` to update a GameObject's position each frame in Unity. It allows a GameObject to "lead" its tracked origin based on anticipated motion.

**Usage:**
- Attach to the GameObject you want to move based on predicted hand motion.
- Assign the `trackingOrigin` (e.g., a hand or controller).
- Adjust `SAMPLE_SIZE`, `SAMPLE_INTERVAL`, and `PREDICTION_TIME` for tuning.

**Notes:**
- Uses Unity's `FixedUpdate()` for consistent sampling.
- Suitable for haptic feedback or anticipatory interaction design.

### 3. `ChangeScreenRefreshRate.cs`
Configures the display refresh rate on Meta Quest devices using Oculus APIs.

**Usage:**
- Attach to any GameObject (e.g., an initialization manager).
- Change the `TARGET_RATE` variable to match your application's preferred frame rate (e.g., 80Hz, 90Hz).

**Note:**
- Only effective on supported devices like Meta Quest.
- Logs success or failure at runtime.
- For optimal performance, ensure that the frame rate, screen refresh rate, `FixedUpdate` interval (via `SAMPLE_INTERVAL`), and `PREDICTION_TIME` are chosen such that they are harmonized. Ideally, these values should be multiples of each other.

## Contributors (From aid-lab)

- [@YihaoDong](https://github.com/YihaoDong)
- [@PamudithaSomarathne](https://github.com/PamudithaSomarathne)
- [@NisalMenuka](https://au.linkedin.com/in/nisal-menuka-gamage-0813ba22)
- [@DeepanaIshtaweera](https://github.com/deepanaishtaweera)
- [@wdanusha](https://www.github.com/wdanusha)

## License

This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

<p align="left">
  <img src="Documentation/by.png" width="200" />
</p>
