
# patched dmg from xpwn

Used for dual booting 32 bit ios devices - https://nyansatan.github.io/dualboot/


copy the xpwn folder from fixed include files to the system header location.  
linux - /usr/include  
mac os - /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include


```
mkdir build
cd build
cmake ..
make
```