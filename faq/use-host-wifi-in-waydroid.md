# Use WiFi network of your Computer in Waydroid

When waydroid is launched for the first time, you can see that there is **no internet connnection** although **your computer is connected to a _WiFi network_**.
In that case, it might be due to **some firewall restrictions** and here's how to fix that.

* Run `sudo firewall-cmd --zone=trusted --add-interface=waydroid0` in the terminal with **administrative privileges**.
* Run `sudo ufw allow 53` in the terminal with **administrative privileges**.
* Run `sudo ufw allow 67` in the terminal with **administrative privileges**.
* Run `sudo ufw default allow FORWARD` in the terminal with **administrative privileges**.
* Restart **waydroid container** with the below command:
  ```sh
  sudo waydroid container restart
  ```
