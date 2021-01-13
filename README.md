# stock-ml project  

## **CLC** - monolith to microservice  

---

### **summary**
an originally monolithic stock price prediction project using django as a front end, mysql as a database and tensorflow for neural network predictions.

---

### **repositories**
Following repositories are included within this one:

- [fabiankastner/stock-ml-web](https://github.com/fabiankastner/stock-ml-web)  
- [fabiankastner/stock-ml-db](https://github.com/fabiankastner/stock-ml-db)  
- [fabiankastner/stock-ml-data](https://github.com/fabiankastner/stock-ml-data)  
- [fabiankastner/stock-ml-nn](https://github.com/fabiankastner/stock-ml-nn)  
- [fabiankastner/stock-ml-config](https://github.com/fabiankastner/stock-ml-config)  

---

### **folder structure**

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

### **setup**

Clone Repo recursively with: `git clone https://github.com/fabiankastner/stock-ml --recursive`.

In case you have already cloned it, execute `git submodule init` and finally `git submodule update`.

### **run**

Non-prefixed docker-compose.yaml file only here for legacy reasons, to be removed soon.

#### **production**

*TODO*

Made for production, debug modes disabled, hardened.

> doker-compose -f prod.docker-compose.yaml up

### **development**

Suited for development, source code files of web service mapped into container to utilize django hot reload.

> doker-compose -f dev.docker-compose.yaml up

### **local**

If you want to start django non-containerized on the host machine, but everything else should be available via docker.
As same volumes as in development are used, this can be utilized to initialize django database.

> doker-compose -f local.docker-compose.yaml up

To finally start django replace values and execute

> DB_NAME=django DB_USER=django DB_PASSWORD=password DB_HOST=localhost DB_PORT=5432 python manage.py makemigrations

don't forget to also call `migrate` and `createsuperuser`.