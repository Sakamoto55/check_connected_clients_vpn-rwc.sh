#!/bin/bash

#This script will check the users connected to vpn-rwc. It will also caution if connected user count is too high


users=$(vpncmd localhost /server  /hub:care2hub /cmd sessionlist | grep -v “Secure”|grep "User Name"|awk '{print $NF}'|cut -b 2-)
user_count=$(vpncmd localhost /server  /hub:care2hub /cmd sessionlist | grep -v “Secure”|grep "User Name"|awk '{print $NF}'|cut -b 2-|wc -l)

echo "$users"
echo "USER COUNT = $user_count"



if [ "$user_count" -le 5 ]

        then

        exit 0

elif [ "$user_count" -gt 5 && -le 10 ]

        then

        exit 1
else

        exit 2
fi
