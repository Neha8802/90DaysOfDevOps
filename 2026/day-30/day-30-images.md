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
   It shows that image is built of layers. The top layer has the image id, the 



