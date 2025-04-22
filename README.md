# SIMPLE-REAL-TIME-IP-TRACKER
# __**The script's primary function is to perform real-time monitoring of the local network's IP address range. When the user's IP address is detected as connected to the owner's WiFi network, the script will send data logs and save them for analysis purposes.**__

The code imports the necessary modules from the scapy.all library for ARP scanning, as well as the sleep function from the time module and the datetime class from the datetime module.

The scan_ip function creates an ARP packet targeting the specified IP address and an Ethernet frame with a broadcast MAC address. It then sends the packet using the srp function from scapy.all and checks if any device responded to the ARP request.

The log_to_file function writes a message with a timestamp to a file named network_monitor_log.txt. This file will be used to store the results of the network monitoring.

The monitor_network function is the main function that performs the network monitoring. It loops through the IP addresses in the specified range (from ip_start to ip_end) and calls the scan_ip function for each IP address. If a device is found, it logs the message to the file and prints it to the console. If a device is not found, it logs and prints the corresponding message.

The function also includes a 60-second delay between each scan cycle to avoid excessive network traffic.

The monitor_network function is called with the range 0 to 100, which corresponds to the IP addresses 10.0.0.0 to 10.0.0.254 or 10.0.0./24.

The code includes a try-except block to handle a manual stop of the monitoring process using the keyboard interrupt (Ctrl+C).
