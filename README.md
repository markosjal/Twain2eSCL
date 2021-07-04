# Twain2eSCL a.k.a. Twain2AirScan

Use a Windows computer as a host to share a scanner with MacOS or Linux.

THIS PROJECT IS NOT COMPLETE AND IS IN DEVELPMENT

This project uses the following pre-built binaries

CmdTwain from http://www.gssezisoft.com/ (web site down as of this writing)

BonJour Print Services for Windows https://support.apple.com/kb/dl999?locale=en_US

PHP for Windows https://windows.php.net/download/

Java for Windows https://www.java.com/download/ie_manual.jsp

As far as I can tell this should work in Windows 7, through Windows 10, so even an older Windows computer with your scanner driver installed may work. 

Also, it should work for users that rely on drivers from VueScan, as VueScan provides a TWAIN interface with their built in scanner drivers.

This means it should work with a wide gamut of scanners , even older ones. 


Clients can be: 


Mac OS with built in driverless scanning
Linux with either the eSCL driver bundled with newer versions of SANE or the separate Airscan driver https://github.com/alexpevzner/sane-airscan


Current Limitations (aside from code not yet complete)
I have found no way to accurately auto-populate the features available from the scanner's TWAIN interface to the eSCL interface. This must be done manually by editing scannerconfig.conf. There are also some settings/preferences not inherited from the scanner that you can set in scanningconfig.php.

I have been using  exclusively the built in PHP Development server to test this which is working fine. From my experience, Apache may need a fair amout of tweaking to get it to behave correcly. The problem with this is that it is running from a command prompt at start up. Not being a Windows guru, I am  not sure if it can be run as a service.

Much like the aforementioned probllem I also must run dns-sd.jar (from Apple Bonjour) from a Windows commmand prompt resulting in yet another unwanted window.


#How to: (using PHP Development Server)

give your Windows host a fixed IP address (heretofore your fixed IP  is referred to as <IPAADDRESS>, and set its hostname to a known value <HOSTNAME>.

  
  Install PHP

  Install Java

  
  Install Bonjour

  Install CmdTwain

  Download this project ZIP

  Copy fies in this project ZIP to C:\html
  
  Start PHP Development server 
  cd C:\html
  php -S <IPADDRESS>:8000
  
  Set options in
  C:\scannerconfig.php (refer to scanners TWAIIN interface)
  C:\scannigconfig.php
  
  Start Bonjour
  cd C:\Program Files (x86)\Bonjour
  dns-sd -R <HOSTNAME> _uscan._tcp local 8000


  Connect with Linux or Mac OS client
  
