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

   