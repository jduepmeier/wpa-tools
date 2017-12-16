## Helper scripts for wpa_spplicant

This repo contains scripts to easier use wpa_supplicant.

It contains the ```add_network``` script as helper to
create a wpa2 config file, the ```network``` script to
select networks, the init.d file and a systemd service file
for starting the wpa_supplicant daemon.

In the samples directory you can find examples for network configs.
Every config file can contain more than one network if you want.

The systemd service file is not tested. If you use it please let
me know if it works.

### Samples
The samples directory contains following examples:
* [empty.conf](samples/empty.conf) - File to clear all networks (i use it to disconnect from all networks).
* [wpa2.conf](samples/wpa2.conf) - File to connect to a wpa2 network.
* [open.conf](samples/open.conf) - File to connect to a open network.
* [ttls_pap.conf](samples/ttls_pap.conf) - Connect to a enterprise network.

### How it works

With the ```network``` script a config file can be selected.
The script searches in ```~/.wpa/``` for config files.
This config file will be copied to ```/tmp/wpa_supplicant.conf```.
After this the daemon will be reloaded using ```wpa_cli``` which
is part of the wpa_supplicant package.
