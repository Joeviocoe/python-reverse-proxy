# python-reverse-proxy
A simple reverse proxy in python

1. Create local DNS entries in your DNS resolver to resolve target hostnames to a local server IP (Optional: Virtual IP in the router)
2. Optional: Create NAT Port Forward from Virtual IP port 443 to high port (e.g. 9443) if you don't want the python server running as root
3. Generate an SSL certificate signed by your local network CA (trusted by client browsers and applications)
4. `python3 proxy.py --hostname tile.openstreetmap.org --port 9443 2>/dev/null`
