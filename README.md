DeepFake Detection API Documentation

Directory Structure 
Deepfake_detection
    |
    |--- Django Application
    |--- Model Creation
    |--- Documentaion


Running application locally on your machine
Step 1 : Clone the repo and Navigate to Django Application
git clone https://github.com/Kartikgc9/KAY_API.git

Step 2: Create virtualenv
python -m venv

Step 3: Activate virtualenv 
venv\Scripts\activate

Step 4: Install requirements
pip install -r requirements.txt

Step 5: Run project
python manage.py runserver


SYSTEM ARCHITECTURE
 

Model Creation
Dataset
Some of the dataset used are listed below:
•	FaceForensics++
•	Celeb-DF
•	Deepfake Detection Challenge
Preprocessing
•	Load the dataset
•	Split the video into frames
•	crop the face from each frame
•	save the face cropped video
Model and train
•	It will load the preprocessed video and labels from a csv file.
•	Create a pytorch model using transfer learning with RestNext50 and LSTM.
•	Split the data into train and test data
•	Train the model
•	Test the model
•	save the model in .pt file
Predict
•	Load the saved pytorch model
•	Predict the output based in trained weights.

ENV PYTHONDONTWRITEBYTECODE 1

ENV PYTHONUNBUFFERED 1

#create a directory to serve static filesRUN mkdir -p /home/app/staticfiles/app/uploaded_videos/
WORKDIR /app
COPY ./requirements.txt/app/requirements.txt
RUN python -m pip install --upgrade pip
RUN pip install cmakeRUN 
pip install opencv-python==4.2.0.32
RUN pip install -r requirements.txt
COPY . /app
RUN python manage.py collectstatic –noinput
RUN pip install gunicornRUN mkdir -p /app/uploaded_videos/app/uploaded_videos/
VOLUME /app/run/
ENTRYPOINT ["/app/bin/gunicorn_start.sh"]

Model Architecture: 
A CNN-LSTM model is defined:
CNN Backbone: ResNeXt50 is used as a feature extractor.
LSTM: Processes sequential data (frames) to capture temporal dependencies.
Fully Connected Layer: Outputs probabilities for fake/real classification.
SUMMARY

Preprocess: Extract frames, crop faces, and normalize.
Model: Use ResNeXt + LSTM to classify videos as REAL or FAKE.
Output: Visualize the decision using heatmaps and print predictions.
