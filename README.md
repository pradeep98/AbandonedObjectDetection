# AbandonedObjectDetection

<b>*Objective*</b>: To design a system to detect abandoned objects at busy regions like railway station, bus terminals etc.<br>

<b>*Methodology*</b>: <br>
 &emsp;• Background modeling and subtraction (BGS)<br>
&emsp;• Pre-processing<br>
&emsp;• Foreground analysis<br>
&emsp;• Blob extraction<br>
&emsp;• Blob tracking<br>
&emsp;• Abandonment analysis<br><br>

<b>A. Background modeling and Subtraction (BGS):</b><br>
  &emsp;• The first frame of the video is taken as the
  background.<br>
  &emsp;• Performed YCbCr on the background and the
  current frame.<br>
  &emsp;• <b>Gaussian mixture model</b> is used to perform BGS. It assumes that the overall intensity at any pixel at each instant <br>
  &emsp;is produced by a combination of background and foreground processes, and each such process can be modeled<br> by a single Gaussian probability distribution function.<br>

<b>B. Pre-Processing:</b><br>
  &emsp;Pre-Processing involves 2 functions:<br>
  &emsp;• Contrast Enhancement: It improves the quality of low
  light video by normalizing the difference between the
  <br> &emsp; maximum & minimum intensities,
   using YCbCr approach. Convert RGB to YCbCr using<br> &emsp;
  “vision.ColorSpaceConverter” function.<br>
  &emsp;• Noise Reduction: Reduces the white noise present in an input
  frame by smoothing the frame.<br>
  
<b>C. Foreground analysis:</b><br>
  &emsp;This system has a separate foreground analysis stage that takes the noisy foreground mask produced by the BGS <br> &emsp;module as its input and
  removes all the false and uninteresting foreground pixels
  from it.<br>&emsp; This can be done by NCC (Normalized Cross-Correlation) <br>
 
 <b>D. Blob extraction:</b><br>
  &emsp;• The refined mask produced by the last step is
  subjected to a connected component detection
  function.<br>
  &emsp;• This function i.e. [Area, Centroid, BBox] =
  step(hBlob, Segmented); gives area , centroid and
  Boundary box for a <br> &emsp; particular blob, discarding blobs
  that are smaller than a specified threshold.
 
<b>E. Blob Tracking:</b><br>
   &emsp;• First step involves comparison of incoming frame
  with the existing blobs.<br>
   &emsp;• If the centroid position and size(criteria) of the blobs
  are in conformity, then the Hit Rate of that blob is
  increased by <br> &emsp;1.<br>
   &emsp;• If at any instant the criteria of the blobs are not in
  conformity, then its Hit Rate is set to 0.<br>
  
<b>F. Abandonment Analysis:</b><br>
 &emsp;• Once the Hit Rate of any static Object exceeds
Abandoned Threshold, it is labeled as an abandoned
object.<br>

Complete Report <a href='https://drive.google.com/file/d/1M_xfuzlLprGZ6rnUdkUr3ub277CstPjF/view?usp=sharing'>Here</a>
