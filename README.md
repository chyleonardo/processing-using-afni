# processing-using-afni
this repository includes all the methods I've used in AFNI
Here is the processing script I have already used.
I wrote this mostly for myself
Also welcome any comments

0. DICOM to nifti
   tcsh @dcm_make_nifti
   output is run-based afni file (.HEAD & .BRIK)

1. slice timing
   the slice timing information is not included in the .HEAD file
   we can check the information through: dicom_hdr -slice_times *.hdr
   In the current TR = 2.45s sequence, tpattern is alt+z2
   3dTshift -tpattern alt+z2 -prefix XX *.nii

2. motion correction
   3dVolreg

3. epi to anatomy 
   affine transformation & distortion correction 

4. anatomy to template 

5. univariate analysis
   scaling & smoothing & GLM

6. surface reconstruction
   setenv FREESURFER_HOME /usr/local/freesurfer
   source $FREESURFER_HOME/SetUpFreeSurfer.csh
   setenv SUBJECTS_DIR <path to subject data>
   recon-all 

7. volume-based analysis shown on surface 
   SUMA
   the cd should be in the volume directory, or AFNI cannot show the dataset
   suma -spec * -sv *


8. fMRI dataset whole control
   nibabel tutorial 

9. ROI_label check FreeSurfer 
   in SUMA .lt file


