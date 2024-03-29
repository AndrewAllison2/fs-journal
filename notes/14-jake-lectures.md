- set up mysql database

# AWS Cloud and EC2

 - aws or azure

 - EC2
  
<!-- NOTE openvpn.net -->

 - instances
  - launch instance
  - name server
  - select unbuntu 
    - yum vs apt -> yum generally ref amazon linux
  - select 22.04
  - x86 -> arm is better but doesn't fully support software
  - select t2.micro instance type -> free tiers
  - key-pair
    - create new pair -> leave defaults/create -> 1 download if lost delete key pair
  
  ## Network
    - allow http/https traffic
    - edit > create new security group
      - 1 free vpc
      - subnet - no pref
      - allow ssh from anywhere
      - http/https
      - custom -> MYSQL - 3306 - from anywhere (should set up box to handle traffic then push)
      - no advanced settings change
  
  - Instances
   - spin up machine
   - connect with ssh

  ## NODE INSTALL
   pm2 or nodemon
   

  ## Nginx
    ctrl+r in cm to cycle through commands, ctrl+c or exit to get out, ctrl+, to open workspace settings
    - connect to ec2 instance through cmd ssh
    - Nginx as proxy

    - sudo apt update
    - sudo apt install nginx

    - modify config in nginx -> default

      server{
        listen 80;
        listen [::]:80;
        server_name [IP Address];

        location / {
          copy/paste readme
        }
      }

      npi i -g pnpm
      pnpm install
      pnpm install -P -> don't install dev dependencies
    

    - can put multiple apis in one box and host them on different ports (post-it on port 3000, gregslist on 3001)

    - setup.js in node servers
      - const routeprefix = process.env.ROUTE_PREFIX
    - startup.js server

  ## Github Actions
    - .github/workflows/deploy.yml
    - yml is white space and syntax sensitive


  - settings -> secrets -> add new
    > name = unbuntu
    > ip address => public ec2 ip
    > pem key = copy paste downloaded file -> must exactly match saved file

<!-- NOTE 502 bad gateway means nginx sent traffic to localhost but got no response-->


<!-- NOTE theme forest for landing page inspiration-->


# Thursday

  ## SSL Certs
   - letsencrypt.org -> free cert

    - public/private key pairs
    - jwt.io

  ### Getting A Cert

<!-- NOTE USED CLOUDFLARE TO OBTAIN CERT INSTEAD (SEE BELOW) -->

    - certbot -> guided walkthrough of getting/installing cert

    - install snapd

    - snap is package manager similar to apt
    - install certbot

    - running certbox nginx
      > server name must be valid domain name
      > domain names -> ex: devsanddragons.com

  <!-- NOTE cloudflare to manage DNS over google and buy domain -->
    
    DNS
      - add record
      - type A
      - name points to subdomain
      
      [Type: A, Name: @, IP Address] -> can say dont use proxy / DNS only

      - SSL on cloudflare -> overview -> Full (strict)

  #### SET UP CERT W/ CLOUDFLARE
    - origin server
      - create cert -> RSA 2048, 15 years -> create

      - gives origin cert and private key -> put on EC2 box
      - change nginx config
        > set up to listen on port 443 -> top section of NGINX in readme
        > update server name with the domain name
        > change 2nd server to be port 443, server name to domain name
        > sudo nano into locations and paste the cert and key (key.pem/cert.pem)

    - sudo systemctl restart nginx

    - served over https at this point


GET DOMAIN FOR LANDING PAGE (NameCodes.dev) and then can route each hosted project across that page securely

# Docker
  - research dev ops and kubernetes

  - install docker on ec2 instance -> sudo snap install docker
  - sudo docker ps

  -sudo docker run -d --restart unless stopped -p 80:3000 {{docker-container}}

  - read how to set up docker and a docker container

  <!-- NOTE DOCKER INFO @ digitalocean/ the docker ecosystem
  working with the docker container -->

  - use Jake's config over tutorials configs