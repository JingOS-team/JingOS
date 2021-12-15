#[Guide] Flatpak App - Install and use Flatpak

Flatpak (https://docs.flatpak.org/en/latest/using-flatpak.html) is a free (as in fully open source) alternative to Snap packages.
First of all, with jingos 1.0 the ca-certificates are out of date, you need to update them by downloading the last version:
- http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates/

Download the last deb file (the "..**all**.deb" one:
`ca-certificates_202XYYZZ_all.deb`
Install it:
```
cd ~/Downloads
sudo dpkg -i ca-certificates_202XYYZZ_all.deb
```

Then, **install Flatpak**:
`sudo apt-get install flatpak`

Now Flatpak is installed, but is not configured:
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
Then you can proceed, by searching for something, in my example I'm looking for "Fluffy Chat":
```
flatpak search FluffyChat
```
and then installing it:
```
sudo flatpak install FluffyChat
```
This will install the binary and its dependencies!

then, check what is installed:
```
flatpak list --app
```

and run it:
```
flatpak run the.id.found.in.list
```
...Unfortunately flatpaks are broken too ATM, they fail with the following issue:
```
bwrap: Can't mount proc on /newroot/proc: Device or resource busy
```
..But one day, maybe...

written and thus under the responsability of bboett
