# stock-ml Project  

## **CLC** - Monolith to Microservice  

---

### **Summary**
An originally monolithic stock price prediction project using django as a front end, mysql as a database and tensorflow for neural network predictions.

---

### **Repositories**
Following repositories are included within the main project:

- [fabiankastner/stock-ml-web](https://github.com/fabiankastner/stock-ml-web)  
- [fabiankastner/stock-ml-db](https://github.com/fabiankastner/stock-ml-db)  
- [fabiankastner/stock-ml-data](https://github.com/fabiankastner/stock-ml-data)  
- [fabiankastner/stock-ml-nn](https://github.com/fabiankastner/stock-ml-nn)  
- [fabiankastner/stock-ml-config](https://github.com/fabiankastner/stock-ml-config)  

---

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

Clone Repo recursively with: `git clone https://github.com/fabiankastner/stock-ml --recursive`.

In case you have already cloned it, execute `git submodule init` and finally `git submodule update`.

### **Run**

Non-prefixed docker-compose.yaml file only here for legacy reasons, to be removed soon.

#### **Production**

*TODO*

Made for production, debug modes disabled, hardened.

> docker-compose -f prod.docker-compose.yaml up

### **Development**

Suited for development, source code files of web service mapped into container to utilize django hot reload.

> docker-compose -f dev.docker-compose.yaml up

### **Local**

If you want to start django non-containerized on the host machine, but everything else should be available via docker.
As same volumes as in development are used, this can be utilized to initialize django database.

> doker-compose -f local.docker-compose.yaml up

To finally start django replace values and execute

> DB_NAME=django DB_USER=django DB_PASSWORD=password DB_HOST=localhost DB_PORT=5432 python manage.py makemigrations

don't forget to also call `migrate` and `createsuperuser`.

## References

### Kubernetes
* Kubernetes explanation: https://medium.com/swlh/pods-deployments-and-services-in-kubernetes-396e04e41e8
* Interactive tutorial: https://kubernetes.io/docs/tutorials/kubernetes-basics/
* Nginx Loadbalancer with affinity cookie: https://kubernetes.github.io/ingress-nginx/examples/affinity/cookie/
* 
