# Traefik-setup
Adding Traefik to my homelab with Let's Encrypt and DNS Challenge

The goal of this project is to provide home lab services using HTTPS with legitimate certificates.   
I had help from Christian Lempa through his video [Traefik Tutorial](https://www.youtube.com/watch?v=-hfejNXqOzA&t=776s)  

I needed to take several steps to get this project to work. 

Prerequisites:   
    - A fully qualified Domain name  
    - A DNS resolver or DNS server to reach out to Let's Encrypt / Cloudflare (Or whoever provides the domain name)  
    - A reverse proxy that can handle secure routing and hand out certificates automatically   

I decided to go with [Traefik](https://traefik.io/traefik)

I plan to migrate to Docker Swarm and use it as a single reverse proxy for all my containers across multiple nodes. 


Step 1: Get a Domain Name  
    - You will need to purchase a domain name and set up a couple of A Records for DNS.   
    - An A record with the domain name pointing to your public IP   
    - A Wildcard A Record 
    - You will need to get a Challenge token to use from your domain provider that can be accessed by Traefik. I put it in a .env file in the same directory as my compose. 

Step 2: Set Up DNS for Traefik  
    - I use Pfsense with Unbound, as a result, I needed to go into Pfsense and set up a custom Unbound config  
    - I set up a local zone with the FQDN I purchased and set the IP address range  

Step 3: Set up Traefik  
    - I used Docker Compose to set up Traefik and added the whoami service to test functionality   
    - To reach the self-hosted application I have, they needed to be on the same Docker network in all my compose files for routing  
    - I set up the YAML so that all requests using HTTP were routed to WebSecure and use HTTPS on port 443  
    - Since this was just for testing on my local network originally, I made the dashboard accessible without a password. Though I would not recommend it.  
    - I also added a .env file for the DNS Challenge Token from Cloudflare and assigned it to a variable accessed in the compose

In the Traefik docs, you can see how to add the whoami service to the Docker Compose YAML to test if it's working

[Traefik Docs](https://doc.traefik.io/traefik/expose/docker/basic/)

Step 4: Set up Trafik.yml
    - Along with the main compose file, I added a traefik.yml file in the directory as the compose under config. 
   


    
