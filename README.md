Download Link: https://assignmentchef.com/product/solved-comp273-assignment-3-image-manipulation-exercises
<br>
We will be going through some fun image manipulation exercises in this one, developing some tools for your image processing toolbox. You may notice that FILE I/O will receive no partial marks. The reason for this is that every following question depends on FILE I/O functioning.

<ul>

 <li>Make sure to follow conventions! beyond just readability and consistency between developers, the conventions also help developers avoid hours of debugging. If you have questions about conventions/debugging, feel free to ask any of the TAs.</li>

 <li>Even if your code does not produce the right image, make it produce something!</li>

 <li>You will receive a 0 on the question if the code does not compile.</li>

 <li>We will be using our own input files during grading, but the general structure is pretty straight forward.</li>

 <li>Do not change any labels in the templates. You may add whatever extra labels you may need, but use the ones provided as intended.</li>

 <li>Make sure you read all the questions first. Though some things you can get away with by hard coding, this isn’t the case for all questions. Certain things (like moving through a 2D matrix) are necessary in multiple questions, for example, and avoiding hard coding might save time in the long run!</li>

 <li>File I/O is the only part of the assignment that requires error checking.</li>

</ul>

-MARS uses relative paths to find images. This means, if you have Mars in the same folder as your .txt and scripts, then the paths specified in the templates will work accordingly.

<ul>

 <li>GIMP is an image editing software. Though you can use anything you’d like, its software that can be used to view the .pgm file after generating the image is complete. https://www.gimp.org/</li>

 <li>headers for .pgm files have a specific format.</li>

</ul>

<em>P</em>2(which is grayscale)

<em>width height </em>## (max value) http://netpbm.sourceforge.net/doc/pgm.html contains more information about proper .pgm formatting. We’re concerned with PLAIN pgm, so we will assume that there are no comment lines in the pgm file.

<ul>

 <li>You may use as many sub routines as you like! I.E. They must not be called from the main function.</li>

 <li>You may add any extra .data you like, but make sure its after the specified line. The data specified in the templates should be used accordingly.</li>

 <li>1           FILE I/O (15 marks) No partial marks</li>

</ul>

(10 marks) The template for this question is provided in fileio.asm

<ul>

 <li>Using the template <em>asm </em>as a starting point, write a MIPS procedure <em>readfile </em>that takes as its argument the address of a string that contains a valid filename, and then uses appropriate syscalls to read from that input file and then simply prints the content of that file to the screen. In the template there are two input files called test1.txt and test2.txt which you should test. To accomplish this task we allow you to create a large buffer, i.e., one that is larger than the expected number of ASCII characters (bytes) in the input file. The body of your code should work by calling the procedure you have written. The procedure should open the file, read its content as ASCII characters, store the content in the buffer, print the content to the screen, and then close the file. For your reference a more complete set of MIPS syscalls implemented in MARS, along with clear documentation on how to use each, is here: <a href="http://courses.missouristate.edu/kenvollmar/mars/help/syscallhelp.html">http://courses.missouristate.edu/kenvollmar/mars/help/syscallhelp.html</a><a href="http://courses.missouristate.edu/kenvollmar/mars/help/syscallhelp.html">.</a></li>

 <li>We shall now build on the above example. Following the process of reading the file <em>txt</em>, after which the ASCII characters have been read into the buffer, we shall call a second MIPS procedure called <em>writefile</em>. This procedure should open a file called <em>copy.pgm</em>, should then write the following information to that file:</li>

</ul>

P2

24 7

15

Then it should write out the content that was read into the buffer. It should then close the file.

***(5 marks)Error statements should be printed if there are any errors in opening the file.

If things are working properly when you view <em>copy.pgm </em>with a suitable image viewer, e.g., gimp, you should see something interesting.

<h1>2           Flip Image</h1>

