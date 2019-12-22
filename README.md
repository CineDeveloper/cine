<body>
Cine - compiler for cine programming language.<br>
In order to start working with the cine language, you need to follow the <a href="https://github.com/CineDeveloper/cineAndFei-installer">link</a> and follow the instructions to install cine and fei.
Currently available only for Linux x86_64.<br>
<br>
Here is an example of creating a simple cine application.<br>
<br>
Create the folder named &quot;line&quot;.<br>
Open a terminal in the created folder.<br>
Run the following command in the terminal:<br>
<code><b>fei new line-cine</b></code><br><br>
In the folder you created, several files and folders will appear. Open the main.cine file and delete it's contents.
Write the following code in the open file (indentation should consist only of spaces, the number of which should be a multiple of 4):<br>
<pre style='color:#0057ae;background-color:#fcfcfc;'>
<code>
<b><span style='color:#1f1c1b;'>type</span></b><span style='color:#1f1c1b;'> </span>Point<span style='color:#1f1c1b;'>(a)</span>
<span style='color:#1f1c1b;'>    x, y a</span>

<b><span style='color:#1f1c1b;'>type</span></b><span style='color:#1f1c1b;'> </span>Line<span style='color:#1f1c1b;'>(a)</span>
<span style='color:#1f1c1b;'>    a, b a</span>

<b><span style='color:#1f1c1b;'>func</span></b><span style='color:#1f1c1b;'> getLength(line)</span>
<b><span style='color:#1f1c1b;'>    rules</span></b>
<span style='color:#b08000;'>        final</span><span style='color:#1f1c1b;'> = line == </span>Line<span style='color:#1f1c1b;'>(_) &amp; line[</span><span style='color:#b08000;'>0</span><span style='color:#1f1c1b;'>][</span><span style='color:#b08000;'>0</span><span style='color:#1f1c1b;'>] &gt; </span>BasicFloat
<b><span style='color:#644a9b;'>        result</span></b><span style='color:#1f1c1b;'> = line[</span><span style='color:#b08000;'>0</span><span style='color:#1f1c1b;'>][</span><span style='color:#b08000;'>0</span><span style='color:#1f1c1b;'>]</span>
<span style='color:#1f1c1b;'>    deltaX .= line.a.x - line.b.x</span>
<span style='color:#1f1c1b;'>    deltaY .= line.a.y - line.b.y</span>
<span style='color:#1f1c1b;'>    </span><b><span style='color:#644a9b;'>result</span></b><span style='color:#1f1c1b;'> = (deltaX * deltaX + deltaY * deltaY).sqrt()</span>

<b><span style='color:#1f1c1b;'>func</span></b><span style='color:#1f1c1b;'> getCoordinateFromSTDIN(coordinateType)</span>
<b><span style='color:#1f1c1b;'>    rules</span></b>
<span style='color:#b08000;'>        final</span><span style='color:#1f1c1b;'> = coordinateType &gt; </span>BasicFloat
<b><span style='color:#644a9b;'>        result</span></b><span style='color:#1f1c1b;'> = coordinateType</span>
<span style='color:#1f1c1b;'>    </span><b><span style='color:#1f1c1b;'>for</span></b>
<span style='color:#1f1c1b;'>        lineFromSTDIN .= getLineFromSTDIN()</span>
<span style='color:#1f1c1b;'>        </span><b><span style='color:#1f1c1b;'>if</span></b><span style='color:#1f1c1b;'> lineFromSTDIN == </span><span style='color:#bf0303;'>&quot;&quot;</span>
<span style='color:#1f1c1b;'>            </span><b><span style='color:#1f1c1b;'>then</span></b><span style='color:#1f1c1b;'> exit()</span>
<span style='color:#1f1c1b;'>        </span><b><span style='color:#1f1c1b;'>if</span></b><span style='color:#1f1c1b;'> xBox .= #coordinateType.fromString(lineFromSTDIN); xBox.item?()</span>
<span style='color:#1f1c1b;'>            </span><b><span style='color:#1f1c1b;'>then</span></b>
<span style='color:#1f1c1b;'>                </span><b><span style='color:#644a9b;'>result</span></b><span style='color:#1f1c1b;'> = xBox[]</span>
<span style='color:#1f1c1b;'>                </span><b><span style='color:#1f1c1b;'>break</span></b>
<span style='color:#1f1c1b;'>            </span><b><span style='color:#1f1c1b;'>else</span></b><span style='color:#1f1c1b;'> print(lineFromSTDIN, </span><span style='color:#bf0303;'>&quot; - is not a valid float number. Please try again:</span><span style='color:#3daee9;'>\n</span><span style='color:#bf0303;'>&quot;</span><span style='color:#1f1c1b;'>)</span>

