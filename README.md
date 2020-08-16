# :building_construction: Build a CI/CD pipeline for a Robo-friends application using rolling deployment strategy

##  Project Description 📝

- Build an web application that lets you search between Robots API and generates robots by name.
- Build an automated CI-CD pipeline that deploys a React.js application into a Kubernetes cluster in a rolling deployment fashion hosted with AWS EKS & ECR.
- Every code change pushed into this repository is validated by a Jenkins.


### Setup the Environment ⚙️


In order to run this project, you need to have AWS Account, AWS CLI, Docker, eksctl, kubectl.

* If you don't have a AWS Account.[Create using this link](https://portal.aws.amazon.com/billing/signup?nc2=h_ct&src=header_signup&redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start)
* use the [AWS CLI version 2] (https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) to install

After setting up the enviroment, you need to run
   
```bash
> aws --version
```

* Install AWS [eksctl] (https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)

Test your environment using Kubectl and eksctl
   
```bash
> kubectl version --short --client
```

```bash
> eksctl version
```

* Finally, You need to also install [Docker] (https://docs.docker.com/engine/install/ubuntu/)

```bash
> docker -v
```


 ### Project Folder structure 🗃

## A typical top-level directory layout

.
├── Dockerfile             # (Build an image of  the app to be published in AWS Elastic Container Registry`ECR`)
├── Infra
│   └── appDeployment.yml  # (Deploy the ECR in AWS Elastic Kubernetes Service`Eks`)
├── Jenkinsfile            # (Setup CI/CD pipeline that will automate the deployment using Jenkins and Deploy into AWS EKS)
├── README.md
├── jenkins                # (Created AWS infrastructure for `Jenkins`)
│   ├── create.sh
│   ├── jenkins-parameters.json
│   ├── jenkins_infra.yml
│   └── update.sh
├── package-lock.json
├── package.json
├── public
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
└── src
    ├── App.test.js
    ├── components
    │   ├── Card.js
    │   ├── CardList.js
    │   ├── Scroll.js
    │   └── SearchBox.js
    ├── containers
    │   ├── App.css
    │   └── App.js
    ├── index.css
    ├── index.js
    └── serviceWorker.js



Continuous Integration you will set up Continuous Deployment, which will include:

Pushing the built Docker container(s) to the Docker repository (you can use AWS ECR, create your own custom Registry within your cluster, or another 3rd party Docker repository) ; and
Deploying these Docker container(s) to a small Kubernetes cluster. For your Kubernetes cluster you can either use AWS Kubernetes as a Service, or build your own Kubernetes cluster. To deploy your Kubernetes cluster, use either Ansible or Cloudformation. Preferably, run these from within Jenkins as an independent pipeline.