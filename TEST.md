How to test? 

I am using Minikube for kubernetes with colima docker driver

First Clone the repository to your local.<br>

login to your dockerhub account (with terminal as well) & generate PAT<br>

Replace the username with yours & placeholder for password with your generated PAT at<br>
jenkins-jcasc-helm/files/jcasc/credentials.yaml for the dockerhub account

Replace everywhere the username is required with your dockerhub username<br>
Jenkins username & password with yours in the values.yaml<br>
GitHub repository with your repository url<br>
Image name & tag with what you want yours everywhere<br>
e.g. in sms-helm charts, jcasc credentials, jcasc helm chart values.yaml, shared library<br>
For jenkins-custom image, you can use my image<br>
Configure Shared-Library with your details (like repo url, branch etc.)

Go to the helm chart directory: jenkins-jcasc-plugin-poc/jenkins-jcasc-helm<br>
Create a jenkins namespace<br>
> kubectl create namespace jenkins<br>
Install the jenkins helm chart:<br>
>helm install jenkins . -f values.yaml -n jenkins<br>
Wait & Validate its installations<br>
> kubectl get po -n jenkins -w<br>
Install the jenkins service account configuration (go to jenkins-sa-config/)<br>
> kubectl apply -f jenkins-admin-crb.yaml
Port-forward the service to access the UI (Run this in background in a new terminal tab)<br>
> kubectl port-forward -n jenkins svc/jenkins 8080:8080 &<br>
(IF THE UI IS IN DARK MODE AS I SET IT, THEN JCASC PLUGIN IS WORKING FINE, CHECK OTHER CONFIGS)<br>
Enter jenkins admin username, and password you set in the values.yaml<br>
Create a new job, JOB SCM, enter your repo details and set Jenkinsfile at SCM<br>
Push your Modified local repo to your remote (e.g. GitHub)<br>
Trigger the job with clicking the Build Button<br>
The pipeline will be executed, image is built, pushed to your dockerhub registry<br>
Deployed in your cluster using helm.<br>
Port-forward the Frontend Service to access the Application Frontend<br>
kubectl port-forward -n jenkins svc/frontend 8081:80 --address 0.0.0.0 &<br>
Access it at browser: http://localhost:8081