## PIV-analysis documentation

Particle Image Velocimetry (PIV) package developed in the Stramer Lab (King's College London, UK).

This analysis should be run on the output of PIV codes, which can be found [here](https://github.com/stemarcotti/PIV). Tested on MATLAB v2018B.

### Flow field quantification

Compute the average flow velocity from the interpolated PIV field with the script called **[flow_speed_quantification.m]**. If working with cell images for which the **[no_cb#\_m.tif]** is available, the output will ignore vectors for the cell body area (set to NaN as the image background). If the file **[no_cb#\_m.tif]** does not exist in the input folder, the output will be computed for the original entity in full.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
- output:
  + the mean flow velocity in [um/min] for each frame in the region of interest (e.g. cell): **[flow_speed_(ouput_name).mat]** (in folder [data])
  + the mean flow velocity in [um/min] across all frames in the region of interest (e.g. cell): **[flow_speed_average_(ouput_name).mat]** (in folder [data])

### Divergence field quantification

Compute the average divergence from the interpolated PIV field with the script called **[divergence_quantification.m]**. If working with cell images for which the **[no_cb#\_m.tif]** is available, the output will ignore vectors for the cell body area (set to NaN as the image background). If the file **[no_cb#\_m.tif]** does not exist in the input folder, the output will be computed for the original entity in full.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
- output:
  + the mean divergence in [A.U.] for each frame in the region of interest (e.g. cell): **[divergence_(ouput_name).mat]** (in folder [data])
  + the mean divergence in [A.U.] across all frames in the region of interest (e.g. cell): **[divergence_average_(ouput_name).mat]** (in folder [data])

### Actin Turnover field quantification

Compute the average tunrover from the interpolated PIV field with the script called **[actin_turnover_quantification.m]**. If working with cell images for which the **[no_cb#\_m.tif]** is available, the output will ignore vectors for the cell body area (set to NaN as the image background). If the file **[no_cb#\_m.tif]** does not exist in the input folder, the output will be computed for the original entity in full.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
- output:
  + the mean turnover in [A.U.] for each frame in the region of interest (e.g. cell): **[turnover_(ouput_name).mat]** (in folder [data])
  + the mean turnover in [A.U.] across all frames in the region of interest (e.g. cell): **[turnover_average_(ouput_name).mat]** (in folder [data])

### Divergence heatmap

Calculate divergence heatmap with the script called **[divergence_heatmap.m]**.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
  + the maximum convergence to be displayed in the heatmap [A.U.]
- output: this script returns the refined stack **[divergence_heatmap_(ouput_name).tif]** (in folder [images]) showing the negative divergence (convergence in arbitrary units) for each frame

### Principal Strain Rate heatmap

Calculate principal strain rate heatmap with the script called **[principal_strain_rate_heatmap.m]**.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
  + the maximum compression to be displayed in the heatmap [A.U.]
- output: this script returns the refined stack **[principal_strain_rate_heatmap_(ouput_name).tif]** (in folder [images]) showing the negative principal strain rate (compression in arbitrary units) for each frame

### Actin Turnover heatmap

Calculate actin turnover heatmap with the script called **[actin_turnover_heatmap.m]**.    
See [here](https://www.ncbi.nlm.nih.gov/pubmed/20485438) and [here](https://www.ncbi.nlm.nih.gov/pubmed/15210979) for references.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
  + the maximum disassembly to be displayed in the heatmap [A.U.]
- output: this script returns the refined stack **[actin_turnover_heatmap_(ouput_name).tif]** (in folder [images]) showing the negative actin turnover (disassembly in arbitrary units) for each frame

### Flow streamline analysis

Calculate streamlines for the flow tracked by PIV with the script called **[streamlines_plot.m]**.

- input requested to the user:
  + folder containing **[cb#\_m.tif]** and PIV output (e.g. _[cell1]_)
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
- output: this script returns the refined stacks **[streamlines_(ouput_name).tif]** and **[end_points_(ouput_name).tif]** (in folder [images]) and the file **[flow_streamlines_endpts_(output_name).mat]** (in folder [data]). The figures are not shown during the script run. The first stack shows in green the flow streamlines for each frame; the second stack shows with magenta dots the locations of streamline end points (saved in the .mat file), the dots size is proportional to the number of streamlines ending in a given location.

### Nucleus tracking

Obtain coordinates of the nucleus centroid at each frame with the script **[tracking.m]**. This script can be used to track any entity, provided that a masked stack of the object is passed as input.

- input requested to the user:
  + folder containing **[n#\_m.tif]** (e.g. _[cell1]_). The object to be tracked has to be masked in white (255) on a black background (0). This can be done in Fiji by opening the stack, setting a threshold and creating a mask from the threshold.
  + name for the output stamp to be appended to all saved output files (e.g. [output_name]: cell1); need to be the same assigned when running **[happy_piv.m]**!
  + the movie ID (# in **[cb#\_m.tif]**)
  + the pixel length in [um] as per the image calibration
- output: this script returns the file **[cell_tracking_(output_name).mat]** (in folder [data]) containing the object centroid coordinates in [um] for each frame