<b><span style='color:#1f1c1b;'>proc</span></b><span style='color:#1f1c1b;'> main()</span>
<span style='color:#1f1c1b;'>    </span><b><span style='color:#1f1c1b;'>for</span></b>
<span style='color:#1f1c1b;'>        line := </span>Line<span style='color:#1f1c1b;'>(</span>Point<span style='color:#1f1c1b;'>(</span>Double<span style='color:#1f1c1b;'>))</span>
<span style='color:#1f1c1b;'>        print(</span><span style='color:#bf0303;'>&quot;Enter the coordinates of the points (press enter to exit):</span><span style='color:#3daee9;'>\n</span><span style='color:#bf0303;'>&quot;</span><span style='color:#1f1c1b;'>)</span>
<span style='color:#1f1c1b;'>        print(</span><span style='color:#bf0303;'>&quot;    The x coordinate of the first point:</span><span style='color:#3daee9;'>\n</span><span style='color:#bf0303;'>&quot;</span><span style='color:#1f1c1b;'>)</span>
<span style='color:#1f1c1b;'>        line:a:x = </span>Double<span style='color:#1f1c1b;'>.getCoordinateFromSTDIN()</span>
<span style='color:#1f1c1b;'>        print(</span><span style='color:#bf0303;'>&quot;    The y coordinate of the first point:</span><span style='color:#3daee9;'>\n</span><span style='color:#bf0303;'>&quot;</span><span style='color:#1f1c1b;'>)</span>
<span style='color:#1f1c1b;'>        line:a:y = </span>Double<span style='color:#1f1c1b;'>.getCoordinateFromSTDIN()</span>
<span style='color:#1f1c1b;'>        print(</span><span style='color:#bf0303;'>&quot;    The x coordinate of the second point:</span><span style='color:#3daee9;'>\n</span><span style='color:#bf0303;'>&quot;</span><span style='color:#1f1c1b;'>)</span>
<span style='color:#1f1c1b;'>        line:b:x = </span>Double<span style='color:#1f1c1b;'>.getCoordinateFromSTDIN()</span>
<span style='color:#1f1c1b;'>        print(</span><span style='color:#bf0303;'>&quot;    The y coordinate of the second point:</span><span style='color:#3daee9;'>\n</span><span style='color:#bf0303;'>&quot;</span><span style='color:#1f1c1b;'>)</span>
<span style='color:#1f1c1b;'>        line:b:y = </span>Double<span style='color:#1f1c1b;'>.getCoordinateFromSTDIN()</span>
<span style='color:#1f1c1b;'>        printLn(</span><span style='color:#bf0303;'>&quot;line length - &quot;</span><span style='color:#1f1c1b;'>, line.getLength())</span>
</code>
</pre>
Return to the terminal and execute the following commands in turn:<br>
<code><b>fei build</b></code><br>
<code><b>sudo fei install pkgs/release.fpkg</b></code><br><br>
To start the program, execute in the terminal:<br>
<code><b>line-cine</b></code><br><br>
To remove the program, execute in the terminal:<br>
<code><b>sudo rm -f /usr/bin/line-cine</b></code><br><br>
<span style='color:#ff0000;'>IMPORTANT!!!</span> If you remove the program, do it very carefully. Since the r and f keys are near and if you accidentally type -rf instead of -f and accidentally put a space after bin, the command will ruin the system.
</body>
