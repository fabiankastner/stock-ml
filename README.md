# stock-ml project  

## **CLC** - monolith to microservice  

---

### summary  
an originally monolithic stock price prediction project using django as a front end, mysql as a database and tensorflow for neural network predictions.

---

### repositories  
clone the following repositories as the mentioned folder structure indicates  

- [fabiankastner/stock-ml](https://github.com/fabiankastner/stock-ml)  
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
├── docker-compose.yml(symlink)
│
├── stock-ml/
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

create a symlink as indicated in the folder structure

### run  
> doker-compose up --build -d  
