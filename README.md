# Traefik-setup
Adding Traefik to my homelab with Lets Encrypt and DNS Challange

the goal of this project is homelab services using Https with legitimate certificates for my homelab services. 

I needed to take several steps to get this project to work. 

Prerequisites: 
    - A fully qualified Domain name
    - A DNS resolver or DNS server to reach out to LetsEncrypt / Cloudflare
    - A reverse proxy that can handle secure routing and hand out certificates automatically 
