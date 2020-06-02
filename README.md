## Vehicle Speed Detection & License Recognition

### Vehicle Detection
<ul>
<li>It uses Haar Cascade Classifier to detect vehicles in the every nth frame.</li>
<li>It removes unnecessary portion from the image to speed up processing.</li>
<li>Two reference lines have been set, one for vehicle entry and one for exit.</li>
<li>When any vehicle in any lane crosses the entry point, the time is recorded, and the vehicle is tracked.</li>
<li>Tracking is done using centroid tracking Techniques.</li>
<li>Time is recorded when the vehicles crosses the exit line.</li>
<li>Based on the time difference, the vehicles speed is estimated.</li>
</ul>

If a vehicle crosses the set speed limit, license recognition function is executed.

### License Recognition
<h4>How It Works?</h4>
<ol>
<li>Load the original image.</li>
<li>Grayscale it.</li>
<li>Blur it using bilateral filter.</li>
<li>Automatically generate its canny image basd on median value of pixels.</li>
<li>Find all contours.</li>
<li>Remove contours having small perimeter.</li>
<li>take convex hull of all remaining contours.</li>
<li>For each convex hull, do the following:</li>
<ul><li>Take its approxpolydp.</li>
<li>Try to approximate it as a quadrilateral.</li>
<li>If quadrilateral, check if it's almost a parallelogram</li>
<li>If almost parallelogram, check if the ratio of width/height is similar to a license plate.</li>
<li>Take only those convex hulls which satisfy these conditions.</li></ul>
<li>Do a perspective transform of the convex hulls.</li>
<li>Loop over each convex hull, and try to recognize its text.</li>
<li>The convex hull with the longest text is our license plate.</li>
<li>And the text is our license number.</li>
<ol>
