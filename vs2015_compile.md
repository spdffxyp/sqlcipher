# compile and run in windows with vs2015
## from:

https://www.domstamand.com/compiling-sqlcipher-sqlite-encrypted-for-windows-using-visual-studio-2022/

## download and install:
https://slproweb.com/download/Win64OpenSSL-3_3_1.exe
https://www.irontcl.com/downloads/irontcl-amd64-8.6.7.zip


## make:
```shell
cmd /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"

"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" x64

SET PATH=%PATH%;C:\Programs\IronTcl\bin

SET PLATFORM=x64

cd D:\xxx\sqlcipher-4.5.7

nmake /f Makefile.msc
```

## run:
```shell
sqlite3.exe
  
sqlite> .open 'MSG0.db'
  
sqlite> PRAGMA key = "h'your_hex_key'";
```
### set pragma:
```
sqlite> PRAGMA cipher_compatibility = wx;
```
#### or:
```
sqlite> PRAGMA page_size = 4096;
  
sqlite> PRAGMA cipher_kdf_algorithm = PBKDF2_HMAC_SHA1;
  
sqlite> PRAGMA kdf_iter = 64000;
  
sqlite> PRAGMA cipher_hmac_algorithm = HMAC_SHA1;
```
### then:
```
sqlite> SELECT COUNT(*) FROM sqlite_master;
```
