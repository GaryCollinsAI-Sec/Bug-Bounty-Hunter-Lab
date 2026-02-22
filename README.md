#Bug Bounty Lab

<h2>Objective</h2>
<p>
Build a locally isolated network environment using pfSense as a virtual gateway to manage and monitor offensive security traffic between a Kali Linux attacking machine and a DVWA target.
</p>

<hr>

<h2>Skills Learned</h2>
<ul>
<li>Network architecture and segmentation.</li>
<li>Firewall rule configuration and traffic logging.</li>
<li>Web vulnerability exploitation (SQLi, XSS, etc.).</li>
<li>DHCP server administration and static IP mapping.</li>
<li>Analyzing attack patterns through real-time firewall logs.</li>
<li>Hardening network boundaries against unauthorized lateral movement.</li>
<li>Secure lab isolation and air-gapping.</li>
</ul>

<hr>

<h2>Tools Used</h2>
<ul>
<li><strong>pfSense:</strong> Virtual router and security appliance.</li>
<li><strong>Kali Linux:</strong> Primary platform for penetration testing tools.</li>
<li><strong>DVWA:</strong> Damn Vulnerable Web App (Target).</li>
</ul>

<hr>

<h2>Steps</h2>

<h3>1. Network Configuration</h3>
<ul>
<li><strong>Hypervisor Setup:</strong> Create an internal network segment (e.g., Lab-Net) in your virtualization software.</li>
<li><strong>pfSense Adapters:</strong>
<ul>
<li>Adapter 1 (WAN): NAT (to allow initial updates).</li>
<li>Adapter 2 (LAN): Assigned to Lab-Net.</li>
</ul>
</li>
<li><strong>Client Adapters:</strong> Set both Kali Linux and DVWA network interfaces exclusively to Lab-Net.</li>
</ul>

<h3>2. pfSense Interface Setup</h3>
<ul>
<li>Boot pfSense and assign interfaces via the console (e.g., vtnet0 for WAN, vtnet1 for LAN).</li>
<li>Configure the LAN IP Address.</li>
<li>Enable the DHCP Server on the LAN to automate IP assignment for the lab machines.</li>
</ul>

<h3>3. Target &amp; Attacker Deployment</h3>
<ul>
<li>Start DVWA and verify it receives a LAN IP from the pfSense DHCP pool.</li>
<li>Boot Kali Linux and access the pfSense WebGUI.</li>
<li>Configure Static DHCP Mappings for the DVWA machine to maintain a consistent attack target.</li>
</ul>

<h3>4. Security Policy &amp; Monitoring</h3>
<ul>
<li>Define Firewall Rules in pfSense to monitor or restrict traffic between the attacker and target.</li>
<li>Enable Packet Logging on the LAN interface to capture and analyze attack signatures.</li>
<li>Disable WAN outbound traffic for the DVWA host to ensure a strictly air-gapped environment.</li>
</ul>

<h3>5. Verification &amp; Testing</h3>
<ul>
<li>Perform a connectivity check (Ping/Nmap) from Kali to the DVWA IP.</li>
<li>Access the DVWA web interface via the browser in Kali.</li>
<li>Initialize the MariaDB database within the DVWA setup page to begin hunting.</li>
</ul>
