# step-project-2-devops-files

STEP 1 ===>
Create test GitLab repo with react app from lection_scripts/lesson-20240215, edit test script command to exit after tests execution
![alt text](<screenshots/Знімок екрана з 2024-03-20 19-11-49.png>)
https://gitlab.com/serhiy.slipchuk/step-project-2

STEP 2 ===> 
Create test account in Docker hub(free)
![alt text](<screenshots/Знімок екрана з 2024-03-20 19-27-55.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 19-31-05.png>)


STEP 3, 4, 5 ===>

Creating VMs, install server monitoring, install Docker with Vagrantfile: https://github.com/SergSL2022/step-project-2-devops-files/blob/main/Vagrantfile

Install Jenkins server in docker container:
https://github.com/SergSL2022/step-project-2-devops-files/blob/main/docker-compose.yml
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-54-55.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-36-13.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-37-53.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-38-28.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-40-17.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-41-41.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-41-53.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-55-36.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 20-44-30.png>)

STEP 6 ===>

Connecting to jenkins-worker VM
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-18-57.png>) 

Create credentials for jenkins-worker VM
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-20-32.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-33-24.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-21-03.png>)

Create and configure jenkins worker
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-21-34.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-22-01.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-25-18.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-26-18.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-27-48.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-28-09.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 21-52-49.png>)

Testing jenkins worker
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-51-15.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-52-08.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-56-12.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-56-20.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-56-27.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-56-59.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-57-39.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-58-05.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-58-41.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 22-59-02.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-09-11.png>)


STEP 7 ===>

Adding Docker hub credentials (login and token)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-40-00.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-41-00.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-41-34.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-44-50.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-45-00.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-45-24.png>)

Adding Gitlab credentials (login and token)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-54-02.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-55-02.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-55-29.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-20 23-57-52.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-21 00-00-11.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-21 00-00-16.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-21 00-00-27.png>)

STEP 8 ===>

Jenkinsfile: https://github.com/SergSL2022/step-project-2-devops-files/blob/main/Jenkinsfile

Creating pipeline
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-49-32.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-50-34.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-51-42.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-52-35.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-53-33.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-54-58.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-55-54.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-56-04.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 00-57-21.png>)

Run pipeline without artifacts adding
![alt text](<screenshots/Знімок екрана з 2024-03-23 18-59-06.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 18-59-30.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 18-59-41.png>)

Run pipeline with artifacts
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-02-50.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-02-58.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-03-05.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-05-33.png>)

Pipeline result in Docker hub registry
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-06-30.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-06-39.png>)

Create an Error in stage "Running tests"
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-10-32.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-18-23.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-18-43.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-19-00.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-19-19.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-19-53.png>)

Remove Error from stage "Running tests"
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-59-30.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 19-59-51.png>)
![alt text](<screenshots/Знімок екрана з 2024-03-23 20-00-15.png>)

VMs monitoring during pipelines run
![alt text](screenshots/photo_2024-03-23_20-03-13.jpg)
![alt text](screenshots/photo_2024-03-23_20-03-28.jpg)
![alt text](screenshots/photo_2024-03-23_20-03-37.jpg)