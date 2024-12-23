# Log Analysis Challenge CTF

<h2>Description</h2>
In this Log Analysis challenge, I used carious filtering strategies to complete the challenge and find the potential user-agent string that returned a possible successful sql injection. 


<h2>Languages and Utilities Used</h2>

- <b>linux CLI</b>

<h2>Environments Used </h2>

- <b>Unbuntu</b> 

<br />
<br />
Challenge prompt.

![1) challenge prompt](https://github.com/user-attachments/assets/0e4936e5-3b74-459f-8d74-10e7b285dc98)

<br />
<br />
Word count and timestamp of last line in the challenge log. 

![2) q 1 2](https://github.com/user-attachments/assets/b11ac4c3-c336-4b6f-b24c-7d9ac355b8a7)

<br />
<br />  
Using "cut challenge -d " " -f 1 | sort | uniq -c | sort -nr | grep -v " 1 "" to filter out the top 3 unique ips in the log. 

![3) q 3 4](https://github.com/user-attachments/assets/94c6ba17-5824-453f-acf7-de3e0d64f2db)

<br />
<br />
Using "cut challenge.log -d "\"" -f 6 | sort | uniq -c | sort -nc" to filter out the top user-agent strings. I noticed "Widows" user-agent trying to spoof windows. 

![4) q5 6](https://github.com/user-attachments/assets/a6391e19-0930-4ec2-bb90-01430479856d)

<br />
<br />
Filtering fot he "widows" user-agent strings and running the last 3 entries into cyberchef to decode and doing some OSINT shows that this is a sql injectiona ttacking using the q URL parameter. 

![5) q8 9](https://github.com/user-attachments/assets/dbfa83b1-d16f-4899-8c79-17465787119b)

<br />
<br />
Filtering for the q paramter with the widows user-agent string shows the sql injection attempts with one responding with a differeny byte size than the rest indicating a potentially successfull attempt. 

![6) TIMESTAMP OF SUCCESSFUL sql bytes different than the failed ones](https://github.com/user-attachments/assets/73b02ab4-e9f1-4276-9e3d-5626049f7f90)

<br />
<br />
