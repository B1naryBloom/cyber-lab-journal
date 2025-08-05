**Lab:** Exploiting an API endpoint using Documentation

**Date Completed:** August 5, 2025

**Platform:** PortSwigger Web Security Academy

**Tools Used:** Burp Suite Professional, Chromium, Firefox, Notes

**OBJECTIVE:** find the exposed API documentation and delete carlos. You
can log in to your own account using the following credentials:
wiener:peter

**Environment Setup:** I am simply using the latest version of kali
Linux, and utilizing Burp Suite's built in browser to complete all the
necessary steps.

**Discovery:** I first opened the built in burp suite browser logged
into the account using the credentials provided. After populating in
Burp's HTTP History tab, I was able to identify a few API endpoints that
looked interesting. What also stood out were the HTTP Request methods:

![A screenshot of a computer AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image1.png)

After logging in I noticed some interesting parameters in the
request:![A screenshot of a login screen AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image2.png){width="3.938692038495188in"
height="3.4333759842519687in"}

![A screenshot of a computer screen AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image3.png){width="2.870748031496063in"
height="4.65382217847769in"}

I also noticed that when I changed the email, I found another api
endpoint **/api/user/wiener**: ![A screenshot of a computer screen
AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image4.png){width="6.15625in"
height="5.979166666666667in"}

So I sent this request to the burp repeater so that I can begin editing
and sending requests. For starters, I started with completely getting
rid of the /api**[/user/wiener]{.underline}** portion of the api and
then I sent the request: ![A screenshot of a computer screen
AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image5.png){width="6.5in"
height="4.834027777777778in"}

I right-clicked and viewed this page in the browser and this is what was
shown: ![A screenshot of a web security academy AI-generated content may
be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image6.png){width="6.276801181102362in"
height="5.44861220472441in"}

If you click into the DELETE table, it lets you input a "string", so I
inputted carlos to see what would happen: ![A screenshot of a computer
AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image7.png){width="6.1988987314085735in"
height="3.692186132983377in"} Then I clicked the green Send Request
button: ![A screenshot of a computer AI-generated content may be
incorrect.](C:\Users\DOUGLAS\Documents\web-security-academy\Labs\API Testing\api-exploit-using-documentation\images/media/image8.png){width="4.637212379702537in"
height="3.936809930008749in"}

Carlos has been deleted (sorry Carlos!) and we have completed the lab!
But we also see in the text box that we could have deleted his account
by also utilizing a curl command!

