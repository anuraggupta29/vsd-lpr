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
<ol>
<li> On recieving the image it grayscales it.</li>
<li>Blurs it using bilateral filter.</li>
<li>Automatically generates its canny image based on median value of pixels.</li>
<li>Finds all contours.</li>
<li>Removes contours having small perimeter.</li>
<li>takes convex hull of all remaining contours.</li>
<li>For each convex hull, does the following:</li>
<ul><li>Takes its approxpolydp.</li>
<li>Tries to approximate it as a quadrilateral.</li>
<li>If quadrilateral, checks if it's almost a parallelogram</li>
<li>If almost parallelogram, checks if the ratio of width/height is similar to a license plate.</li>
<li>Takes only those convex hulls which satisfy these conditions.</li></ul>
<li>Does a perspective transform of the convex hulls.</li>
<li>Loops over each convex hull, and tries to recognize its text.</li>
<li>The convex hull with the longest text is our license plate.</li>
<li>And the text is our license number.</li>
<li>Displays the car image and license image and the license text</li>
</ol>
  
The execution of the program pauses after every detection, and resumes again once the user closes the car image window and license image window.
 
##### This program requires the following python libraries to function:
opencv, dlib, imutils, numpy, pytesseract (tesseract ocr should also be installed)
