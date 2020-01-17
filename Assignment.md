Deploying de environment
========================


Registration
------------

First, we need to run the `registration` service with *gradle*:

```shell
gradle registration:bootRun
```

![](https://i.imgur.com/dvKOS50.png)

The *Eureka* dashboard will be available at `http://localhost:1111`:

![](https://i.imgur.com/4n9UspC.png)


Account service
---------------

Then, we will run the account microservice. It will attach to `registration` automatically:

```shell
gradle accounts:bootRun
```

![](https://i.imgur.com/B6QngL8.png)

The *Account service* dashboard will be available at `http://localhost:2222`:

![](https://i.imgur.com/hjzDKvq.png)


Web service
-----------

Finally, we will run the web microservice. It will also attach to `registration` automatically:

```shell
gradle web:bootRun
```

![](https://i.imgur.com/gaxPCwn.png)

The *Web service* dashboard will be available at `http://localhost:3333`:
![](https://i.imgur.com/OrTA7eY.png)


Checking the deployment
-----------------------

Accessing `registration` dashboard will show that both accounts and web microservices are attached:

![](https://i.imgur.com/RqH7Fgg.png)

### Example account

We can check an account with the web, now that the deployment is ready:

![](https://i.imgur.com/o30w8iu.png)

![](https://i.imgur.com/6A8Ors0.png)



### Second account service

Now we can launch a second account service and we can expect that it will be attached to `registration`:

![](https://i.imgur.com/Jx80X56.png)

![](https://i.imgur.com/M5FDTUE.png)

If we access an account via the web interface, we can see that this second account service is being used:

![](https://i.imgur.com/x6dFurA.png)


### Killing the first account service

If we kill the process (as easy as pressing `Ctrl` + `C`), we can see that we still can retrieve the account:

![](https://i.imgur.com/b8tqPLc.png)

That's because `registration` is automatically balancing the services.