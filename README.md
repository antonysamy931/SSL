# SSL
How to create certificate in Windows:

Self signed certificate:

1. Open visual studio command prompt in administrative.
2. makecert.exe used to create a self signed security certificate.
   pvk2pfx.exe used to create personal information exchange certificate.

   ex :	Make local directory for store certificate. Navigate to maked folder.
   
   --------------------------
   create security certificate
   --------------------------
   makecert -r -pe -n "CN=First certificate creation" first.cer -sv first.pvk -a sha512 -sky exchange -b 01/01/2015 -e 01/01/2050
   press enter 
   first.cer and first.pvk file created inside that folder
   -----------------------------------
   create personal infomation exchange
   -----------------------------------
   pvk2pfx -pvk first.pvk -spc first.cer -pfx first.pfx -po password
   press enter
   first.pfx file created inside created folder
		
3. Open run and type mmc -> file -> add or remove snap in -> left panel select certificate and add
4. Personal -> certificate -> import certificate to certificate folder
5. Trusted roots certifications authority -> certificate -> import certificate


Integrate with IIs secure website.

1. Fist import the certificate to iis.
	Open Inetmgr -> Home -> Server Certificates double click -> Right side action panel click Import -> Select your created .pfx file and give to your pfx password then click ok	
2. Create new website -> bindings -> add -> https -> ssl certificate -> select your imported certificate.
