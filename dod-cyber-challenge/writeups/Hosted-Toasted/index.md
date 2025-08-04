Hosted Toasted

Access the website

![A screenshot of a web page AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image1.png){width="5.1361329833770775in"
height="5.688293963254593in"}

You will get hit with a Warning:

![A screenshot of a computer AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image2.png){width="6.5in"
height="4.406944444444444in"}

Click on advanced and view certificate and look for anything that sticks
out:

![A screenshot of a computer AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image3.png){width="6.5in"
height="6.322222222222222in"}

I notice that it has two separate dns names registered. When you
originally visit the first website, you are met with this homepage: ![A
screenshot of a document AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image4.png){width="6.5in"
height="7.829166666666667in"}

Going to the other website yields this page:\
![A screenshot of a computer AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image5.png){width="6.5in"
height="5.957638888888889in"}

After identifying the hidden internal domain from the SSL certificate,
we used dig to resolve the public-facing server's IP address. We then
mapped the internal domain to this IP in /etc/hosts to bypass DNS
restrictions and simulate access to an internal virtual host.

![A computer screen with green text AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image6.png){width="6.5in"
height="2.310416666666667in"}

![A screenshot of a computer AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image7.png){width="6.5in"
height="1.8701388888888888in"}

Now save the file and try visiting the website:

![A screenshot of a computer AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image8.png){width="6.5in"
height="6.003472222222222in"}

Explore the website to find the flag! *(hint, it's in at the bottom)*

![A screenshot of a computer AI-generated content may be
incorrect.](D:\Desktop\DOD CYBER WRITEUPS\Hosted-Toasted\images/media/image9.png){width="6.5in"
height="6.534722222222222in"}

Flag: C1{vH0st_S4n_M4g1c_R3ve4l3d}

**🧠 Final Write-Up Summary (Field-Tested for CTF Reports)**

**🔍 Challenge Summary:**

The challenge hinted at a **hidden internal site** behind
https://not-torbian.ethtrader-ai.com/. Buried in the SSL certificate was
a suspicious alternate domain:

CopyEdit

definitelynotaflag.north.torbia

------------------------------------------------------------------------

**🛠️ Step-by-Step Solution**

**✅ Step 1: Discover the Hidden Domain**

By inspecting the SSL certificate (browser padlock \> certificate \>
SAN), we found:

plaintext

CopyEdit

DNS Name: definitelynotaflag.north.torbia

This domain didn't resolve publicly:

bash

CopyEdit

nslookup definitelynotaflag.north.torbia

Returned:

nginx

CopyEdit

NXDOMAIN

------------------------------------------------------------------------

**✅ Step 2: Resolve the Public IP**

We extracted the **public IP address** of the main site with:

bash

CopyEdit

dig +short not-torbian.ethtrader-ai.com

It returned:

CopyEdit

34.86.60.228

------------------------------------------------------------------------

**✅ Step 3: Host Override via /etc/hosts**

To "spoof" internal DNS resolution, we manually mapped the hidden domain
to the public IP:

bash

CopyEdit

sudo nano /etc/hosts

Added this line:

CopyEdit

34.86.60.228 definitelynotaflag.north.torbia

This tricks the system into thinking the internal name resolves
correctly --- perfect for CTFs and pentests where **host header
routing** is used.

------------------------------------------------------------------------

**✅ Step 4: Access the Internal Site**

We then made an HTTPS request directly:

bash

CopyEdit

curl -k https://definitelynotaflag.north.torbia/

Or visited it in-browser to view the content (TLS warning bypassed).

------------------------------------------------------------------------

**🎯 Result:**

The internal site revealed the **flag** or another lead --- inaccessible
via normal DNS.

**📝 Final Notes (for write-up clarity)**

- This challenge demonstrates **host-based virtual routing**.

- It's often used in CTFs to simulate **segregated dev/internal
  infrastructure** that's not directly linked via DNS.

- Modifying /etc/hosts is a classic pentester move when probing SSL
  certs, Docker containers, or corporate web apps.

------------------------------------------------------------------------

If you want, I can turn that into a markdown .md file or PDF export for
your report --- just say the word. 🎯💾
