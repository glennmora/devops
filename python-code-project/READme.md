## Here we will build and unit test using Docker and Python
1. In this project we will be building a two docker containers a build container and test container. The build container has the proper python version installed that will identical to our environment. You can think of this as a copy to your company's web application. The test container on the other hand will have Pytest installed we will use this container to test our environment by running a test in it.

2. Tools used:
* Jenkins
* Python
* Pytest
* Docker

## Requirements
1. I would suggest having a VM that has at least 2CPU of RAM and 2 GB of Memory. 
2. Having Jenkins, Python, and Docker installed
3. You could also just have Docker installed since the containers are going to have the Python installed in them. Your preference.

## What are the Python files doing?
1. Thy python files in this case are testing the function in main.py. The *do-stuff* function is adding 5 plus *num*. The *test.py* file is just testing different scenerios and different type of errors so we can keep polishing this *do-stuff* function.

2. We are using the test file to test different paramaters that a user might input so we can make this function more durable. The *test.py* file is importing the *do_stuff* function from our script file and running various test.