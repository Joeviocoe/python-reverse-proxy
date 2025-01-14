# python-reverse-proxy
A simple reverse proxy in python

1. Create local DNS entries in your DNS resolver to resolve target hostnames to a local server IP (Optional: Virtual IP in the router)
![DNS_Resolver](https://user-images.githubusercontent.com/16479297/170362188-d0bc34f1-ff6e-4182-8e44-e6c804b7c9a9.png)
2. Optional: Create NAT Port Forward from Virtual IP port 443 to high port (e.g. 9443) if you don't want the python server running as root
![Port_Forward](https://user-images.githubusercontent.com/16479297/170362227-672a08db-ff8b-4a7b-b99f-018a7bed6af2.png)
3. Generate an SSL certificate for the original target domains, signed by your local network CA which must be trusted by client browsers and applications. The paths to the cert file and key file are defined on lines 10 and 11 of proxy.py 
![Screenshot 2022-05-29 at 13-10-07 System Certificate Manager Certificates - Zoltar zDomain](https://user-images.githubusercontent.com/16479297/170887589-977aa6cf-d5e6-4e3c-82b7-efe50d61a452.png)
4. Example:  `python3 proxy.py --hostname tile.openstreetmap.org --port 9443 2>/dev/null`

This proxy.py file includes modifications from the original to include:
1. Line 15: Changed header merge function to work with Python 3.6
2. Line 32: Modify the GET Request URL to work with the new destination URL path format
3. Line 45: Changed resp.text to resp.content to proxy images instead of text
4. Line 108: Added wrapper for SSL
