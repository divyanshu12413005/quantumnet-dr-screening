
   ## Team
   - Nayan Prakash (team leader)
   - Divyanshu Singh Chauhan
   - Aditya Jarwal


# Hybrid Classical-Quantum Transfer Learning for Diabetic Retinopathy Screening

Binary DR vs No-DR screening on APTOS 2019. A pretrained ResNet50 gives 2048-D features, a trainable layer reduces them to n values, and a PennyLane-simulated variational circuit (dressed quantum circuit, as in Bali et al., MethodsX 14, 103185, 2025) classifies them. A matched classical control replaces only the quantum circuit.

## Results (550-image test set)

| Model | Seeds | Test accuracy |
| --- | --- | --- |
| Simple CNN | 1 | 86.91% |
| ResNet50 (end to end) | 6 | 93.70% +/- 0.36 |
| MobileNetV2 | 1 | 94.73% |
| Hybrid (4 qubits, 6 layers) | 6 | 94.97% +/- 0.39 |
| Classical control | 6 | 95.24% +/- 0.34 |

Hybrid vs classical control: Wilcoxon p = 0.47 (no significant difference).

## Files

- `QuantumNet_Final_Standalone.ipynb`: data setup, ResNet50 feature extraction, hybrid vs classical, ablation, plots
- `QuantumNet_Baselines_MultiSeed.ipynb`: CNN / ResNet50 / MobileNetV2 over multiple seeds
- `QuantumNet_Kaggle.ipynb`: single-seed baselines (CNN, ResNet50, MobileNetV2)

## How to run

1. Open a notebook on Kaggle (File > Import Notebook).
2. Add the input "APTOS 2019 Blindness Detection", set Accelerator to GPU and Internet to On.
3. Run the cells from top to bottom.

## Notes

- Split: stratified 70/15/15, seed 42 (2563 / 549 / 550 images).
- Software used: PyTorch 2.11, PennyLane 0.45.1.
- Never commit API tokens (for example Kaggle tokens) to the repository.
- This is a research prototype and not a medical device.
