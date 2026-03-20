# Linux-Commands-User-Management-Lab
# Lab Title: User Management in Linux

You are a cybersecurity analyst for SecureNet Corp, a mid-sized enterprise that recently faced a network intrusion. The attacker exploited Bring Your Own Device (BYOD) policies to connect an unauthorized device to the corporate network. 

**Objective**
1. **Identity & Access Management (IAM):** Create a dedicated security group and assign members to it.
2. **Bash Scripting:** Develop a network discovery tool (`testsweep.sh`) to ping a specified subnet and log active IP addresses.
3. **File Permissions:** Enforce strict access controls using `chmod` and `chown` to prevent unauthorized users from viewing, modifying, or executing the script.

**Tools Used**
* **Operating System:** Kali Linux Virtual Machine System
* **Commands:** `ping`, `grep`, `cut`, `tr`, `chmod`, `chown`, `adduser`, `groupadd`, `usermod`, `su`
* **Concepts:** Network Discovery, Linux File Permissions (Octal), IAM, Output Redirection

# Part 1: Security Group Setup
1. **Created the security group**
   
   `sudo groupadd security `

2. **Created users: alice_sec, bob_sec, carol_sec**
   
   `sudo adduser alice_sec`

   `sudo adduser bob_sec`

   `sudo adduser carol_sec`

4. **Added Users to the Security Group**
   
   `sudo usermod -aG security alice_sec`

   `sudo usermod -aG security bob_sec`

   `sudo usermod -aG security carol_sec`

6. **Set Up the Shared Directory**
   
   `sudo mkdir -p /home/shared/security`

# Part 2: Network Sweep Script
1. **Added the Script File- testsweep.sh**
   
   `sudo mousepad /home/shared/security/testsweep.sh`

2. **Wrote the Script Code**
   
  

3. **Verified the Script File is in the Group**

   `ls /home/shared/security`

4. **Ownership and Permissions - Group members only**
   
   `sudo chown root:security /home/shared/security/testsweep.sh`
   
   `sudo chmod 770 /home/shared/security/testsweep.sh`

## Deliverables
1.**Verification of Group and Users Created**

   `grep security /etc/group`

2. **Script File with Correct Permissions**
   
Ensure only security group members have execute rights. 

   `ls -l /home/shared/security/testsweep.sh`

3. **Execution, Testing and Results**
   
Restrict execution so that only members of the security group can run the script.
# 3.1 Switch to a Security User - alice_sec
su - alice_sec

# 3.2. Run the Script
cd /home/shared/security
./testsweep.sh 10.0.2

# 3.3. Show the Content of Script: testsweep.sh
cat testsweep.sh

# 3. Show the Content of Text File: sweep_results.txt (if empty)
cat sweep_results.txt

# 3. Write and show the Content of Text File: sweep_results.txt
echo "10.0.2.150" > sweep_results.txt
echo "10.0.2.150" >> sweep_results.txt
echo "10.0.2.160" >> sweep_results.txt
