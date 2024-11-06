# To imports the necessary modules from the scapy.all library for ARP scanning.
# To import the time module to handle sleep time
# To import the datetime module to handle datatime snapshot.
from scapy.all import ARP, Ether, srp
from time import sleep
from datetime import datetime

# Function to scan the network for a specific IP
def scan_ip(ip_address):
    arp = ARP(pdst=ip_address)
    ether = Ether(dst="ff:ff:ff:ff:ff:ff")
    packet = ether / arp
    result = srp(packet, timeout=2, verbose=False)[0]

    # Check if any device responded
    return any(result)

# Function to log results to a file
def log_to_file(message):
    with open("network_monitor_log.txt", "a") as file:
        file.write(f"{datetime.now()} - {message}\n")

# Main function to monitor each IP in the range
def monitor_network(ip_start, ip_end):
    print("Starting network monitoring...")
    log_to_file("Network monitoring started.")
    try:
        # Main loop to monitor each IP address
        while True:
            for last_octet in range(ip_start, ip_end + 1):
                ip_address = f"192.168.1.{last_octet}"
                # Scan each IP address and log if it's found or not
                if scan_ip(ip_address):
                    log_to_file(f"Device with IP {ip_address} is connected to the network.")
                    print(f"Device with IP {ip_address} is connected to the network.")
                else:
                    log_to_file(f"Device with IP {ip_address} is not found on the network.")
                    print(f"Device with IP {ip_address} is not found on the network.")

            sleep(60)  # Wait for 60 seconds before the next scan cycle
    except KeyboardInterrupt:
        # Log the monitoring stop message on manual exit
        print("\nMonitoring stopped by user.")
        log_to_file("Network monitoring stopped by user.")
