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
incorrect.](images/image1.png)

After logging in I noticed some interesting parameters in the
request:![A screenshot of a login screen AI-generated content may be
incorrect.](images/image2.png)

![A screenshot of a computer screen AI-generated content may be
incorrect.](images/image3.png)

I also noticed that when I changed the email, I found another api
endpoint **/api/user/wiener**: ![A screenshot of a computer screen
AI-generated content may be
incorrect.](images/image4.png)

So I sent this request to the burp repeater so that I can begin editing
and sending requests. For starters, I started with completely getting
rid of the /api**[/user/wiener]{.underline}** portion of the api and
then I sent the request: ![A screenshot of a computer screen
AI-generated content may be
incorrect.](images/image5.png)

I right-clicked and viewed this page in the browser and this is what was
shown: ![A screenshot of a web security academy AI-generated content may
be
incorrect.](images/image6.png)

If you click into the DELETE table, it lets you input a "string", so I
inputted carlos to see what would happen: ![A screenshot of a computer
AI-generated content may be
incorrect.](images/image7.png) Then I clicked the green Send Request
button: ![A screenshot of a computer AI-generated content may be
incorrect.](images/image8.png)

Carlos has been deleted (sorry Carlos!) and we have completed the lab!
But we also see in the text box that we could have deleted his account
by also utilizing a curl command!


