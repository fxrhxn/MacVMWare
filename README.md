# MacVMWare
Creating a virtual computer using El Capitan OSX.


## Part 1 - Install OSX El Capitan, 

1) Go into Apples App Store, and go to Downloads. Find the OSX, and download it again.

2) Your final download should appear in Applications, and look like --- 'Install OS X El Capitan.app'. DO NOT CLICK ON IT.


## Part 2 - Run these alphabetical code snippets in Terminal. 
### The purpose of these snippets are to get a .iso image for use in VirtualBox. 


a)
hdiutil attach "/Applications/Install OS X El Capitan.app/Contents/SharedSupport/InstallESD.dmg" -noverify -nobrowse -mountpoint /Volumes/esd

b)
hdiutil create -o ElCapitan3 -size 7316m -layout SPUD -fs HFS+J


c)
hdiutil attach ElCapitan3.dmg -noverify -nobrowse -mountpoint /Volumes/iso


d)
asr restore -source /Volumes/esd/BaseSystem.dmg -target /Volumes/iso -noprompt -noverify -erase


e)
rm /Volumes/OS\ X\ Base\ System/System/Installation/Packages


f)
cp -rp /Volumes/esd/Packages /Volumes/OS\ X\ Base\ System/System/Installation


g)
cp -rp /Volumes/esd/BaseSystem.chunklist /Volumes/OS\ X\ Base\ System/


h)
cp -rp /Volumes/esd/BaseSystem.dmg /Volumes/OS\ X\ Base\ System/


i)
hdiutil detach /Volumes/esd


j)
hdiutil detach /Volumes/OS\ X\ Base\ System


k)
hdiutil convert ElCapitan3.dmg -format UDTO -o ElCapitan3.iso


l)
mv ElCapitan3.iso.cdr ElCapitan3.iso

