

# HOWTO use this script

- Install your server and ensure you can ssh to it and that the ssh user can sudo.
- Copy sampleinventory.yaml to inventory.yaml and edit with your hosts info.
- Install ansible on the workstation where this project is checked out.
- Run: 

      ansible-playbook -i inventory.yaml home.yaml

- Homeassistant is now available at: http://your_host_ip:8123/  where your_host_ip is the one in inventory.yaml


# Docker cheat-sheet
- sudo docker container ls                           # List running containers
- sudo docker container logs -n 10 -f homeassistant  # Shows logs of homeassistant container
- sudo docker container logs -n 10 -f mosquitto      # Ditto for mosquitto container 
- sudo docker container logs -n 10 -f voltronic-mqtt # Ditto for voltronic-mqtt container
- sudo docker container exec -ti voltronic-mqtt bash # Get a root shell in voltronic-mqtt container
- sudo docker-compose -f /opt/home/docker-compose.yaml up --remove-orphans --force-recreate --detach   # (re)Starts all services
- sudo docker-compose -f /opt/home/docker-compose.yaml down                                            # Stops and removes all services


# References
Version of compose file used: https://github.com/docker/compose/issues/8251
Giving Voltronic-mqtt access to USB inside docker: https://stackoverflow.com/questions/24225647/docker-a-way-to-give-access-to-a-host-usb-or-serial-device#answer-66427245

# TODO
Naming the USB device: https://community.openhab.org/t/raspberry-pi-make-serial-usb-ports-persistent-via-symlinks/35847
Rotating logfiles (including /var/log/docker_tty.log).
