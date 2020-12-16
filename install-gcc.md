First, add the ubuntu-toolchain-r/test PPA to your system with:

```
sudo apt install software-properties-common
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```
modify /etc/lsb-release with:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
```

Install the desired GCC and G++ versions by typing:
```
sudo apt install gcc-7 g++-7 gcc-8 g++-8 gcc-9 g++-9
```
The commands below will configure alternative for each version and associate a priority with it. The default version is the one with the highest priority, in our case that is gcc-9.
```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 90 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 80 --slave /usr/bin/g++ g++ /usr/bin/g++-8 --slave /usr/bin/gcov gcov /usr/bin/gcov-8
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 70 --slave /usr/bin/g++ g++ /usr/bin/g++-7 --slave /usr/bin/gcov gcov /usr/bin/gcov-7
```
Later if you want to change the default version use the update-alternatives command:
```
sudo update-alternatives --config gcc
```
There are 3 choices for the alternative gcc (providing /usr/bin/gcc).
```
  Selection    Path            Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-9   90        auto mode
  1            /usr/bin/gcc-7   70        manual mode
  2            /usr/bin/gcc-8   80        manual mode
  3            /usr/bin/gcc-9   90        manual mode
```
Press <enter> to keep the current choice[*], or type selection number:
You will be presented with a list of all installed GCC versions on your Ubuntu system. Enter the number of the version you want to be used as a default and press Enter.

The command will create symbolic links to the specific versions of GCC and G++.