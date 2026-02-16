# RouterOS Scripts

These are scripts that we have found useful in managing our large mikrotik infrastructure.

This script was not written by us but found on the net and is really useful:

   * auto-sys-restore - described in more detail on our [webpage](https://hamwan.org/Labs/auto-sys-restore%20Script.html).
     It provides an alternative to safe mode, when it can't be used. Available at:
     https://github.com/mikrotik-user/auto-sys-restore

## HamWAN developed scripts

   * check_ap - this script checks that a station which can see multiple APs with the same SSID is connected to the preferred AP.
     It is described in more detail on our website: [https://hamwan.org/Labs/Check_AP%20Script.html]
   * update-address-list - this script updates a list in /ip/firewall/address-list without removing and re-adding. Its adds missing entries and removes obsolete entries.
     This allows us to centrally manage firewall address lists on our edge routers.

## Installing Scripts

Installing scripts by cut and paste is problematic. Installing as part of a script (.rsc) file also has problems.
I have found the following procedure is the easiest
If you were trying to install the update-address-list.script as update-mylist, you should follow the following process:

   * upload update-address-list.script to your router. WinBox upload or scp are easiest, but ```/tool fetch``` can also be used.
     For example: ```scp update-address-list.script myrouter.example.com:```.
   * ```/system script add name=update-mylist source=[/file get update-address-list.script contents]```
   * If needed, edit the script configuration:
     ```/system script edit [find name=update-mylist] source```.
