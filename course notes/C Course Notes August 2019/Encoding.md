# Encoding

Encoding

    File Extensions
    
    	.txt
    	.jpg
    
    		Rename myFile.txt to myFile.jpg what is it?  It's still a TEXT FILE.
    
    File Signatures
    
    	Pattern of 1's and 0's at the START OF A FILE WHEN IT'S LAID DOWN ON DISK 
    		(IE WRITTEN) WHICH INDICATES THE FILE TYPE.
    
    	File Signatures are PUBLICLY KNOWN
    
    		Drive Recovery Programs can SCAN THE DISK FOR KNOWN SIGNATURES IN ORDER
    		TO ATTEMPT TO RECREATE DELETED FILES 
    
    ASCII
    
    	USA built first computers ==> US English is default character set on Web.
    
    	7 bits ie numbers 0 through 127
    
    		(int)char will yield this number eg (int)'f'
    
    UTF8
    
    	0 added on end of ASCII
    
    	01010101 
    
    	Web is built using characters exclusively from UTF8 set

[https://getbootstrap.com/docs/4.3/getting-started/introduction/#starter-template](https://getbootstrap.com/docs/4.3/getting-started/introduction/#starter-template)[getbootstrap.com](http://getbootstrap.com/) ==> <meta charset="utf-8">

    BASE64 is therefore used to TRANSPORT ALL DATA WHICH IS NOT IN THIS SIMPLE
    		CHARACTER SET
    
    			<<complex data>>  ==>  chop it into blocks of 6 bit wide
    
    							  ==>  each 6-bit block allocated ASCII letter
    
    							  ==>  SEND DATA AS ASCII
    
    							  ==>  Process reversed at receiving end
    
    
    
    UTF16
    
    	Russian/Chinese languages etc have many characters
    	Using 16 bits we can now describe most characters in world.
    
    		ASCII 2^7 = 128
    		UTF16 => 2^16 ==> 65536 characters
    
    UNICODE = UTF16
    
    C# .NET default encoding is 16 bit      ((but .NET core defaulting ??? 8 bit ???))
    
    
    
    SecureString can be used as an input type which is slightly more secure than standard string.
    No strings are completely secure