# [Guide] Install Flutter

## Flutter on the JingPad

Flutter is a cross platfrom framework, based on the dart language, that one day will permit to compile/run also flutter apps on the JingPad, as soon as the problems with the OpenGL library are fixed....

### Installation

its easy, just clone the directory:
```
git clone https://github.com/flutter/flutter.git
```
then you need to adjust in your bashrc, supposing you cloned the flutter stuff directly into your $HOME:
```
export  PATH=$PATH:~/flutter/bin:$HOME/.pub-cache/bin # adding the flutter binary and the binaries of your projects to exe path
export CHROME_EXECUTABLE=chromium-browser #to be able to create web apps
```
the latter is needed if you want to dev webapps with flutter...
then source the bashrc or open a new shell (you are running with screen or something like that, aren't you?)
and check if the dart exe is found:
```
which dart
```
    
then check the flutter install:
```
flutter doctor
```

### creating a dart app

to create a new dart project:
```
dart create my_new_awesome_project
cd my_new_awesome_project
dart run -d linux
```

ATM  plain dart stuff runs well, which can be enough (i often design my apps as command line apps, with a separate, optional graphical UI).
dart has a name convention of small caps only, no Java style camelcase! use underscores as separators!

To change the default app, you have to look into bin/main.dart and into lib.


### creating a flutter app

to create a new flutter project:
```
flutter create my_new_awesome_project
cd my_new_awesome_project
flutter run -d linux
```

UI stuff has a (big) caveat:

if you run into a blank screen (which will probably happen), and on the console something like:

```
Launching lib/main.dart on Linux in debug mode...
Building Linux application...
** (<your_app_name>:2084): WARNING **: 11:17:47.183: Failed to start Flutter renderer: No GL implementation is available
** (<your_app_name>:2084): WARNING **: 11:30:20.700: Unable to retrieve framework response: No engine to send to
```
please

```
unset LD_LIBRARY_PATH
```
that will remove libhybris from LD_LIBRARY_PATH and Flutter will (slowly) run with MESA LLVMpipe SW rendering
(thanks to Taepi!) 

### installing from the pub.dev repositories

e.g. stagehand was a nice module that creates all relevant files for a dart project, just for example sake, 
you can "install" pub.dev modules for easy execution:

```
dart pub global activate stagehand
```

which will be placed in your .pub-cache/bin, as long as that is in your path, just  type:
```
stagehand
```
will execute the binary!
otherwise you have to cd into the dir of the project and:
```
dart run bin/stagehand
```


### compiling the executables

for better performance don't forget at all waypoints of your code to offer a fast and really usable user experience by 
precompiling the dart binary (speedup at least x 10!)

with 
```
dart compile exe bin/myapp.dart -o bin/runme
```

and off you go dev'ing!
written and thus under the responsability of bboett
