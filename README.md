# stock-ml project  

## **CLC** - monolith to microservice  

---

### summary  
an originally monolithic stock price prediction project using django as a front end, mysql as a database and tensorflow for neural network predictions.

---

### repositories  
Following repositories are included within this one:

- [fabiankastner/stock-ml-web](https://github.com/fabiankastner/stock-ml-web)  
- [fabiankastner/stock-ml-db](https://github.com/fabiankastner/stock-ml-db)  
- [fabiankastner/stock-ml-data](https://github.com/fabiankastner/stock-ml-data)  
- [fabiankastner/stock-ml-nn](https://github.com/fabiankastner/stock-ml-nn)  
- [fabiankastner/stock-ml-config](https://github.com/fabiankastner/stock-ml-config)  

---

### folder structure  
``` 
stock-ml/
│
├── docker-compose.yml
│
├── stock-ml-web/
│
├── stock-ml-db/
│
├── stock-ml-data/
│
├── stock-ml-nn/
│
├── stock-config/
```

### setup

Clone Repo recursively with: `git clone https://github.com/fabiankastner/stock-ml --recursive`.

In case you have already cloned it, execute `git submodule init` and finally `git submodule update`.

### run  
> doker-compose up --build -d  
