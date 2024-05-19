# MipsPRO license warning suppressor for SGI Irix

## SGI MipsPRO compiler
The SGI MipsPRO compiler suite is no longer available for purchase or maintained. SGI made the compiler suite available but compiler commands displayed a warning message to purchase a license. Besides this warning, the compiler suite was completely functional.

## License warning suppression
`mipspro-suppress` is a wrapper for the SGI MipsPRO compilers that suppresses the license messages. That makes for much less screen output and allows to better see other, more important messages from the compiler.
This wrapper has the following advantages over other similar wrappers that I have seen:
- It doesn't suppress warning or error messages that are sometimes shown **before** the license message is displayed
- It shows all compiler ouptut
- It doesn't end with stdout and stderr swapped
- It returns compiler error codes properly
- It works whether you have flexlm configured or not

## Installation
Copy the file mipspro-suppress in a folder that will be in PATH before `/usr/bin/cc`. Then link this file to the compiler name that you wish to use. For example:

```
mkdir -p $HOME/bin
cp mipspro-suppress $HOME/bin
cd $HOME/bin
for i in CC OCC cc c89 c99 f77 f90 fort77; do
ln -s mipspro-suppress $i
done
export PATH=$HOME/bin:$PATH
``` 
 
 ## Notes on bash
 This wrapper requires a bash-specific feature and won't work with another shell. 
 
 If you see a delay between the end of the compilation and the display of error messages, uncomment the last 3 lines of the wrapper  

 ## Original license
For reference, here is the text of the original license message for SGI's cc compiler, suppressed by this wrapper. Other messages for CC, f77 etc. are similar except for the first two lines that indicate the compiler invoked.

```
 The MIPSpro C Compiler 
 (license FEATURE string = cc) 
 requires a license password. 

 For license installation and trouble shooting 
 information visit the web page: 

         http://www.sgi.com/Support/Licensing/install_docs.html 

 To obtain a Permanent license (proof of purchase
 required) or an Evaluation license please
 visit our license request web page: 

         http://www.sgi.com/support/licensing/

         or send a blank email message to: 

         license@sgi.com 

 In North America, Silicon Graphics' customers may request 
 Permanent licenses by sending a facsimile to: 

         (650) 932-0537 

         or by calling our technical support hotline 

         1-800-800-4SGI 

 If you are Outside of North America or you are not a Silicon 
 Graphics support customer then contact your local support provider. 
```

