## Active Directory OU and Group Management

### Environment Preparation

**Static IP configured on Glasgow with DNS pointing to the London domain controller.**

![Static IP configuration on Glasgow](images/Pasted%20image%2020260614171956.png)
![DNS configuration on Glasgow](images/Pasted%20image%2020260614172346.png)

**Glasgow domain controller successfully demoted, server removed from the wyrobek.local domain.**

**Glasgow successfully joined to the contoso.com domain hosted on the London server.**

![Domain join to contoso.com](images/Pasted%20image%2020260614172922.png)
![Domain join confirmation](images/Pasted%20image%2020260614173842.png)

**Existing Kadry and Kierownicy OUs confirmed at the domain root on the London server, prior to reorganization.**

![Domain tree reviewed on London](images/Pasted%20image%2020260614175213.png)

**RSAT Active Directory tools installed on the Nowak client.**

![RSAT AD tools installed](images/Pasted%20image%2020260614175354.png)

### Task 1

*Goal: build the OU structure under contoso.com — Użytkownicy_wyrobek as the parent OU, with Dział IT, Księgowość, Sprzedaż, and Marketing nested inside, and move the existing Kadry and Kierownicy OUs into it.*

**Parent OU uzytkownicy_wyrobek created in the contoso.com domain root, with sprzedaz_wyrobek and marketing_wyrobek created inside it.**

![OU structure created](images/Pasted%20image%2020260614180055.png)

**ksiegowosc_wyrobek and dzial_it_wyrobek OUs created via the dsadd command on the London server.**

![OUs created via dsadd](images/Pasted%20image%2020260614180246.png)

**Kadry and Kierownicy OUs moved from the domain root into uzytkownicy_wyrobek.**

![OUs moved into uzytkownicy_wyrobek](images/Pasted%20image%2020260614181556.png)

### Task 2

*Goal: create domain accounts for the sales team (Tomasz Smyk, Jan Kot, Tomasz Lem, Artur Radecki) inside sprzedaz_wyrobek using the first-initial + surname naming convention, and verify login from both a client and a server.*

**User accounts tlem, tsmyk, and aradecki created in the sprzedaz_wyrobek OU.**

![User accounts created](images/Pasted%20image%2020260614182039.png)

**User account jkot created via the dsadd command in the sprzedaz_wyrobek OU.**

![jkot created via dsadd](images/Pasted%20image%2020260614182242.png)

**Successful domain user login on the Nowak client machine.**

![Domain login on Nowak](images/Pasted%20image%2020260614182612.png)

**Successful domain user login on the Glasgow server.**

![Domain login on Glasgow](images/Pasted%20image%2020260614183036.png)

### Task 3

*Goal: fix a missed requirement — restrict logon hours and disable password changes for all sales OU users at once, without recreating any accounts.*

**Logon hours set to 7:00–18:00 and "User cannot change password" enabled for all users in the sprzedaz_wyrobek OU simultaneously, using multi-select.**

`Select all users in sprzedaz_wyrobek OU using Ctrl+A -> right-click -> Properties -> Account -> check "User cannot change password" -> click Logon Hours -> select Monday to Friday 7:00-18:00 -> OK -> OK`

![Multi-select account restrictions applied](images/Pasted%20image%2020260614184800.png)

### Task 4

*Goal: create a global group for the sales department and a domain local group for shared printer access, nesting the global groups inside it.*

**Global security group Sprzedaz created in the sprzedaz_wyrobek OU.**

![Global group Sprzedaz created](images/Pasted%20image%2020260614185154.png)

**All sales department users added as members of the Sprzedaz global group.**

![Members added to Sprzedaz](images/Pasted%20image%2020260614185231.png)

**Domain local security group Drukarka_HP_Laserjet4000_1pietro created in the sprzedaz_wyrobek OU.**

![Domain local group created](images/Pasted%20image%2020260614185341.png)

**Groups Sprzedaz and Kadry added as members of the Drukarka_HP_Laserjet4000_1pietro domain local group.**

![Groups nested in domain local group](images/Pasted%20image%2020260614185627.png)

### Task 5

*Goal: grant Jan Kot local administrator rights on Glasgow only, without affecting his permissions on any other machine.*

**User jkot added to the local Administrators group on the Glasgow server only.**

`Log in to Glasgow as domain administrator -> Win + R -> lusrmgr.msc -> Groups -> Administrators -> double-click -> Add -> type jkot -> Check Names -> OK -> OK`

![jkot added to local Administrators](images/Pasted%20image%2020260614190501.png)

**User jkot confirmed as local administrator on the Glasgow server.**

![jkot confirmed as local admin](images/Pasted%20image%2020260614190746.png)
![jkot local admin verification](images/Pasted%20image%2020260614190806.png)

**A different domain user (jnowak) logged in on Glasgow to confirm standard accounts have no administrative access, unlike jkot.**

![Regular user session on Glasgow](images/Pasted%20image%2020260614191031.png)

### Task 6

*Goal: move Tomasz Lem into the Kadry OU, delegate him user-management rights over that OU only, and give him a desktop shortcut to manage it.*

**User tlem moved from sprzedaz_wyrobek to the Kadry OU.**

![tlem moved to Kadry OU](images/Pasted%20image%2020260614191154.png)

**User tlem added to the Kadry group to inherit resource permissions.**

![tlem added to Kadry group](images/Pasted%20image%2020260614191228.png)

**Delegation of group management permissions granted to tlem in the Kadry OU.**

![Delegation of control wizard](images/Pasted%20image%2020260614191323.png)

**Custom MMC console saved as zarzadzanie_domena_wyrobek.local on tlem's desktop on Nowak.**

![MMC console saved on tlem desktop](images/Pasted%20image%2020260614192145.png)

**tlem successfully manages groups in the Kadry OU but receives an access denied error in other OUs.**

![tlem managing groups in Kadry OU](images/Pasted%20image%2020260614192256.png)
![Access denied in other OU](images/Pasted%20image%2020260614192318.png)