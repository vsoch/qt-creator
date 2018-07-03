# QT-Creator Docker

This image is derived from [erstrom/qt](https://github.com/erstrom/docker-qt). We first
[build the image](build) and put it on Docker Hub as [vanessa/qt-creator:base](https://hub.docker.com/r/vanessa/qt-creator/), and then [add to it](Dockerfile) additional
dependencies, including download of test files for compilationu. Usage is discussed below.


## Start the Container
We need to start the container and run priviledged to bind the display

```bash
docker run -it \
	--privileged \
	-v /tmp/.X11-unix:/tmp/.X11-unix \
	-e DISPLAY=$DISPLAY \
	--name qt-sh \
	vanessa/qt-creator
```

If you want to bind a folder with projects, etc., don't forget to do that!

```bash
docker run -it \
	--privileged \
        -v $PWD:/home/user/projects \
	-v /tmp/.X11-unix:/tmp/.X11-unix \
	-e DISPLAY=$DISPLAY \
	--name qt-sh \
	vanessa/qt-creator
```

The container is now running, and the command above will shell you inside. You won't need to start it again. If you need to stop and remove it, you should do this.

```bash
docker stop qt-sh
docker rm qt-sh
```

## Start Qt Creator
We are in the container as user "user" and the working directory is `/qt`. I 
changed directory to $HOME where I could see the project folder, and then
started qtcreator. We are (somewhat) following the instructions [here](http://web.stanford.edu/dept/cs_edu/qt-creator/qt-creator-linux.shtml).

```bash
cd $HOME
qtcreator
```

Once in Qt-creator:
 - click Open Project
 - Leave the defaults, click Open
 - Control+B will build (takes about 30 seconds)
 - Pressing the green arrow will Run the script.

You should see a smiley face and message that it ran successfully. Good job!

![img/success.png](img/success.png)
