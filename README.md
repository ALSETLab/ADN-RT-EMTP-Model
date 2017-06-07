[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.61183.svg)](http://dx.doi.org/10.5281/zenodo.61183)

# FP7-IDE4L-KTHSmarTSLab-ADN-RTModel
This project contains an Active Distribution Network Power System Model developed in the FP7 IDE4L Project by KTH SmarTS Lab.
The model was developed for use with the [Opal-RT eMegaSim](http://www.opal-rt.com/product/emegasim-powergrid-real-time-digital-hardware-in-the-loop-simulator) real-time power system simulator.

## Model Versions

Several versions of the model are provided in this repository, along with a model description and a self-contained documentation (i.e. help file).

Details of the first version (V2) can be found in the open access publication in the following link:
- Ref. 1: H. Hooshyar, F. Mahmood, L. Vanfretti, M. Baudette, ''Specification, implementation, and hardware-in-the-loop real-time simulation of an active distribution grid,'' Sustainable Energy, Grids and Networks, Volume 3, September 2015, Pages 36-51, ISSN 2352-4677, [http://dx.doi.org/10.1016/j.segan.2015.06.002](http://dx.doi.org/10.1016/j.segan.2015.06.002)

The second version of the model was developed to overcome several of the limitations in accuracy of the "stub-line" modeling used to decouple the model into different cores. Hence, V6 partitions each subsystem into state-space-nodal (SSN) groups so that parallel computations can be carried out with the ARTEMiS-SSN solver. More information about the model can be found on the "ReadMe.pdf" included in the V6 folder, and in the following paper:
- Ref. 2: H. Hooshyar, L. Vanfretti, C. Dufour, ''Delay-free parallelization for real-time simulation of a large active distribution grid model'', in Proc. IEEE IECON, Florence, Italy, October 23-27, 2016. [https://doi.org/10.1109/IECON.2016.7793885](https://doi.org/10.1109/IECON.2016.7793885) Note: A pre-print copy of this paper is available in the V6 folder, however, note that it is not the final version that will appear in the proceedings of the IEEE IECON conference.
A modified version of this model for Matlab 2015aSP1 is also available.

A third version of the model was developed to address some of the differences found when implementing the model using EMTP-RV. More information about the model can be found on the [V6_1_correcctions.pdf](https://github.com/SmarTS-Lab/FP7-IDE4L-KTHSmarTSLab-ADN-RTModel/blob/master/V6p1/V6_1%20corrections.pdf), 

The EMTP-RV version is reported in the following paper, and will be uploaded in this repository in the future:
- Ref. 3: A. Haddadi, H. Hooshyar, J. Mahseredjian, C. Dufour, and Luigi Vanfretti, A First Step Towards the Implementation and Software-to-Software Validation of an Active Distribution Network Model'', in Proc. International Conference on Power System Transients (IPST), Seoul, Republic of Korea, June 26th-29th, 2017. [Website:](http://www.ipst2017.com/)

### Requirements:
You will need access to an Opal-RT eMegaSim simulator or equivalent, and associated software. The models run with the following software versions:
- V2: Runs under RT-Lab v10.6, ARTEMiS v6.3.3 and MATLAB 2010b
- V6: Runs under RT-Lab v11, ARTEMiS v7.0.2 and Matlab 2011b 
- V6.1: It requires at least RT-Lab v11.0.8 and ARTEMiS v7.0.4. It runs with both Matlab 2011b and Matlab 2015aSP1.

Please contact Opal-RT support if you have issues with your own software configuration: [link](http://www.opal-rt.com/support/support-request)

### Using our Models = Citing our Work!
If you use our model in your work or research, all we ask from you in exchange is that you **cite our publications above**! If you only have space for one citation, please cite Ref. 1.

### Contributing
If you make modifications to the model that improve it or add functionality, you are welcome to submit a "pull request". When you do this, please add a new folder with your files, and use versioning (e.g. VXXX.0.0), please start with V010.0.0).

### License
The software is licensed under GPLv3. If you are unfamiliar with the GPLv3 terms and conditions, please see this [link](https://www.gnu.org/licenses/quick-guide-gplv3.en.html).


## Model Description
This model represents an active distribution grid with high penetration of distributed generation (DG). The model was initially developed as part of the IDE4L [(Ideal Grid for All)](http://ide4l.eu/) project, financed by the European Commission [1]. It can be used to study dynamics of active distribution grids under several test scenarios.

The modelled grid is a 79-bus multi-phase unbalanced network including components of 10 different types, each with electrical and mechanical parts, various controllers and protection systems, allowing to simulate the behavior of an active distribution grid. Details of the component models and the grid structure are explained in [2], see Ref. 1 below. The modelled grid includes four different voltage levels: HV (220 kV), MV (36 kV), LV (6.6 kV), and residential LV (0.4 kV).

### HV section:
The HV section is a 6-bus network adopted from [3] with 50 MW wind farm generation added.
### MV section:
The MV section is based on the IEEE 34 bus test feeder with the main difference being that three constant power loads (total of 110 kVA) are replaced by motor load models to incorporate motor loads dynamics, and two 1.5 MW wind farms are added to the middle and end of the feeder [4]. In addition, a circuit breaker supervised by an overcurrent protection relay and a three-phase recloser are added to the beginning and middle of the MV feeder, respectively.
### LV and residential LV sections:
The LV and residential LV sections are based on the IEEE 37 bus test feeder. The following differences are made: two constant power loads (total of 150 kVA) are replaced by motor load models; two PV farm models (total of 1.05 MW), three residential PV system models (total of 0.77 MW), and two battery storage models (total of 325 Ah) are added to the feeder [4]; and two sets of single-phase reclosers are added to this section.

In order to comply with real-time simulation constraints, the model was implemented in three subsystems each partitioned into SSN groups so that parallel computations can be performed using the ARTEMiS-SSN solver. More details on the real-time simulation setup of the model can be found in [5].

### References
[1] EU-FP7 IDE4L project official website: [link](http://www.ide4l.eu)

[2] H. Hooshyar, F. Mahmood, L. Vanfretti, M. Baudette, “Specification, implementation, and hardware-in-the-loop real-time simulation of an active distribution grid,” Elsevier Sustainable Energy, Grids and Networks (SEGAN), vol. 3, pp. 36-51, September 2015. [http://dx.doi.org/10.1016/j.segan.2015.06.002](http://dx.doi.org/10.1016/j.segan.2015.06.002)

[3] R. Billinton, S. Kumar, N. Chowdhury, K. Chu, K. Debnath, L. Goel, E. Khan, P. Kos, G. Nourbakhsh, J. Oteng-Adjei, “A reliability test system for educational purposes-basic data”, IEEE Transactions on Power Systems, vol. 4, no. 3, pp. 1238-1244, Aug. 1989.

[4] Available on-line at: [link](http://www.ewh.ieee.org/soc/pes/dsacom/testfeeders/index.html)

[5] H. Hooshyar, L. Vanfretti, C. Dufour, “Delay-free parallelization for real-time simulation of a large active distribution grid model”, in Proc. IEEE IECON, Florence, Italy, October 23-27, 2016.
