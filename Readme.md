# MultiMedia Course

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
 And this curve explains the relationship between PSNR and bitRate

 ![image](https://user-images.githubusercontent.com/68567544/144230097-4ef88688-1eae-44a6-8a37-7c5a5729b30e.png)


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
  
And this curve explains the relationship between PSNR and bitRate
   
![image](https://user-images.githubusercontent.com/68567544/144230333-c332a94d-5f37-46ec-ae4f-cee451c53002.png)

Correlate the relation between video coding complexity and coding efficiency 
------

Observe the transcoding time, PSNR, and compressed video size for the following cases:
1. Vary Maximum CU size
2. Vary Maximum partitioning depth
3. Vary Motion estimation search range 

At first the maximum CU the range of the values for CU is **{16 ,32 ,64}**  and i used this command to do it : 

` ffmpeg -benchmark -i {Input_Viedo}.mp4 -c:v libx265 -x265-params ctu={Values_of_CU} -qp {Values_of_QP} {Output_Viedo}.mp4 -psnr `

After applying the command, I got the results in the tables below : 
<table>
<tr><th>CU 16</th><th>CU 32</th><th>CU 64</th></tr>
<tr><td>
  
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 82.71 | 21078.7     | 51.282 |
| 20 | 68.92 | 6589.37     | 45.315 |
| 30 | 51.7  | 2198.89     | 38.875 |
| 40 | 39.11 | 631.93      | 32.431 |
| 50 | 34.48 | 210.5       | 27.163 |
</td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 74.88 | 20579.04    | 51.297 |
| 20 | 62.82 | 6491.08     | 45.546 |
| 30 | 48.11 | 2082.98     | 39.06  |
| 40 | 34.66 | 510.78      | 32.738 |
| 50 | 28.78 | 111.85      | 27.33  |
  </td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 88.78 | 20539.29    | 51.219 |
| 20 | 84.14 | 6511.73     | 45.517 |
| 30 | 58.44 | 2078.23     | 39.199 |
| 40 | 38.07 | 485.96      | 33.021 |
| 50 | 30.06 | 80.27       | 27.65  |
  </td></tr>
  </table>
 This curve shows the relationship between the PSNR and the bit rate of the tables above
 
 ![image](https://user-images.githubusercontent.com/68567544/144232527-40d55d0e-ab3e-4377-9d4c-5cd1fbd7109e.png)
 
The same steps were applied to another 10-second video, and the results were as follows : 

<table>
<tr><th>CU 16</th><th>CU 32</th><th>CU 64</th></tr>
<tr><td>
  
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 13.04 | 456.63      | 63.43  |
| 20 | 16.32 | 260.38      | 54.607 |
| 30 | 17.93 | 160.31      | 47.716 |
| 40 | 19.38 | 121.98      | 41.324 |
| 50 | 14.78 | 108.74      | 34.666 |
</td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 18.62 | 379.12      | 63.4   |
| 20 | 27.59 | 191.91      | 55.004 |
| 30 | 28.41 | 92.16       | 48.194 |
| 40 | 25.49 | 53.61       | 41.927 |
| 50 | 22.12 | 41.79       | 35.818 |
  </td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 19.76 | 349.69      | 63.34  |
| 20 | 25.51 | 168.69      | 54.996 |
| 30 | 26.59 | 75.11       | 48.538 |
| 40 | 24.43 | 36.62       | 42.253 |
| 50 | 21.29 | 24.75       | 35.836 |
  </td></tr>
  </table>
This curve shows the relationship between the PSNR and the bit rate of the tables above

![image](https://user-images.githubusercontent.com/68567544/144232873-2da12b5a-97cf-449c-9dbf-7ac28ba60423.png)

 
Now partitioning depth , The range of values of dpth is **{1,2,3,4}** and this command was applied to get the results : 

`ffmpeg -benchmark -i  {Input_Viedo}.mp4 -c:v libx265 -x265-params tu-inter-depth={Depth}:tu-intra-depth={Depth} -qp {Value_of_QP} {Output_Viedo}.mp4 -psnr`

After applying the command, I got the results in the tables below : 

<table>
<tr><th>Depth 1</th><th>Depth 2</th><th>Depth 3</th><th>Depth 4</th></tr>
<tr><td>
  
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 84.66 | 20539.29    | 51.219 |
| 20 | 70.62 | 6511.73     | 45.517 |
| 30 | 54.24 | 2078.23     | 39.199 |
| 40 | 37.08 | 485.96      | 33.021 |
| 50 | 27.6  | 80.27       | 27.65  |
</td><td>

| QP | Time   | Rate (Kb/s) | PSNR   |
|----|--------|-------------|--------|
| 10 | 119.13 | 20099.44    | 51.372 |
| 20 | 93.75  | 6281.23     | 45.745 |
| 30 | 64.08  | 2133.11     | 39.525 |
| 40 | 41.31  | 513.75      | 33.199 |
| 50 | 25.75  | 81.3        | 27.633 |
  </td><td>

| QP | Time   | Rate (Kb/s) | PSNR   |
|----|--------|-------------|--------|
| 10 | 119.78 | 20020.98    | 51.356 |
| 20 | 94.12  | 6218.88     | 45.699 |
| 30 | 69.3   | 2094.58     | 39.352 |
| 40 | 44.45  | 497.68      | 32.688 |
| 50 | 26.75  | 81.16       | 27.571 |
  </td><td>
 
| QP | Time   | Rate (Kb/s) | PSNR   |
|----|--------|-------------|--------|
| 10 | 169.23 | 19950.4     | 51.346 |
| 20 | 136.93 | 6181.08     | 45.658 |
| 30 | 99.53  | 2060.4      | 39.115 |
| 40 | 60.28  | 463.29      | 31.856 |
| 50 | 41.55  | 81.11       | 27.449 |
  </td></tr>
  </table>
This curve shows the relationship between the PSNR and the bit rate of the tables above

![image](https://user-images.githubusercontent.com/68567544/144234060-38ec6cac-fd73-46fc-8e54-96431d230309.png)

The same steps were applied to another 10-second video, and the results were as follows : 

<table>
<tr><th>Depth 1</th><th>Depth 2</th><th>Depth 3</th><th>Depth 4</th></tr>
<tr><td>
  
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 19.99 | 349.69      | 63.34  |
| 20 | 28.29 | 168.69      | 54.996 |
| 30 | 28.26 | 75.11       | 48.538 |
| 40 | 27.24 | 36.62       | 42.253 |
| 50 | 23.34 | 24.75       | 35.836 |
</td><td>
 
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 24.56 | 338.45      | 63.755 |
| 20 | 29.58 | 167.04      | 55.323 |
| 30 | 32.18 | 74.06       | 48.691 |
| 40 | 29.69 | 36.64       | 42.394 |
| 50 | 24.21 | 24.89       | 35.964 |
  </td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 30.54 | 341.03      | 63.811 |
| 20 | 34.28 | 168.78      | 55.44  |
| 30 | 34.83 | 73.78       | 48.736 |
| 40 | 30.47 | 36.46       | 42.518 |
| 50 | 27.48 | 24.58       | 35.951 |
  </td><td>
 
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 38.42 | 340.92      | 63.828 |
| 20 | 45.29 | 168.34      | 55.365 |
| 30 | 44.73 | 73.42       | 48.753 |
| 40 | 43.89 | 36.49       | 42.531 |
| 50 | 37.79 | 24.64       | 35.898 |
  </td></tr>
  </table>
  
  This curve shows the relationship between the PSNR and the bit rate of the tables above
  
  ![image](https://user-images.githubusercontent.com/68567544/144234345-0efa96bb-18a7-4896-8adf-ce976f909181.png)

Finally the Motion , the range of motion is between **{0-32768}** and to get better results take the value **57** or the multiples so i take these values **{47,114,171}**
and use this command to got the result : 

`ffmpeg -benchmark -i  {Input_Viedo}.mp4 -c:v libx265 -x265-params merange={Values_of_motion} -qp {Values_of_QP} {Output_Viedo}.mp4 -psnr`

After applying the command, I got the results in the tables below : 

<table>
<tr><th>Motion 57</th><th>Motion 114</th><th>Motion 171</th></tr>
<tr><td>
  
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 92.96 | 20539.29    | 51.219 |
| 20 | 79.07 | 6511.73     | 45.517 |
| 30 | 62.26 | 2078.23     | 39.199 |
| 40 | 44.24 | 485.96      | 33.021 |
| 50 | 31.63 | 80.27       | 27.65  |
</td><td>
 
| QP | Time   | Rate (Kb/s) | PSNR   |
|----|--------|-------------|--------|
| 10 | 105.81 | 20547.05    | 51.219 |
| 20 | 85.29  | 6511.74     | 45.516 |
| 30 | 61.88  | 2078.34     | 39.206 |
| 40 | 38.68  | 486.59      | 33.018 |
| 50 | 29.12  | 80.63       | 27.646 |
  </td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 84.14 | 20545       | 51.219 |
| 20 | 69.27 | 6512.95     | 45.515 |
| 30 | 52.3  | 2077.71     | 39.202 |
| 40 | 36.19 | 485.56      | 33.019 |
| 50 | 25.34 | 80.42       | 27.653 |
  </td></tr>
  </table>
  
 This curve shows the relationship between the PSNR and the bit rate of the tables above
 
 ![image](https://user-images.githubusercontent.com/68567544/144235251-ce52b764-7695-4832-b582-484a25527ef5.png)

The same steps were applied to another 10-second video, and the results were as follows : 

<table>
<tr><th>Motion 57</th><th>Motion 114</th><th>Motion 171</th></tr>
<tr><td>
  
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 18.44 | 349.69      | 63.34  |
| 20 | 26.6  | 168.69      | 54.996 |
| 30 | 27.56 | 75.11       | 48.538 |
| 40 | 25.01 | 36.62       | 42.253 |
| 50 | 19.66 | 24.75       | 35.836 |
</td><td>
 
| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 41.72 | 349.21      | 63.35  |
| 20 | 41.05 | 168.33      | 55.006 |
| 30 | 41.95 | 74.32       | 48.53  |
| 40 | 38.23 | 36.17       | 42.255 |
| 50 | 34.09 | 24.6        | 35.791 |
  </td><td>

| QP | Time  | Rate (Kb/s) | PSNR   |
|----|-------|-------------|--------|
| 10 | 41.08 | 350.11      | 63.354 |
| 20 | 48.62 | 168.09      | 55.005 |
| 30 | 48.52 | 73.93       | 48.526 |
| 40 | 43.95 | 35.97       | 42.249 |
| 50 | 38.31 | 24.46       | 35.861 |
  </td></tr>
  </table>
This curve shows the relationship between the PSNR and the bit rate of the tables above

![image](https://user-images.githubusercontent.com/68567544/144235565-06c25346-8e3f-49c8-8480-cf158d1c1cbc.png)

