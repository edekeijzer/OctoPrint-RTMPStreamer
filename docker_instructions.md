**Install docker**

    curl -sSL https://get.docker.com | sh
    sudo usermod pi -aG docker
    sudo reboot

    docker pull kolisko/rpi-ffmpeg:latest
	
**OctoPrint Settings**

- Enter your stream url used above in the OctoPrint-RTMPStreamer plugin settings.
- Change your webcam stream url to a fully quliafied url using the ip address of your pi like

    `http://127.0.0.1/webcam/?action=stream`
	
**SSH Prerequisites**

To connect over SSH, the paramiko library is needed. This has some dependencies of which the most recent versions are not available on [piwheels](https://www.piwheels.org/) so on Raspberry Pi you have to make sure all build dependencies are available _or_ install the available versions on your system:

```python -m pip install bcrypt=3.2.2 cryptography==38.0.1 paramiko==2.12.0```

Furthermore, you will need to:
- Have an SSH keypair or generate one
- Make sure the SSH keypair is added to the SSH agent when attempting to connect to Docker
- Allow the SSH key to control Docker on the server
- Connect via SSH to the server once from the account that's running OctoPrint to store the SSH host key in your known_hosts list