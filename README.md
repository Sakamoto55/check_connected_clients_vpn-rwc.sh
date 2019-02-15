#check_connected_clients_vpn-rwc.sh
#This script will check the users connected to vpn-rwc. It will also caution if connected user count is too high
#!/bin/bash

 STATE_OK=0
 STATE_WARNING=1
 STATE_CRITICAL=2
 STATE_UNKNOWN=3

 connected_users=$(/cdusr/bin/vpncmd localhost /server  /hub:care2hub /cmd statusget|grep "Status"|tail -1|cut -b 31-)

 if [[ "$status" == "Online" ]]

  then

    echo "VPN Server up"
    exit 0

  else

    echo  "VPN Server down"
    exit 2
 fi
