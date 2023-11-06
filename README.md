# simple-attendance-system
simple attendance system using face recognition

#1. Tutorial:
   
   Step 1: download source from github
   ```sh
   $ git clone https://github.com/nguyen-tho/simple-attendance-system.git
   ```
   Step 2: install pakages by command.
   ```sh
   $ pip install -r requirements.txt
   ```
   Step 3: run program.
   run GUI.py file by command.
   ```sh
   $ python GUI.py
   ```
   or
   ```sh
   $ python3 GUI.py
   ```
   if you use python 3
#2. Collect data:
   - System will take a video about 350 frame, user can make several poses as much as possible to create a variety dataset

#3. Capture an image to verify:
   - When user need to check in, system will take a photo automatically for 5s after camera/webcam turned on
#4. Deepface:
   - In this project I have just used deepface to verify the identity of a person who sign up his/her information and data has been saved in our database
   - Using find method to check an image which is fiited to one or more images in database
   ```sh
   from deepface import Deepface
   checklist =  DeepFace.find(image, data_path, enforce_detection=False)
   #image is path of image which is captured to verify
   #data_path is path of that person dataset
   ```
   - set threshold to determine how many correct samples are enough to make decision verified or not verified.
   - In this case, set threshold more than 0,6
   where
   ```sh
   threshold = len(checklist)/num_of_files(name)
   #threshold > 0,5 -> verified, otherwise -> not verified
   #num_of_files(name) is the number of samples which exists in each person dataset
   #len(checklist) is the number of samples which are predicted is true
   ```

#5. Advantages and Disadvantages
   ### Advantages
   - Can recognize object in weak brigtness environment
   - When signed up user wear glasses. However, while recognition that person do not wear glass -> can recognize
   ### Disadvantages
   - In the first time need to download model file and weights file -> it spends too much time (about 120 seconds) depends on computer
   - When threshold too low model may have a wrong prediction
   - Cannot detect real-time -> cannot apply to a practical project

#6. References:
   - Deep face: https://github.com/serengil/deepface .
   - UI design: https://github.com/joeVenner/FaceRecognition-GUI-APP
    
   
   