<ol>

 <li>Template: flipper.asm</li>

 <li>Read the data in <em>txt </em>into the specified buffer.</li>

 <li>The data read into the buffer should now be converted to consecutive integers and then stored in a 2D array of length 24×7, i.e., one that has 24 columns and 7 rows. However that 2D array will actually be represented as a 1D array*. Finally, take care to convert the entries in the buffer (which are in ASCII) to their numerical values in base 10.</li>

 <li>Write a procedure named <em>flip</em>.</li>

 <li>Argument structure outlined in template.</li>

</ol>

* Normally, in a language like Java, we would simply specify the respective array positions of i and j. That is, we would let i represent the row we are currently at, and j represent the column we are currently at. In MIPS, however, our 2D array is stored as values in a 1D array. It is clear to see that for any position [i,j] in our 2D array, we can retrieve this position by simple computing ( i * width ) + j. Since i represents rows, whenever we add a width (for this assignment, width is 24) we are essentially going to the next row in our conceptual 2D array. j simply represents which column we are currently looking at.

<h1>3           Transpose Image</h1>

<ol>

 <li>The template for this question is provided in <em>asm</em>.</li>

 <li>Read the data in <em>txt </em>into the specified buffer.</li>

 <li>The data read into the buffer should now be converted to consecutive integers and then stored in a 2D array of length 24×7, i.e., one that has 24 columns and 7 rows. However that 2D array will actually be represented as a 1D array*. Finally, take care to convert the entries in the buffer (which are in ASCII) to their numerical values in base 10.</li>

 <li>Write a procedure named <em>transpose</em>. This routine will take your image buffer, and apply the matrix operation transpose to it (where position (i,j) in a matrix is now at position (j,i).</li>

 <li>The content of the output 2D array should then be written into a file named <em>pgm</em>.</li>

 <li>The header will be changed! update your writefile routine to work accordingly.

  <ul>

   <li>THIS CAN ONLY BE VIEWED if you have properly implemented (a). This means that you are expected to write the information as you did in 1(b) and THEN write the completed output 2D array to <em>pgm</em>.</li>

   <li>TESTING: You can assume that all .txt files we may use for this question use the same header as specified in b).</li>

  </ul></li>

</ol>

<h1>4           Crop Image</h1>

<ol>

 <li>Template: <em>asm</em></li>

 <li>You are given <em>x</em>1<em>,y</em>1<em>,x</em>2<em>,y</em>2, and a <em>txt </em>file.</li>

 <li>Read the data in <em>txt </em>into the specified buffer.</li>

 <li>Generate a new .pgm named <em>pgm </em>that contains a cropped version of the image information contained in <em>test.txt</em>, i.e., reading it into an array and then cropping the rectangular portion bounded by <em>x</em>1<em>,y</em>1<em>,x</em>2<em>,y</em>2.</li>

 <li>Make sure that the cropped.pgm has the correct header! Otherwise, the cropped image won’t be displayed properly.</li>

 <li>Make sure to use P2 for “plain pgm” and 15 for the max intensity (last term from the header in part 1 b). This means the only values that change are those specifying the dimensions of your image. Therefore, the header must not be hard coded for this question. This extension should be added to your write function.</li>

 <li>TESTING: you can expect that all test.txt files that are tested will start with the same header as part 1, and that x1,y1,x2,y2 will be valid inputs, i.e., they will be within the bounds of the original array.</li>

</ol>

<h1>5           Add Image Border</h1>

<ol>

 <li>Template: border.asm</li>

 <li>Read the data in <em>txt </em>into the specified buffer.</li>

 <li>In a routine called <em>bord</em>, given <em>borderWidth </em>(a pixel width), take your <em>txt </em>image and produce a new <em>borded.pgm </em>image with a borderwidth equal to the pixels.</li>

 <li>The border will be white (=15). You can assume P2 and 15 here as well.</li>

 <li>TESTING: you can expect that all test.txt files that are tested will start with the same header as part 1.</li>

</ol>