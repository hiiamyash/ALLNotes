#windows #active

![[Exported image 20241212232809-0.png|Exported image]]  
![[Exported image 20241212232811-1.png|Exported image]]  
![[Exported image 20241212232814-2.png|Exported image]]  
![[Exported image 20241212232816-3.png|Exported image]]  
![[Exported image 20241212232817-4.png|Exported image]]  
![[Exported image 20241212232823-5.png|Exported image]]  
![[Exported image 20241212232824-6.png|Exported image]]  
![[Exported image 20241212232827-7.png|Exported image]]  
![[Exported image 20241212232828-8.png|Exported image]]

<span style="color:rgb(133, 233, 145)">now you know looking at the aboce img that the minimum password is 7 so now you useee password spraying with weak passsworrds of 7 leanth</span>

![[Exported image 20241212232830-9.png|Exported image]]  
![[Exported image 20241212232832-10.png|Exported image]]  
![[Exported image 20241212232834-11.png|Exported image]]  
![[Exported image 20241212232840-12.png|Exported image]]  
![[Exported image 20241212232842-13.png|Exported image]]  
![[Exported image 20241212232844-14.png|Exported image]]  
![[Exported image 20241212232846-15.png|Exported image]]  
![[Exported image 20241212232847-16.png|Exported image]]  
![[Exported image 20241212232849-17.png|Exported image]]  
![[Exported image 20241212232850-18.png|Exported image]]  
![[Exported image 20241212232855-19.png|Exported image]]  
![[Exported image 20241212232857-20.png|Exported image]]  
![[Exported image 20241212232858-21.png|Exported image]]  
![[Exported image 20241212232900-22.png|Exported image]]  
![[Exported image 20241212232901-23.png|Exported image]]  
![[Exported image 20241212232903-24.png|Exported image]]  
![[Exported image 20241212232905-25.png|Exported image]]  
![[Exported image 20241212232909-26.png|Exported image]]  
![[Exported image 20241212232911-27.png|Exported image]]  
![[Exported image 20241212232912-28.png|Exported image]]  
![[Exported image 20241212232915-29.png|Exported image]]  
![[Exported image 20241212232916-30.png|Exported image]]  
![[Exported image 20241212232917-31.png|Exported image]]  
![[Exported image 20241212232919-32.png|Exported image]]  
![[Exported image 20241212232924-33.png|Exported image]]  
![[Exported image 20241212232927-34.png|Exported image]]  
![[Exported image 20241212232928-35.png|Exported image]]  
![[Exported image 20241212232929-36.png|Exported image]]  
![[Exported image 20241212232931-37.png|Exported image]]  
![[Exported image 20241212232932-38.png|Exported image]]  
![[Exported image 20241212232934-39.png|Exported image]]  
![[Exported image 20241212232939-40.png|Exported image]]  
![[Exported image 20241212232941-41.png|Exported image]]
in the above image you can see the THEPUNISHER has session of the domin admin account which can be used in the token impersanation atacks



```
powershell -ep bypass
Get-NetDomain
Get-NetDomainController

Get-NetUser | select cn
Get-DomainPolicy
(Get-DomainPolicy)."system access"

Get-UserPolicy 

Get-UserProperty -Properties pwdlastset
Get-NetComputer
Get-NetComputer -FullData
Get-NetComputer -FullData | select OperatingSystem
Get-NetGroup
Get-NetGroup -GroupName "Domain Admin"
Get-NetGroupMember -GroupName "Domains Admins"
Invoke-ShareFinder
Get-NetGPO
Get-NetGPO | select displayname, whenchanged
Invoke-Bloodhound -CollectionMethod ALL -Domain MARVEL.local -ZipFileName file.zip




```



