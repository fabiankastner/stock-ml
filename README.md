# stock-ml Project  

## **CLC** - Monolith to Microservice with CI/CD pipeline 


### **Summary**

An originally monolithic stock price prediction project using django as a front end, mysql as a database and tensorflow for neural network predictions.


### **Repositories**

Following repositories are included within the main project:

- [fabiankastner/stock-ml-web](https://github.com/fabiankastner/stock-ml-web)  
- [fabiankastner/stock-ml-db](https://github.com/fabiankastner/stock-ml-db)  
- [fabiankastner/stock-ml-data](https://github.com/fabiankastner/stock-ml-data)  
- [fabiankastner/stock-ml-nn](https://github.com/fabiankastner/stock-ml-nn)  
- [fabiankastner/stock-ml-config](https://github.com/fabiankastner/stock-ml-config)  


### **Folder structure**

``` 
stock-ml/
│
├── dev.docker-compose.yml     --   development environment
│
├── local.docker-compose.yml   --   extended development environment (non-containerized django)
│
├── prod.docker-compose.yml    --   production environment
│
├── kubernetes                 --   everything for the local kubernetes setup
│
├── stock-ml-web/              --   django backend
│
├── stock-ml-db/               --   stock database
│
├── stock-ml-data/             --   data service
│
├── stock-ml-nn/               --   neural network
│
├── stock-config/              --   config service
```

### **Setup**

Clone the repository recursively with: `git clone https://github.com/fabiankastner/stock-ml --recursive`.

In case you have already cloned it, execute `git submodule init` and finally `git submodule update`.

#### Setup local dev environment on Linux/Mac:

After you've successfully cloned the repository, check if python is 
available `python3 --version` and `python3 -m pip --version`.
Both statements should return a version number!

Set up a python environment to install all necessary packages locally. In case you don't have virtualenv yet, type `python3 -m pip install --user virtualenv`. 
For this you can type `python3 -m venv venv`. 
You activate the environment with `source venv/bin/activate`.

Now you can install all necessary libraries with `pip install -r 
requirements.txt`.

#### Setup local dev environment on Windows:

After you've successfully cloned the repository, check if python is 
available `py --version` and `py -m pip --version`.
Both statements should return a version number!

Set up a python environment to install all necessary packages locally. In case you don't have virtualenv yet, type `py -m pip install --user virtualenv`.
For this you can type `py -m venv env`. 
You activate the environment with `.\env\Scripts\activate`.

Now you can install all necessary libraries with `pip install -r 
requirements.txt`.

### **Run Docker**

In order to start the docker container use one of the following commands.
Non-prefixed docker-compose.yaml file only here for legacy reasons, to be removed soon.

#### Production:

Made for production, debug modes disabled, hardened.

> docker-compose -f prod.docker-compose.yaml up

#### Development:

Suited for development, source code files of web service mapped into container to utilize django hot reload.

> docker-compose -f dev.docker-compose.yaml up

#### Local:

If you want to start django non-containerized on the host machine, but everything else should be available via docker.
As same volumes as in development are used, this can be utilized to initialize django database.

> doker-compose -f local.docker-compose.yaml up

To finally start django replace values and execute

`DB_NAME=django DB_USER=django DB_PASSWORD=password DB_HOST=localhost DB_PORT=5432`

`python manage.py makemigrations`

don't forget to also call `python manage.py migrate` and `python manage.py createsuperuser`.

### **Run Kubernetes**

#### Local:

Necessary tools installed: kubectl & kind / minikube / other local cluster.

If you want to develop in a full sandbox (local DB) you can use the `kubernetes` folder in this repository root, and apply

> kubectl apply -f {subfolder}

for every subfolder in there.

#### Azure:

Necessary tools installed: kubectl & azure cli (az).

To set necessary kube context locally execute:

> az aks get-credentials --resource-group {yourResGroup} --name {kubernetesServiceName}

Databases have to be provided as database serivce / vm. As CD is used, kubernetes files are split up into the subrepositories. To deploy any part of the project as kubernetes service, just execute:

> kubectl apply -f kubernetes/

Both `stock-ml-config` & `stock-ml-web` can be scaled up as long as the underlying RDMS can withstand the traffic. This can be done manually by editing the deployment or automatically by using kubectl / azure, more information at https://docs.microsoft.com/en-us/azure/aks/cluster-autoscaler.

Keep the configuration settings up to date, and the secrets out of versioning ;)

### **References**

#### Kubernetes:
* Kubernetes explanation: https://medium.com/swlh/pods-deployments-and-services-in-kubernetes-396e04e41e8
* Interactive tutorial: https://kubernetes.io/docs/tutorials/kubernetes-basics/
* Nginx Loadbalancer with affinity cookie: https://kubernetes.github.io/ingress-nginx/examples/affinity/cookie/


### **Contributors**
* Fabian Kastner
* Paul Hörmann
* Nicole Hölzl
