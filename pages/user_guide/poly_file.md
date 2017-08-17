---
title: Defining connectivity in bonded systems
folder: user_guide
permalink: poly_file.html
---

        <h2>poly_file: Defining connectivity in bonded systems</h2>
<p>
The polymer connectivity file can have any name and is set in dft_input.dat in the <a href="UG_sect7.html">polymer input section</a>.  It is needed whenever <a href="UG_sect3.html">Type_poly</a> is turned on.
This file simply identifies the
architecture of the chains by defining the number of bonds at each segment, i, as well
as the ij bond pairs (all j segments bonded to i).  This file also identifies
symmetries in the chain so that redundant equations may be removed from the system
of equations.  The order of entry for parameters in the poly_file must be
(segID_i, Nbond, sets of {segID_j, symbond_j}). So, if a given segment is bonded to three other segments, there will be 8 entries in the row.
More specifically, the parameters are:<p>

<ul>
<li><b>segID_i</b>(int): 
The ith 
segment number on a given polymer component.  Note that in a blend, this number will begin at 0 for <u>each</u> of the polymer components.  </li>
<li><b>Nbond</b>(int):   Number of bonds associated with a given segment on a given polymer component.  Note that the exception is for end beads on 
a chain where we include one additional virtual bond per end.  For a single site species set Nbond=2.</li>
<li><b>segID_j</b>(int): Segment ID for the jth segment to which the ith segment is bonded.  Note that to flag the end of
a chain, set the seg_ID_j values to -1.  If a single site species is included there should be 2 bonds, both with both
segID_j values set to -1.  For grafted polymers, set the segID_j value of the segment that is grafted to the surface to -2.</li>
<li><b>symbond_j</b>(int): Identify a bond as identical to another bond in the system (by virtue of symmetry of the polymer
architecture).  Enter the bond id number for the symmetric bond rather than -1 in this field.  
Enter -1 if a bond is to be included independently.  This parameter may always be turned off by setting all values to -1, but will result
in some redundant calculations.
</li>

<p> An example of a star polymer with 4 arms is shown here </p>
<p>0 2 -1 -1 1 -1 </p>
<p>1 2  0 -1 2 -1</p>
<p>2 2  1 -1 3 -1</p>
<p>3 2  2 -1 4 -1</p>
<p>4 4  3 -1 5 -1 9 -1 13 -1</p>
<p>5 2 4  7  6  6</p>
<p>6 2 5  5  7  4</p>
<p>7 2 6  3  8  2</p>
<p>8 2 7  1 -1  0</p>
<p>9 2 4   7 10  6</p>
<p>10 2 9   5 11  4</p>
<p>11 2 10  3 12  2</p>
<p>12 2 11  1 -1  0</p>
<p>13 2 4   7 14   6</p>
<p>14 2 13  5 15  4</p>
<p>15 2 14  3 16  2</p>
<p>16 2 15  1 -1  0</p>

</ul>

***

<a href="http://www.sandia.gov/general/privacy-security/index.html">Privacy and Security</a> 