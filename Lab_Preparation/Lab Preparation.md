## Lab Preparation

**Step 1:** Reset the Windows Server evaluation license using the `slmgr /rearm` command in PowerShell with administrator privileges

![Step 1 - slmgr rearm command](images/Pasted%20image%2020260613002401.png)
![Step 1 - confirmation prompt](images/Pasted%20image%2020260613002446.png)

**Step 2:** Restart the server and verify the license status changes from "License is expired" to "Expires in 90 days"

**Step 3:** Install Guest Additions on the server VM

![Step 3 - Guest Additions install](images/Pasted%20image%2020260613002538.png)

**Step 4:** Install Guest Additions on the client (end user) desktop VM

**Step 5:** Before disconnecting internet access, re-log in to both the server and client desktop to allow policy settings to refresh

![Step 5 - re-login after policy refresh](images/Pasted%20image%2020260613003708.png)

**Step 6:** Configure a static IP address on the server: IP `192.168.100.1`, subnet mask `255.255.255.0`, gateway and DNS pointing to itself

![Step 6 - server static IP config](images/Pasted%20image%2020260613174704.png)

**Step 7:** Configure a static IP address on the client computer: IP `192.168.100.10`, subnet mask `255.255.255.0`, gateway and DNS pointing to the server

![Step 7 - client static IP config](images/Pasted%20image%2020260613181118.png)

**Step 8:** Verify network connectivity between the machines using the `ping` command