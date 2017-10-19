# ART-TV

Code to reconstruct the shape of a grain from a topo-tomography dataset collected using dark-field X-ray microscopy ([DFXRM](https://www.nature.com/articles/ncomms7098)) at beamline BL06 of the European Synchrotron Radiation Facility (ESRF).

The reconstruction algorithm combines the Algebraic Reconstruction Technique (ART) and Total Variation (TV) <sup>[1](#myfootnote1)</sup>.

Reconstruction steps:

 1. For each projection, sum all images collected varying the "rock" and "roll" angles. The procedure is outlined in the [recon3d manual](https://github.com/albusdemens/Recon3D/blob/master/Manual_Recon3D.pdf). Key scripts: getdata.py, recon3d.py, img_sum.py.
 2. Reconstruct the sample using ART-TV. Script: reconstr.m, which calls ART_TV_reconstruct_2d_new.m. To use only part of the input dataset, see reconstr_one_ang_range.m.

It is also possible to compare the 3D grain reconstruction from ART-TV with the reconstruction from recon3d and with the experimental data. Script: Compare_recon3d_ART.m. The script also combines information from the recon3d and ART-TV reconstruction in a single volume, with shape defined by the recon3d reconstruction for a certain completeness value. In the selected volume, the voxels have orientation calculated by recon3d.

Contributors: A.Cereser, M. Busi

Technical University of Denmark, Department of Physics, NEXMAP

<a name="myfootnote1">1</a>: LaRoque, S. J., Sidky, E. Y., & Pan, X. (2008). Accurate image reconstruction from few-view and limited-angle data in diffraction tomography. JOSA A, 25(7), 1772-1782.
