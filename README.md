
### Helper for ObjectScript Language Extensions
Creating your own commands or shortcut is one of the strongest features of ObjectScript    
If you create your own Language Extensions to Object you mostly have to find the  
proper %ZLANGC00 or %ZLANGV00 or %ZLANGF00 and add the extensions manually.  
    
A few utilities do it already automatically (ZPM, ZME, ..)   
This utility allows you to add your extensions also programmatically.    
- eg. at first run, or during installation    
I found this quite useful for my Docker-based demos as it all happens at start time.
 
This package includes a demo example to visualize the operation of this utility.

### Prerequisites
Make sure you have [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [Docker desktop](https://www.docker.com/products/docker-desktop) installed.

### Installation   
Clone/git pull the repo into any local directory
```
$ git clone https://github.com/rcemper/helper-for-objectscript-language-extensions.git
```
Open the terminal in this directory and run:
```
$ docker-compose build
```
Run the IRIS container with your project:
```
$ docker-compose up -d
```
### How to Use it
```
 ; typ = "C" ... command extentson
 ;       "F" ... function extension
 ;       "V" ... variable Extensin
 ; ext = name of the extension
 ; code (by ref) numbered array of lines to add
 ;  
 ; do cmd^zLangExtender(typ,ext,.code)   ;>> add extension 
```
### How to Test it
Open IRIS terminal:
```
$ docker-compose exec iris iris session iris   
USER>ZN "%SYS"   
%SYS>do ^zLangExample  
Compiling routine : %ZLANGF00.mac  
label="ZZDUMMY"   
line=6  
line(1)=" ; "   
line(2)=" ; just a demo dummy"  
line(3)="ZZDUMMY(%a) "    
line(4)=" quit " I got '"_%a_"' for test""   
line(5)=" ; what a nice demo "  
line(6)=" ; "   
sc=1   
typ="F"   
**** try ****  
sc=" I got 'hi folks' for test"    
result:
         ;Generated by %ZPM.PackageManager: Start
ZPM(pArgs...) Quit ##class(%ZPM.PackageManager).Shell(pArgs...)  
         ;Generated by %ZPM.PackageManager: End  
         ;  
         ; just a demo dummy  
ZZDUMMY(%a) 
         quit " I got '"_%a_"' for test"  
         ; what a nice demo
         ;
%SYS>   
```
And if you run it a second time ?    
It returns a standard error %Status.   
~~~
%SYS>do ^zLangExample
%objlasterror="0 ...ZZDUMMY^%ZLANGF00 already defined.........
label="ZZDUMMY"
line=6
line(1)=" ; "
line(2)=" ; just a demo dummy"
line(3)="ZZDUMMY(%a) "
line(4)=" quit " I got '"_%a_"' for test""
line(5)=" ; what a nice demo "
line(6)=" ; "
sc=""0 ...ZZDUMMY^%ZLANGF00 already defined.........
typ="F"
ERROR #5001: ZZDUMMY^%ZLANGF00 already defined
%SYS>
~~~

#### Warning
It is meant mainly for COS experts !  

[Article in DC](https://community.intersystems.com/post/helper-objectscript-language-extensions)    

[Video](https://youtu.be/_G2LYWxMIU0)    

[Online Demo](https://language-extender.demo.community.intersystems.com/csp/sys/UtilHome.csp)   
[Online Terminal](https://language-extender.demo.community.intersystems.com/terminal/)   
