# Data
This repository does **not** include imaging data, segmentations, or any patient-level information. The notebooks are shared for transparency and reproducibility. To rerun the analyses, you must provide your own local copies of the imaging and derived tables in the expected format.

## Imaging and segmentation format

### Images
Images were analysed as **.nrrd** volumes derived from the original DICOM series (conversion performed outside this repository using **3D slicer**). Each scan should have a corresponding `.nrrd` file.

### Segmentations
Segmentations were created in **3D Slicer**. Multiple ROIs can exist per scan and are stored as separate segments within a segmentation. When exporting, ensure the segmentation format you provide preserves the per-segment identity (for example, a labelmap with distinct integer labels per ROI, or individual masks per ROI). The notebooks assume that each ROI can be uniquely matched to a scan and an ROI identifier.

## Radiomics feature tables

Radiomic features were extracted using **PyRadiomics** from each ROI.

### One-row-per-ROI convention
The primary derived dataset used by the notebooks is a tabular feature file where:

- **One row corresponds to one ROI** (one segmented lesion/region).
- Columns include:
  - **Identifiers**: at minimum `scan_id`/`Scan_Name` and `roi_id`/`Segment Name` (and optionally `subject_id`, `cohort`, `reader`, `repeat_index`, etc.).
  - **Radiomic features**: numeric columns produced by PyRadiomics.
