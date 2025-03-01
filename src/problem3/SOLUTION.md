Provide your solution here:
1) Memory leak in NGINX	
Step 1:  Check with commands:
htop or free -m

Step 2:  Check NGINX worker connections & limits:
sudo nano /etc/nginx/nginx.conf

worker_processes auto;
worker_connections 1024;
If worker_connections is too high for available RAM, lower it.

Step 3: Restart NGINX to clear memory:
sudo systemctl restart nginx

Step 4: Check logs
sudo tail -f /var/log/nginx/error.log

2) Memory Swapping

Step 1:  Check swap usage
swapon --summary

Step 2: Disable swap temporarily to free RAM
sudo swapoff -a

Step 3: Increase vm.swappiness
echo "vm.swappiness=10" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

Step 4: Restart the VM if necessary:
sudo reboot
