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

## What is the Jenkinsfile doing?
1. The Jenkinsfile in this case we are using agent none so every stage we have to specify the agent. In the first step we are building a docker container with the image **python:2-alpine** you can use an image of your choice this one is lightweight so we went along with it. 

![Screenshot 2023-05-19 101105](https://github.com/glennmora/empty-repo/assets/108555140/d731a4b3-101f-4f64-a330-c9a7449d90fa)

2. Then we compiling two different files and stashing them in a compiled-results file and including all the python files under our **python-code-project** directory.

![Screenshot 2023-05-19 101125](https://github.com/glennmora/empty-repo/assets/108555140/b8f43cbd-ef64-42fd-b28a-690a4e93d8fd)

3. The next stage we are creating our test container using the **qnib/pytest** image. Again you can use one of your choice that has pytest or any other testing library relative to your coding language.

![Screenshot 2023-05-19 101139](https://github.com/glennmora/empty-repo/assets/108555140/c7a35685-dc3d-422a-835f-ef86f1488220)

4. Next we are using **py.test** to make a JUnit report and export it to a directory we are calling test-reports and naming the file test_results.xml and we are giving it the absolute path of the file. After we are using the *cat* command to show the **test_results.xml** file.

![Screenshot 2023-05-19 101157](https://github.com/glennmora/empty-repo/assets/108555140/84a4041d-23c3-499c-aeb1-86ee18e22c20)

5. At the very end we are archiving the results and exposing them in the Jenkins console output or logs.

## How did I build my Jenkins pipeline job?
1. Here I'm using a pipeline SCM to clone this GitHub repository and i'm making sure to set the path to **/main** and making sure the script path is set to **python-code-project/Jenkinsfile**

![Screenshot 2023-05-19 095556](https://github.com/glennmora/empty-repo/assets/108555140/d8850f3e-2954-4582-bc9e-a3e336a1e5c9)


![Screenshot 2023-05-19 095610](https://github.com/glennmora/empty-repo/assets/108555140/08d313da-266a-4652-82be-0a93dfa3982f)
