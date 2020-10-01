# Abandoned Object Detection

<b>*Objective*</b>: To design a system to detect abandoned objects at busy regions like railway station, bus terminals etc.<br>

<b>*Methodology*</b>: <br>
 &emsp;• Background modeling and subtraction (BGS)<br>
&emsp;• Pre-processing<br>
&emsp;• Foreground analysis<br>
&emsp;• Blob extraction<br>
&emsp;• Blob tracking<br>
&emsp;• Abandonment analysis<br><br>

<div style="border-left: 5px solid black">
 
<ul><b>A. Background modeling and Subtraction (BGS):</b>
  <li>The first frame of the video is taken as the
  background.</li>
  <li>Performed YCbCr on the background and the
  current frame.</li>
  <li><b>Gaussian mixture model</b> is used to perform BGS. It assumes that the overall intensity at any pixel at each instant 
  is produced by a combination of background and foreground processes, and each such process can be modeled by a single Gaussian probability distribution function.</li></ul>
  
</div>

<ul><b>B. Pre-Processing:</b><br>
  Pre-Processing involves 2 functions:<br>
  <li>Contrast Enhancement: It improves the quality of low
  light video by normalizing the difference between the
  maximum & minimum intensities,
   using YCbCr approach. Convert RGB to YCbCr using
  <blockquote>vision.ColorSpaceConverter</blockquote>function. </li>
  <li>Noise Reduction: Reduces the white noise present in an input
  frame by smoothing the frame.</li></ul>
  
<ul><b>C. Foreground analysis:</b><br>
  <li>This system has a separate foreground analysis stage that takes the noisy foreground mask produced by the BGS module as its input and
  removes all the false and uninteresting foreground pixels
  from it. This can be done by <blockquote>NCC (Normalized Cross-Correlation)</blockquote></li> </ul>
 
 <ul><b>D. Blob extraction:</b><br>
  <li>The refined mask produced by the last step is
  subjected to a connected component detection
  function.</li>
  <li>This function i.e.
   <blockquote>
   [Area, Centroid, BBox] = step(hBlob, Segmented);
   </blockquote>
   gives area , centroid and
  Boundary box for a particular blob, discarding blobs
  that are smaller than a specified threshold.</li></ul>
 
<ul><b>E. Blob Tracking:</b><br>
   <li>First step involves comparison of incoming frame
  with the existing blobs.</li>
   <li>If the centroid position and size(criteria) of the blobs
  are in conformity, then the Hit Rate of that blob is
  increased by 1.</li>
   <li>If at any instant the criteria of the blobs are not in
  conformity, then its Hit Rate is set to 0.</li></ul>
  
<ul><b>F. Abandonment Analysis:</b><br>
 <li> Once the Hit Rate of any static Object exceeds
Abandoned Threshold, it is labeled as an abandoned
object.</li></ul>

Complete Report <a href='https://drive.google.com/file/d/1M_xfuzlLprGZ6rnUdkUr3ub277CstPjF/view?usp=sharing'>Here</a>
