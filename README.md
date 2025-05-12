<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this walkthrough, we will be experimenting with DNS. This lab will help us have a better understanding of DNS. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined your domain

<h2>Lab Steps</h2>
<p>
</p>
<p>
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as an admin (mydomain\jane_admin)
From Client-1, try to ping “mainframe”, notice that it fails.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/8594359c-cb9b-4752-9751-41a166f4d956" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Nslookup “mainframe”, notice that it fails (no DNS record)
</p>
<br />
<img src="https://github.com/user-attachments/assets/a69874c7-9451-4c0f-b509-454dc09185db" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

</p>
<p>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works

</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/59e5ccc1-61a1-4249-9528-064408275ae3" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://github.com/user-attachments/assets/5d036d10-3802-4650-be86-c191fab7f59b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
<p>
Go back to DC-1 and change the mainframe’s record address to 8.8.8.8
Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address.

</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/314afe12-a799-418e-b8f4-975ce29f0e00" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://github.com/user-attachments/assets/cb0078a7-987f-41ef-a9ff-8439e35eb963" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</ br>
Observe the local DNS cache (ipconfig /displaydns)
Flush the DNS cache (ipconfig /flushdns).
Observe that the cache is empty (ipconfig /displaydns)
Attempt to ping “mainframe” again. Observe that the address of the new record is showing up.


</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/47d542ce-539c-4a46-8815-7f0950eeef3c" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</ br>
<p>
Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com


</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/d128e8ce-b2d4-411f-b88a-b584b300b9e1" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</ br>
<p>
Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record.


</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/42d07531-e254-4eb5-8f15-60d3e06c6a84" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</ br>
<p>
On Client-1, nslookup “search”, observe the results of the CNAME record


</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/6bfbd6ea-77b5-4378-8cca-01f347b35b2b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>



