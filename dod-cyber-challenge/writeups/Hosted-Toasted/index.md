Hosted Toasted

Access the website

![A screenshot of a web page AI-generated content may be
incorrect.](images/image1.png)

You will get hit with a Warning:

![A screenshot of a computer AI-generated content may be
incorrect.](images/image2.png)

Click on advanced and view certificate and look for anything that sticks
out:

![A screenshot of a computer AI-generated content may be
incorrect.](images/image3.png)

I notice that it has two separate dns names registered. When you
originally visit the first website, you are met with this homepage: ![A
screenshot of a document AI-generated content may be
incorrect.](images/image4.png)

Going to the other website yields this page:\
![A screenshot of a computer AI-generated content may be
incorrect.](images/image5.png)

After identifying the hidden internal domain from the SSL certificate,
we used dig to resolve the public-facing server's IP address. We then
mapped the internal domain to this IP in /etc/hosts to bypass DNS
restrictions and simulate access to an internal virtual host.

![A computer screen with green text AI-generated content may be
incorrect.](images/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](images/image7.png)

Now save the file and try visiting the website:

![A screenshot of a computer AI-generated content may be
incorrect.](images/image8.png)

Explore the website to find the flag! *(hint, it's at the bottom)*

![A screenshot of a computer AI-generated content may be
incorrect.](images/image9.png)

Flag: C1{vH0st_S4n_M4g1c_R3ve4l3d}


