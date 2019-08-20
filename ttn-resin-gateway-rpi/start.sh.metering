#!/bin/bash

# Start the node exporter
mkdir /mnt/ramdisk && mount -t tmpfs -o size=8m tmpfs /mnt/ramdisk
cd /mnt/ramdisk
/opt/ttn-gateway/run.py &

# WORKAROUND: Add symlink, as gwexporter otherwise currently don't seem to find this file
ln -s /mnt/ramdisk/loragwstat.json /opt/gwexporter/loragwstat.json

export PATH=$PATH:/opt/gwexporter/bin
node /opt/gwexporter/gwexporter.js &

cd /etc && ./node_exporter --web.listen-address ":81"
