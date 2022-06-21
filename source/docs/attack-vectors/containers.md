# Containers

Containers significantly increase the attack surface of any application. They may seem like a secure option because of 
their short lifespan and their isolated nature, but they are usually deployed on the same IP space. 

If an adversary gains access to even a single container, they can then access any number of other containers in the 
cluster. And in 15 to 20 minutes, adversaries can access other vulnerabilities and download packages that can be used 
for more elaborate attacks.