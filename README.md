Assuming you have brew and brew cask installed on OS X you’ll need to install:
```
brew install socat screen
brew cask install xquartz
```

Then you can run XQuartz from the command line:
```
open -a XQuartz
```

socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\" &

```
docker build --tag x11 .
docker run --rm -e DISPLAY=192.168.65.1:0  x11 xeyes
```

In case the above command fails with `Error: Can't open display: 192.168.65.1:0` you’ll need to find a valid IP address using this voodoo:

```
screen ~/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux/tty
route | grep default | awk '{ print $2 }'
```
