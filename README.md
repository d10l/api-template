# $APINAME

This is the template for creating APIs locally and deployed on Kubernetes & Istio.

## Repository Structure

* `Dockerfile`: running the service just do a `docker run`
* `docker-compose.yml`: starts your development setup including the swagger editor as well as a mock server based on the `swagger.yaml` file located in `/swagger`/ directory
* `/api`: including the python modules for the api implementation (described in the sections below)
* `/lib`: includes currently only the library which implements a customer token validation. 
* `/devops`: includes the *script to build and deploy* and the *istio config*

### Develop

You either can work with the `Dockerfile` which includes all the commands to start the server or you develop locally. I suggest you use [skaffold](https://github.com/GoogleContainerTools/skaffold#skaffold-dev) - the installation instructions you find using the link.  

1. Create your swagger file including examples (they are used for the mock) and place it under `/swagger/swagger.yaml`
2. Setup your environment by doing 
```bash
virtualenv venv --python=python3
source venv/bin/activate
# install pylint
pip install pylint
pip install -r requirements.txt
```
If you use visual studio code do this first in your terminal window and then open the folder again with `code .`.
1. Then start the connxion mock server based on the swagger file: `connexion run swagger/swagger.yaml --mock=all`
1. Validate this with your customers like external API developers and your frontend developer and improve the API. 
1. Then implement the API resources and methods under `api`. 


## Developer a docker microservice in Python

1. Check that you have have a local docker environment in [Plattform](../plattform.md) -&gt; Setup Docker Environment.
2. Create Dockerfile and docker-compose that starts the Mock Server\([Code](https://github.com/denseidel/products-marketplace-service/commit/6303f0ba152be610dc4fabcf85d624a4e32faa31)\) - make sure the Swagger  file does not include custom functions like `x-tokenInfoFunc`. **TODO create it for the mock** 
   * [Environment Variables to connect to AWS](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)
3. Implement Frontend against mocks
4. Update Dockerfile to production config
5. Implement API \(including DB, ...\)

Connexion Examples:

* [https://github.com/hjacobs/connexion-example](https://github.com/hjacobs/connexion-example)
* [https://github.com/ssola/python-flask-microservice](https://github.com/ssola/python-flask-microservice)
* [http://blog.bejanalex.com/2017/03/mongodb-rest-api-interface-in-docker/](http://blog.bejanalex.com/2017/03/mongodb-rest-api-interface-in-docker/)

Create a client library for the API:

* [https://realpython.com/blog/python/api-integration-in-python/](https://realpython.com/blog/python/api-integration-in-python/)

Use Feature flags:

* [https://featureflags.io/python-feature-flags/](https://featureflags.io/python-feature-flags/)

Python Testing:

* Unit Testing
* Mocks
* Code Coverage

Python Functional Programming:

* [https://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming](https://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming)

Python Clean Code:

* [http://pythonforengineers.com/writing-great-code/](http://pythonforengineers.com/writing-great-code/)
* [https://github.com/zedr/clean-code-python](https://github.com/zedr/clean-code-python)
* [https://github.com/rmariano/Clean-code-in-Python/blob/master/build/Clean code in Python.pdf](https://github.com/rmariano/Clean-code-in-Python/blob/master/build/Clean%20code%20in%20Python.pdf)
* [http://docs.python-guide.org/en/latest/writing/reading/](http://docs.python-guide.org/en/latest/writing/reading/)



Benefits API First:

![](/img/advantages-of-api-first.png)

[https://github.com/swagger-api/swagger-codegen/wiki/server-stub-generator-howto\#python-flask-connexion](https://github.com/swagger-api/swagger-codegen/wiki/server-stub-generator-howto#python-flask-connexion)

[http://connexion.readthedocs.io/en/latest/cli.html](http://connexion.readthedocs.io/en/latest/cli.html)

[https://blog.runscope.com/posts/openapi-swagger-resource-list-for-api-developers](https://blog.runscope.com/posts/openapi-swagger-resource-list-for-api-developers)

[https://medium.com/ibm-data-science-experience/deploy-your-python-functions-as-a-rest-api-811981ec7ec5](https://medium.com/ibm-data-science-experience/deploy-your-python-functions-as-a-rest-api-811981ec7ec5)

[https://github.com/zalando/connexion](https://github.com/zalando/connexion)

[http://michal.karzynski.pl/blog/2016/06/19/building-beautiful-restful-apis-using-flask-swagger-ui-flask-restplus/](http://michal.karzynski.pl/blog/2016/06/19/building-beautiful-restful-apis-using-flask-swagger-ui-flask-restplus/)

[https://cidrblock.github.io/zero-to-api-in-4-minutes.html](https://cidrblock.github.io/zero-to-api-in-4-minutes.html)

Beispiel: [https://github.com/hjacobs/connexion-example](https://github.com/hjacobs/connexion-example)

### Develop API First in Python

Get started with Connextion: [http://connexion.readthedocs.io/en/latest/quickstart.html](http://connexion.readthedocs.io/en/latest/quickstart.html)

[https://github.com/zalando/connexion](https://github.com/zalando/connexion)

[https://github.com/hjacobs/connexion-example](https://github.com/hjacobs/connexion-example)

[https://cidrblock.github.io/zero-to-api-in-4-minutes.html](https://cidrblock.github.io/zero-to-api-in-4-minutes.html)

[https://github.com/ssola/python-flask-microservice/blob/master/api/room.py](https://github.com/ssola/python-flask-microservice/blob/master/api/room.py)

[https://medium.com/@ssola/building-microservices-with-python-part-i-5240a8dcc2fb](https://medium.com/@ssola/building-microservices-with-python-part-i-5240a8dcc2fb)

[http://coderobot.downley.net/swagger-driven-testing-in-python.html](http://coderobot.downley.net/swagger-driven-testing-in-python.html)

[https://uwsgi-docs.readthedocs.io/en/latest/](https://uwsgi-docs.readthedocs.io/en/latest/)

[http://connexion.readthedocs.io/en/latest/routing.html](http://connexion.readthedocs.io/en/latest/routing.html)

* [https://medium.com/@ssola/building-microservices-with-python-part-i-5240a8dcc2fb](https://medium.com/@ssola/building-microservices-with-python-part-i-5240a8dcc2fb)
* [https://github.com/hjacobs/connexion-example/blob/master/app.py](https://github.com/hjacobs/connexion-example/blob/master/app.py)
* [http://connexion.readthedocs.io/en/latest/request.html](http://connexion.readthedocs.io/en/latest/request.html)
* Check a token: [https://auth0.com/docs/api-auth/tutorials/verify-access-token](https://auth0.com/docs/api-auth/tutorials/verify-access-token)

API Sources / public api collection: [https://any-api.com](https://any-api.com)

[https://www.programmableweb.com/apis/directory](https://www.programmableweb.com/apis/directory)

[https://apis.guru/browse-apis/](https://apis.guru/browse-apis/)




### Deploy and Run

It is suggested to use the docker container for your deployment using the container runtime of your choice.

We save the environment config: 

```
# config for mongodb
export MONGODB_URL= mongodb://sampleUser:samplePassword@localhost:27017/identities // mongodb://mongodb:27017/test
export MONGODB_USERNAME=sampleUser
export MONGODB_PASSWORD=samplePassword
export MONGODB_ROOT_PASSWORD=samplePassword
# config apigee
export apigee_client_id=user@sample.com
export apigee_client_secret=samplePassword
export apigee_management_endpoint=https://api.enterprise.apigee.com/v1/organizations/denseidel-trial
export apigee_auth_endpoint=https://login.apigee.com/oauth/token
#config auth0
export auth_client_id=dsfdfndfernd34fdfn3234djfdf
export auth_client_secret=ldfjn3f3o23nf23lfj0j23fn2lfn23nf232nf23nf2nfn32fn2ffn2
export auth0_endpoint=https://d10l.eu.auth0.com
```


Connect to Istio MongoDB with port forwarding

```
kubectl -n default port-forward \
$(kubectl -n default get pod -l app=mongodb -o jsonpath='{.items[0].metadata.name}') \
27017:27017 &
```