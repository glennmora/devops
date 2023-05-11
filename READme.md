# Building and pushing docker image with a Jenkinsfile

This repository builds a docker image using a dockerfile that we created. It will tag the docker image and push to our dockerhub.

## What does the Jenkins job do?

In this case we create a Jenkins pipeline SCM to clone this repository. We then specify the branch "main" and finally we give it the script path which is just "/Jenkinsfile"

## What does the Jenkinsfile do?

1. First in our Jenkinsfile we are going to give our docker credentials so that we are able to login and push to our docker image to our dockerhub folder. We did under "Manage Jenkins/Credentials". After that we will checkout the git repository "checkout scm" we then verify it's installed "ls *". 
 
2. The next step is we are actually building the docker image by running "sh 'docker build -t rangel9697/jenkinstest:$BUILD_NUMBER ./pushdockerimage/'" here we are using the docker build command and tagging it using our dockerhub id and using a preconfigured variable provided by Jenkins "$BUILD_NUMBER" we then specify the dockerfile path which in this case is just "./" since we don't have a subfolder in our Github directory.

3. After we need to login using our docker credentials "sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'" we echo our docker credentials and then use a pipe and run the docker login command and using the password that was captured from the echo.

4. Then we actually push the docker image using " sh 'docker push rangel9697/jenkinstest:$BUILD_NUMBER'". Here  we are pushing the docker image using our tag.

5. Lastly we are going to logout of docker which is always a good practice!

## What does the requirements.txt file do?

1. The requirements file keeps the external dependencies that are going to be installed in the docker container image that we're creating. In this case we want our image to have Flask version 2.3.2 .

## What does the Dockerfile do?

1. The docker is grabbing the image of "python 3.11.3-buster" image. Then creating a "/app" work directory. After it's copying our "requirements.txt" file and running "pip3 install" so that we're able to grab all the "requirements.txt" packages. Then copying everything we just created and booting up the container.

## What does the app.py file do?

1. The app.py file in this case is pretty basic. We are importing the Flask library and from the library we are using Flask. Then we are defining a simple "hello_world" function that returns "This is a DevOps Example!"

## Neccesarry tools to run this environment

1. Make sure you have Python3 installed this should work with any version of Python3. You should also have Docker install and we are assuming that you're using an CentOS environment. Third, is we should have Git installed. Lastly make sure to have Jenkins installed in your system to be able to create the pipeline and a dockerhub account to push the docker image.

2. Have fun! Experiment and let me know if you guys encounter any problems I'll do my best to fix them!