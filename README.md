# Resize_Swap

Resize Swap to 8GB

# Turn swap off
# This moves stuff in swap to the main memory and might take several minutes
```
sudo swapoff -a
```
# Create an empty swapfile
# Note that "1G" is basically just the unit and count is an integer.
# Together, they define the size. In this case 8GB.
```
sudo dd if=/dev/zero of=/swapfile bs=1G count=8
```
# Set the correct permissions
```
sudo chmod 0600 /swapfile
```
# Set up a Linux swap area
```
sudo mkswap /swapfile
```
# Turn the swap on
```
sudo swapon /swapfile
 ```
 
Check if it worked
 ```
grep Swap /proc/meminfo
 ```
 
Make it permanent (persist on restarts)
Add this line to the end of your /etc/fstab:
 ```
/swapfile swap swap sw 0 0
```
