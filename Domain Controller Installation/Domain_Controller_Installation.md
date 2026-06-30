## Domain Controller Installation & AD Management Console Setup

**Adding the Active Directory Domain Services role via Server Manager.**

`Server Manager -> Add roles and features -> Next -> Next -> Next -> Active Directory Domain Services -> Add Features -> Next -> Next -> Next -> Install`

![Add AD DS role](images/Pasted%20image%2020260613175159.png)

**Active Directory Domain Services role installation in progress.**

![AD DS installation progress](images/Pasted%20image%2020260613175342.png)

**Initiating domain controller promotion after AD DS role installation.**

After installation, click **Promote this server to a domain controller**.

![Promote to domain controller](images/Pasted%20image%2020260613175752.png)

**Configuring a new Active Directory forest with the domain name wyrobek.local.**

`Add a new forest -> type wyrobek.local -> Next`

![New forest configuration](images/Pasted%20image%2020260613180002.png)

**Logging in as domain administrator WYROBEK\Administrator after server reboot.**

![Domain admin login](images/Pasted%20image%2020260613180955.png)

**Joining the Windows client machine to the wyrobek.local domain.**

`Control Panel -> System -> Change settings -> Change -> Domain -> type wyrobek.local -> OK -> enter Administrator + password -> OK -> restart`

![Join client to domain](images/Pasted%20image%2020260613181725.png)

**Confirmation that the client has successfully joined the wyrobek.local domain.**

![Domain join confirmation](images/Pasted%20image%2020260613181746.png)

**Restarting and verifying login with the domain account.**

`On login screen -> Other user -> WYROBEK\Administrator + password`

![Domain account login verification](images/Pasted%20image%2020260613182123.png)

**Adding the Active Directory Users and Computers snap-in to the MMC console.**

`Win + R -> mmc -> File -> Add/Remove Snap-in -> Active Directory Users and Computers -> Add -> OK`

![Add AD Users and Computers snap-in](images/Pasted%20image%2020260614184251.png)

**Active Directory Users and Computers snap-in added to MMC console.**

`File -> Save As -> Desktop -> name: domain_controller_wyrobek.local -> Save`

![Save MMC console](images/Pasted%20image%2020260614184450.png)