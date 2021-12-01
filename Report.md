# MultiMedia Course
Thie Repository for multi media course 2021

Compare coding efficiency of various video compression standards
------
Produce the rate-PSNR (rate-distortion) curves for the following video compression standards: 
1.  AVC/H.264
2. HEVC/H.265

For AVC/H.264 use this command with differen QP then save it

`ffmpeg -i {Input_Viedo}.mp4 -c:v libx264 -qp {Value_of_QP} {Output_Viedo}.mp4 -psnr `

Then take the result and put in the table , table below show the result with 10 diff. QP **{10,20,25,30,35,40,45,47,49,50}**

`Note the Range of QP is from 1 to 51 `
 
 
<table>
<tr><th>For Viedo 1 with 8 sec </th><th>For Viedo 2 with 10 sec</th></tr>
<tr><td>
  
| QP   | Rate (Kb/s) | PSNR   |                               
|----|-------------|--------|
| 10 | 99638.7     | 51.395 |
| 20 | 18413       | 46.12  |
| 25 | 8137.07     | 43.686 |
| 30 | 3970.21     | 40.93  |
| 35 | 2295.7      | 38.192 |
| 40 | 1763.57     | 35.567 |
| 45 | 1387.89     | 32.768 |
| 47 | 1159.5      | 31.552 |
| 49 | 891.41      | 30.326 |
| 50 | 744.92      | 29.49  |
</td><td>

| QP | Rate (Kb/s) | PSNR   |
|----|-------------|--------|
| 10 | 18067.86    | 51.906 |
| 20 | 5624.13     | 45.878 |
| 25 | 3426.91     | 43.027 |
| 30 | 2187.34     | 39.694 |
| 35 | 1329.81     | 35.967 |
| 40 | 766.1       | 32.589 |
| 45 | 454.51      | 29.649 |
| 47 | 373.56      | 28.54  |
| 49 | 306.39      | 27.504 |
| 50 | 276.16      | 26.943 |
  </td></tr>
  </table>

> As we see when the QP increases the PSNR will decrease and the rate also decrease which mean the resolution of video will decrease

the same step to apply AVC/H.265 use this command with differen QP then save it :

`ffmpeg -i {Input_Viedo}.mp4 -c:v libx265 -qp {Value_of_QP} {Output_Viedo}.mp4 -psnr `

Tables below shown the results : 

<table>
<tr><th>For Viedo 1 with 8 sec </th><th>For Viedo 2 with 10 sec</th></tr>
<tr><td>
  
| QP | Rate (Kb/s) | PSNR   |
|----|-------------|--------|
| 10 | 96645.42    | 51.398 |
| 20 | 13654.05    | 46.605 |
| 25 | 4950.46     | 44.292 |
| 30 | 1867.6      | 41.973 |
| 35 | 842.48      | 39.484 |
| 40 | 425.14      | 37.013 |
| 45 | 227.3       | 34.726 |
| 47 | 184.66      | 33.929 |
| 49 | 156.75      | 33.205 |
| 50 | 148.07      | 32.773 |
 </td><td>


| QP | Rate (Kb/s) | PSNR   |
|----|-------------|--------|
| 10 | 20539.29    | 51.219 |
| 20 | 6511.73     | 45.517 |
| 25 | 3763.41     | 42.384 |
| 30 | 2078.23     | 39.199 |
| 35 | 1052.38     | 36.011 |
| 40 | 485.96      | 33.021 |
| 45 | 195.41      | 30.158 |
| 47 | 134.09      | 29.084 |
| 49 | 93.09       | 28.077 |
| 50 | 80.27       | 27.65  |
  </td></tr>
  </table>

