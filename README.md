# 2420_assign2
# Step 1 (VPC and Load Balancer setup, along with droplet creation)
# Head over to digitalocean and create a VPC first (located in the manage -> networking tab), name it whatever you want. Set the location to SFO3.
![image](https://user-images.githubusercontent.com/98194499/205429597-6fa59b82-0a35-42a2-81fd-da4231a0dd5a.png)

# Create your two droplets now, selecting the VPC that we created earlier. Add "web" as a tag, and make sure the server is SFO3.
![image](https://user-images.githubusercontent.com/98194499/205429657-a943001d-2bd2-4ad7-af41-6521b2e5af41.png)
![image](https://user-images.githubusercontent.com/98194499/205429661-6c273175-2f6c-4f60-8fb1-13420cbbd97b.png)

# After creating the droplets, create the load balancer, selecting the VPC that you created.
![image](https://user-images.githubusercontent.com/98194499/205429682-d9bfb17f-8e78-40b1-9300-6f99c807b5ba.png)

# Step 2 (Creation of server configs and html)
# Afterwards, login to any one of the two servers via ssh.
![image](https://user-images.githubusercontent.com/98194499/205429753-e28006e3-393f-40bf-9e4a-417a18062e10.png)

# Perform sudo apt update and upgrade for the server first.
![image](https://user-images.githubusercontent.com/98194499/205430117-08317d6a-2160-4b34-8159-07b2236b99ac.png)
![image](https://user-images.githubusercontent.com/98194499/205430130-36230c18-0257-4a62-a93b-b862f4c24774.png)


# Install Caddy by following the documentation linked below, and copy pasting the commands there in the "Stable releases" area.
https://caddyserver.com/docs/install#debian-ubuntu-raspbian

# Install Volta, and execute the content with source.
![image](https://user-images.githubusercontent.com/98194499/205429813-13fd00d9-8bff-471c-b4d8-48dfe6434c23.png)

# Install node with Volta, and then create two new directories in the home directory named "html" and "src".
![image](https://user-images.githubusercontent.com/98194499/205429834-f7101871-7c92-4821-8cb5-90334885f29d.png)

# Create a file in the html directory called "index.html" and attach basic boilerplate html to it, as well as a message stating that you are in the specified server.
![image](https://user-images.githubusercontent.com/98194499/205429896-c0cd3599-3c93-4e2d-8839-4b56797b5a0a.png)

# Create a file in the "src" directory called "hello_web.service".
![image](https://user-images.githubusercontent.com/98194499/205429925-1860edba-168f-4bb6-86d1-3aa0e760ba45.png)

# Install fastify in the directory, and then proceed to make index.js in the src directory, and then edit the js file so that it listens to port 5050.
![image](https://user-images.githubusercontent.com/98194499/205429946-61a41eec-2c58-4dd7-8cfe-e7ed5796e5b2.png)
![image](https://user-images.githubusercontent.com/98194499/205431498-3f991cf5-5aa6-4e4a-8805-b810ebd52998.png)


# In the home directory, create a file called "Caddyfile", and vim into /etc/caddy/Caddyfile and configure it such that you set the path to the sites directory, and you enable the reverse proxy and add /api.
![image](https://user-images.githubusercontent.com/98194499/205431429-999574c8-ec41-4667-b652-35911b23c136.png)

# Now, edit the service file in src so that it can start the node application, and make it so that it can restart the service on failure.
![image](https://user-images.githubusercontent.com/98194499/205431196-a5e2d2ff-17b5-4308-97a4-f1c1320006e3.png)

# Change the owner of the Caddyfile and chmod it so that only the owner and group can read or write for the file. Copy the associated caddyfile in your home directory to the caddyfile located in /etc/caddy/Caddyfile.
![image](https://user-images.githubusercontent.com/98194499/205430761-128f3d39-0af4-485e-b217-f91dde92c465.png)

# Create new src and html directories in the var folder, with -p to create the other necessary directories. Use your load balancer ip in the command.
![image](https://user-images.githubusercontent.com/98194499/205430861-58561afc-4093-4f3f-8952-b199d50aa50c.png)

# Copy the index, src, and service files to the var and systemd directories respectively.
![image](https://user-images.githubusercontent.com/98194499/205430972-9769d77a-896f-4082-a6b8-b1db195478c7.png)
![image](https://user-images.githubusercontent.com/98194499/205430991-4a9f9232-359e-4cd7-bf63-7a81c4179f1d.png)

# Reload the daemon, and then check the status of caddy.
![image](https://user-images.githubusercontent.com/98194499/205431019-8c2e2422-b4c3-43cb-a6fc-6460fa2c4592.png)

# After that's done, check to see if everything is working with curl localhost.
![image](https://user-images.githubusercontent.com/98194499/205431760-0b634f90-bc25-43f9-b681-be2aa6cb71c1.png)











