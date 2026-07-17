This project is to learn & practice JCasC - Jenkins Configuration as Code Plugin<br>
along with DinD Sidecar Pattern for jenkins pipeline execution for hands on poc

I made my custom jenkins helm chart ON top of the Official jenkins helm chart 5.9.33<br>
I created my custom Configuration Files (jcasc files at jenkins-jcasc-helm/files/jcasc)<br> 
, and imported them to configure jenkins using ConfigMaps.

For Pipeline execution, I implemented DinD SideCar approach to share Docker daemon<br>
with the jenkins controller container to run docker builds.

I have written separate README.md or Comments for each sections explaining the Workflow & Execution.<br> 

For Pipeline Script, I used Jenkins SCM Method writing Jenkinsfile to keep in Git Repository<br>
along with the Jenkins Shared-Library Approach for stage functions

For Deployment, I used Student Management System Application, cloned from:<br>
https://github.com/medinar/full-stack-spring-boot-react.git

I used Helm Charts for Managed Kubernetes Deployment I created in the following project:<br>
https://github.com/Ashir-Qayyum/sensiply-training-helm-poc.git