# V6.2 Release Notes

  - Previous versions of this model had issues when using the state-space nodal (SSN) solver OLTC model within the SSN library.
  - This update uses a new version of the OLTC model, which makes it possible to simulate the OLTC without an explicit representation of taps via switches (which considerably increases computation requirements).
  - The model does not require to generate S-functions any longer. Model only needs to be built in RT-Lab to be executed.

## Requirements and Dependencies
- RT-Lab v11.3.1.34
- ARTEMiS v7.3.0.1251
- MATLAB 2015aSP1

## Authors
- Hossein Hooshyar, RPI, October 2018.
