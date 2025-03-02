# Secure Private Messaging System Using STM32F103 and W5500

## In an era where digital privacy is constantly threatened, our project offers a truly secure and low-level encrypted messaging system. By utilizing the STM32F103 microcontroller, W5500 Ethernet module, and a simple HID keyboard, we create a direct, encrypted communication channel between identical devices.

Why is this system secure?
	1.	Hardware-Level Encryption Initialization
Before using the system, each user must manually input an interruption vector for SHA-256 encryption using the connected keyboard. This vector serves as a unique key known only to the user and is not stored anywhere within the system, making external breaches virtually impossible.
	2.	No Third-Party Servers or Cloud Involvement
Unlike conventional messaging apps that rely on internet-based services, our system operates on a direct peer-to-peer Ethernet connection. This means no external servers can intercept or store messages.
	3.	Unique Session-Based Encryption
Each session requires the user to set up a unique SHA-256 encryption vector, ensuring that even if an attacker gains access to the system, previous messages cannot be decrypted.
	4.	Custom Communication Protocol
The messaging protocol is implemented at a very low level, avoiding standard protocols like TCP/IP that could be vulnerable to packet sniffing. This makes it extremely difficult for an attacker to analyze network traffic and extract meaningful data.
	5.	Limited Attack Surface
	•	The system is designed to be minimalistic, removing unnecessary software layers that could introduce vulnerabilities.
	•	It does not rely on an OS or external APIs, reducing exposure to malware or exploits.
	•	No wireless communication (e.g., Wi-Fi or Bluetooth), preventing remote attacks.

How It Works
	1.	User Setup
	•	Connect the HID keyboard.
	•	Input the custom SHA-256 interruption vector (not stored, only used in RAM).
	•	Configure the destination IP and port of the target device.
	2.	Sending a Message
	•	The system encrypts the message using SHA-256 hashing with the user-defined vector.
	•	The encrypted message is sent via Ethernet using the W5500 module.
	3.	Receiving & Decryption
	•	The recipient device receives the encrypted message.
	•	If the same interruption vector is manually entered, the message is decrypted successfully.
	•	If the incorrect vector is used, the message remains unreadable.

Why is it Impossible to Decrypt?
	•	No stored encryption keys: Each session requires a manually entered vector, meaning even if a device is captured, past messages cannot be retrieved.
	•	Custom communication protocol: Without knowing the exact system architecture, attackers cannot decipher the encryption method or data structure.
	•	SHA-256 strength: Even with brute force, SHA-256 remains computationally infeasible to break.

Conclusion

This project is perfect for individuals or organizations needing absolute privacy in communications. Whether for personal security, journalistic protection, or sensitive military applications, our STM32F103-based system ensures that messages remain confidential and beyond the reach of any third-party eavesdropping.
