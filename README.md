## CREDITS
* Forked from https://github.com/hackenfreude/docker-tlatoolbox-1.5.2
* Leslie Lamport for [his work](http://research.microsoft.com/en-us/um/people/lamport/tla/papers.html) on TLA+... and [lots of other things](https://en.wikipedia.org/wiki/Leslie_Lamport). 
* [Jess Frazelle](https://github.com/jfrazelle) for [containers on the deskop](https://blog.jessfraz.com/post/docker-containers-on-the-desktop/).

## WHAT DOES THIS DO?
This is a container that runs the TLA+ Toolbox.

## WHY?
* TLA+ Toolbox requires Java.
	* Who wants to install Java?
* TLA+ is neat... you should keep reading!
* Impress your friends by running a GUI application in Docker.

## WHAT IS TLA+?
_"TLA+ is especially well suited for writing high-level specifications of concurrent and distributed systems."_ ([source](http://research.microsoft.com/en-us/um/people/lamport/tla/tla-intro.html))

## HOW DO I LEARN MORE?
Visit [The TLA Home Page](http://research.microsoft.com/en-us/um/people/lamport/tla/tla.html).

## HOW TO RUN IT?
1. Make sure you're on a system running [X](https://en.wikipedia.org/wiki/X_Window_System).
2. Disable X access control (don't do this on a public-facing machine): `$ xhost +`
3. `$ cd` to a path where you want to write some .tla files.
4. ``$ docker run -d -v /tmp/.X11-unix:/tmp/.X11-unix -v `pwd`:`pwd` -e DISPLAY=$DISPLAY kimada/tlatoolbox:1.7.1-latest``
5. You should see the TLA+ splash screen and eventually the TLA Toolbox.
6. Use the TLA Toolbox menu: File/Open Spec/Add New Spec.
7. Enter /root/specs/{foo}.tla as the root-module name. The specification name should auto-complete to {foo}. Click Finish.
8. Have fun. Write some specifications. Close the TLA+ Toolbox when you're done, and the container will shut down. Your files will be in the path on the host where you started.
9. __Reenable X access control:__ `$ xhost -`

## WHAT JUST HAPPENED?
* Docker mounted the host's X socket in the continer as the container's X socket; this allows the container's GUI to pass back up to the host.
* Docker mounted the host's working directory in the container at the same path.

## WHAT IF IT DOESN'T WORK?
Open an [issue](https://github.com/keikun555/docker-tlatoolbox/issues).
