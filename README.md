# Archived: Docker now supports mounting the USB bus out of the box so this approach is unnecessary.

# adb-on-docker
This vagrant box contains docker>docker container with adb. It supports the mounting of Android devices connected to the host with USB. Modify the Vagrant file for the USB filer for working with your machine.

## Pre-Req:
1. Vagrant is installed on the machine.
2. virtualbox-extension-pack installed on the machine.

## Steps:
1. Clone repo 
 
 		git clone https://github.com/pr4bh4sh/adb-on-docker.git
2. Navigate to folder

	    cd adb-on-docker
3. Edit the **Vagrantfile** for the USB device you have.
4. Run 
	    
        vagrant up;vagrant provision
5. Login into the box 
    	
        vagrant ssh
6. Start the docker container 
    	
        docker run -d --privileged -v /dev/bus/usb:/dev/bus/usb --name adbd sorccu/adb
7. Now execute to check the device connectivity with the docker container 
    	
        docker run --rm -ti --net container:adbd sorccu/adb adb devices
    
## Thanks

@vbanthia @sorccu

## References
- https://github.com/vbanthia/appium-docker-test
- https://github.com/sorccu/docker-adb

    
