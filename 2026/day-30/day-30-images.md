Task 1: Docker Images
1. Pull the nginx, ubuntu, and alpine images from Docker Hub

   <img width="570" height="376" alt="image" src="https://github.com/user-attachments/assets/c517a71c-1384-4163-bdff-ea0845154464" />

2. List all images on your machine — note the sizes
   <img width="409" height="75" alt="image" src="https://github.com/user-attachments/assets/c519445b-2d6a-44f6-b0b4-51809ac98752" />


3. Compare ubuntu vs alpine — why is one much smaller?
   Ubuntu is a general distribute of linux. It has my libraries and tools by default.
   Alpine is a minimal it is only built for container and it has absolute essentials

4. Inspect an image — what information can you see?
   can see image_id, image_tag, how many layers it took to build, exposed port, path

5. Remove an image you no longer need
   <img width="618" height="193" alt="image" src="https://github.com/user-attachments/assets/40e7a96d-1081-4bee-a6af-373bb0549302" />

Task 2: Image Layer
1. Run docker image history nginx — what do you see?
   It shows that image is built of layers. The top layer has the image id, some of the file holds the size while
   some of them are 0b

2. Each line is a layer. Note how some layers show sizes and some show 0B
   there are some commands that does not create file when it runs thats why there sizes are 0b
   these are like- run, expose, labels.


3. Write in your notes: What are layers and why does Docker use them?
   when the commands get executed they create a layer like one instruction when it executes it will create a layer
   layer helps in building the dockerimage. if the other image is using a same base which is downloaded then it does
   not require redownloading. Layers makes docker fast, effecient, resusable.

Task 3: Container Lifecycle
Practice the full lifecycle on one container:

1. Create a container (without starting it)
   <img width="518" height="60" alt="image" src="https://github.com/user-attachments/assets/fbe71696-0d43-4ce6-8147-4643340501c7" />
   
2. Start the container
   <img width="765" height="70" alt="image" src="https://github.com/user-attachments/assets/e56b65f1-04bd-4e8c-887b-d97abeb4bba5" />

3. Pause it and check status
   <img width="842" height="89" alt="image" src="https://github.com/user-attachments/assets/0858a63f-3665-4eda-80b3-40c6e0135e82" />
   Effect: The container remains running, but all processes are suspended. It doesn’t use CPU.

4. Unpause it
   <img width="739" height="100" alt="image" src="https://github.com/user-attachments/assets/915c6947-cc51-432c-b5c4-be07ed030eb7" />
   Container keeps running it start the processes from where it stopped

5. Stop it
   <img width="510" height="62" alt="image" src="https://github.com/user-attachments/assets/35f1e626-e0bf-4b3e-b1c4-48c083255f0b" />
   Its stops the container but the container exist on the system

6. Restart it
   <img width="739" height="70" alt="image" src="https://github.com/user-attachments/assets/d02e244e-8d9c-466d-ab94-3a80a792e585" />
   container starts running again from its previous states.

7. Kill it
   <img width="842" height="182" alt="image" src="https://github.com/user-attachments/assets/9b9b2883-98dd-4573-9fe5-bd28b8bbf1fe" />
   it kills the container immediately it does not give a chance to processes to clean up we can even restart the conatiner after the
   container kill

9. Remove it
   <img width="494" height="55" alt="image" src="https://github.com/user-attachments/assets/32d3c6dc-11ec-435a-b80b-deae113171c4" />
   the container gets deleted permanently it we don't have it on our system once we do docker rm container_id

Task 4: Working with Running Containers
1. Run an Nginx container in detached mode
   <img width="495" height="37" alt="image" src="https://github.com/user-attachments/assets/7bc7f0bc-44ff-4231-9163-dd50284f657c" />

2. View its logs
   <img width="686" height="230" alt="image" src="https://github.com/user-attachments/assets/6f2d9cec-4276-48a5-8809-1d2b96a6a072" />

3. View real-time logs (follow mode)
   <img width="697" height="240" alt="image" src="https://github.com/user-attachments/assets/19a84793-2b2e-4b4b-a14b-7dcc4a1e0c3a" />

4. Exec into the container and look around the filesystem
   <img width="1033" height="73" alt="image" src="https://github.com/user-attachments/assets/fddf1c96-97e7-4112-a2ee-07ce7afd4c6f" />

5. Run a single command inside the container without entering it
   <img width="323" height="309" alt="image" src="https://github.com/user-attachments/assets/3ddf6e7f-84ef-4df0-92a0-47ae713a1705" />

6. Inspect the container — find its IP address, port mappings, and mounts
   IPAddress: 172.17.0.2
   <img width="217" height="25" alt="image" src="https://github.com/user-attachments/assets/5f329d36-5d1e-41d6-bb46-b9bbe259be7a" />

   Port Mapping: <img width="265" height="158" alt="image" src="https://github.com/user-attachments/assets/e4e91c86-5f4d-49cc-9315-90d1f4982bce" />
   mount: nothing is there - <img width="341" height="57" alt="image" src="https://github.com/user-attachments/assets/6d168aba-5e2e-43c1-99ae-6b3c20615903" />

Task 5: Cleanup
1. Stop all running containers in one command
   docker stop $(docker ps -q)
   <img width="391" height="31" alt="image" src="https://github.com/user-attachments/assets/a18d719f-0c1a-4713-b792-a68ddfdaec68" />

2. Remove all stopped containers in one command
   docker container prune
   <img width="359" height="67" alt="image" src="https://github.com/user-attachments/assets/edae3570-0fad-4ae8-aa2d-9044cf21a5f8" />

3. Remove unused images
   docker images prune -a
   <img width="616" height="49" alt="image" src="https://github.com/user-attachments/assets/0bf40b0f-75c7-4529-b953-7b38b8897341" />

4.Check how much disk space Docker is using
  docker system df
  <img width="470" height="86" alt="image" src="https://github.com/user-attachments/assets/da3bc636-a8af-4cda-a8bd-adce4ef5274c" />

 






   




