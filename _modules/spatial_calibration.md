---
title:  Spatial calibration
layout: module

prerequisites:
  - "[Basics properties of images and pixels](../pixels)"
  
objectives:
  - Understand that a pixel index is related to a physical coordinate.
  - Understand that a spatial calibration allows for physical size measurements.

motivation: >
  We would like to relate the image dimensions to a physical size. 
  The relation between pixels and physical size is referred to as spatial calibration. 
  Image calibration is dictated by acquisition and detection parameters of a microscope, such as magnification, 
  camera detector size, sampling, etc, and is  usually stored within the so-called image metadata. 
  Before performing quantitative measurements, e.g. volume, area, ..., 
  you should make sure that the spatial calibration has been set appropriately. 
   
concept_map: >
  graph TD
    Im("Image") -->|has many| P("Pixel/Voxel")
    Im --> |has| C("Calibration")
    P -->|has| Va("Value")
    P -->|has| I("Indices")
    P --> |has| RWC("Real world coordinate")
    C --> RWC
    I --> RWC

figure: /figures/spatial_calibration.png
figure_legend: Spatial calibration and size measurements

activity_preface: |
    Emphasize where to find spatial calibration information and why it can 
    be important. How to edit spatial calibration and perform consistency checks. 
    Discuss how for certain cases one can convert pixel measurements to calibrated measurements, e.g. 
    For example area and lengths for 2D and Volume for 3D.
    Some example images:
    - [xyz_8bit__mitotic_plate_calibrated.tif](https://github.com/NEUBIAS/training-resources/raw/master/image_data/xyz_8bit__mitotic_plate_calibrated.tif)
    - [xyz_8bit__mitotic_plate_badZcalibrated.tif](https://github.com/NEUBIAS/training-resources/raw/master/image_data/xyz_8bit__mitotic_plate_badZcalibrated.tif)
    - [xyz_8bit__mri_head.tif](../image_data/xyz_8bit__mri_head.tif)


activities:
    - ["ImageJ GUI", "spatial_calibration/activities/spatial_calibration_imagejgui.md", "markdown"]

exercises:
    - ["ImageJ GUI", "spatial_calibration/exercises/spatial_calibration_imagejgui.md"]
    
assessment: |
    ### Fill in the blanks
    
    - Given a 2D image with pixel height = pixel width = 0.13 micrometer. What is a distance of 147 pixels? __
    - What is the area covered by 10 pixels in micrometer square, given a spatial calibration of pixel height = pixel width = 0.13 micrometer? __
    
    > ## Solution
    >   - 147 * 0.13 = 19.11 micrometer
    >   - 10 * 0.13 * 0.13 = 0.169 micrometer square
    {: .solution}

learn_next:

external_links:

---

## Isotropy

One speaks of **isotropic sampling** if the pixels have the same extent in all dimensions (2D or 3D).

While microscopy images typically are isotropic in 2D they are typically **anisotropic** in 3D with coarser sampling in the z-direction. 

It is very convenient for image analysis if pixels are isotropic, thus one sometimes resamples the image during image analysis such that they become isotropic.
 
