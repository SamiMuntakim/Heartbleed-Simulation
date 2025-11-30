Heartbleed Vulnerability Simulation

A fully functional demonstration of the Heartbleed (CVE-2014-0160) flaw in the TLS heartbeat extension, showing how improper bounds checking leads to unintentional memory disclosure. This project recreates the vulnerability in a controlled environment for security education and analysis.

Overview

This simulation includes:

Vulnerable TLS Server

Built with pyOpenSSL

Implements the TLS heartbeat extension without performing proper payload length validation

Mimics the original Heartbleed bug by returning excess memory from the server process

Attacker Client

Connects to the vulnerable server over TLS

Sends an intentionally malformed heartbeat request

Extracts and prints leaked server memory

This project is strictly for educational and security-research purposes.

Setup Guide
1. Clone the Repository
git clone https://github.com/your/repo
cd heartbleed-simulation


If needed, delete the existing server.crt and server.key to generate fresh ones.

2. Install Dependencies

Ensure Python 3.x is installed, then run:

pip install pyOpenSSL

3. Generate a TLS Certificate

Create a self-signed certificate and private key:

openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout server.key -out server.crt


This provides the server with the minimal TLS setup required for the heartbeat exchange.

Running the Simulation
Step 1: Start the Vulnerable Server
python vulnerable_server.py


The server will begin listening for TLS connections and heartbeat messages.

Step 2: Launch the Attacker Client

In a second terminal:

python attacker_client.py


You will see raw memory bytes leaked from the server, replicating the core behavior of the Heartbleed vulnerability.
