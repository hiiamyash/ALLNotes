#networking #basics

![[../../../../../attchments/Exported image 20241212230901-0.png|Exported image]]

Netmask is also is know as subnet mask

![[../../../../../attchments/Exported image 20241212230903-1.png|Exported image]]

8 bits are turened off so 2**8 are the number of hosts  
The amount od host you can have depends on the subnet mask

![[../../../../../attchments/Exported image 20241212230907-2.png|Exported image]]

It /24 because 8 bits are turned off

![[../../../../../attchments/Exported image 20241212230911-3.png|Exported image]]

First you add 128 and 64you get 192 then you start adding diagnally 192+32+224 ,,224+16=240

![[../../../../../attchments/Exported image 20241212230913-4.png|Exported image]]   
How to calculate the subnet mask  
For explame /1 so in this 31 bits are turened off only 1 is on so subnet mask will be 128.0.0.0  
For explame /14 in this 18 bist are turned off and 14 are on  
So subnet mask will be 255.252.0.0

![[../../../../../attchments/Exported image 20241212230918-5.png|Exported image]]

First 8 bits will be 255 and rest 6 bits will be 252

![[../../../../../attchments/Exported image 20241212230921-6.png|Exported image]]  
![[../../../../../attchments/Exported image 20241212230924-7.png|Exported image]]  
![[../../../../../attchments/Exported image 20241212230926-8.png|Exported image]]  
![[../../../../../attchments/Exported image 20241212230929-9.png|Exported image]]