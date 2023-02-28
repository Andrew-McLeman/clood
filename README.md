
<img src="https://raw.githubusercontent.com/RGU-Computing/clood/master/images/CloodV2.png" width="400">

*Clood CBR: Towards Microservices Oriented Case-Based Reasoning*

<img src="https://img.shields.io/badge/version-2.0.0-brightgreen" alt="Version"/>

### 🚀 Version 2 Released!


# What is Clood? 
*(its **Cloud** in Scottish dialect)*


Case-based Reasoning (CBR) applications have been widely deployed across various sectors, including pharmaceuticals, defense, aerospace, IoT, transportation, poetry, and music generation. However, a significant proportion of these applications have been developed using monolithic architectures, which present size and complexity constraints. Consequently, these applications face barriers to the adoption of new technologies, and changes in frameworks or languages directly impact them, making them prohibitively expensive in terms of time and cost. To tackle this challenge, **we have developed Clood CBR, a distributed and highly scalable generic CBR system based on a microservices architecture.** By splitting the application into smaller, interconnected services, Clood CBR can scale to meet varying demands. Microservices are cloud-native architectures that have become increasingly popular with the rapid adoption of cloud computing. Therefore, the CBR community can benefit from a framework such as Clood CBR at this opportune time.


[CloodCBR Paper Published at ICCBR 2020](https://rgu-repository.worktribe.com/output/895530/clood-cbr-towards-microservices-oriented-case-based-reasoning) 📄 

[CloodCBR Presentation and Demo from ICCBR 2020](https://www.dropbox.com/s/i4vadj9c0dkwrsn/Clood%20CBR%20Final%20-%20ICCBR%202020.mp4?dl=0) ▶️ 

[Adapting Semantic Similarity Methods for Case-Based Reasoning in the Cloud from ICCBR 2022](https://rgu-repository.worktribe.com/output/1706158/adapting-semantic-similarity-methods-for-case-based-reasoning-in-the-cloud) 📄 

### Cite CloodCBR
```bib
@inproceedings{cloodcbr,
  title={Clood CBR: Towards Microservices Oriented Case-Based Reasoning},
  author={Nkisi-Orji, Ikechukwu and Wiratunga, Nirmalie and Palihawadana, Chamath and Recio-Garc{\'\i}a, Juan A and Corsar, David},
  booktitle={International Conference on Case-Based Reasoning},
  pages={129--143},
  year={2020},
  organization={Springer}
}
```

### What's new in Clood CBR Version 2
#### Core Updates
- Semantic SBERT
- Explanation API - Extracts the field names and local similarity values from explanations.
- Minor normalisation fixes (e.g. mcsherry, inerca)
- Array datatype functionality
- Complete docker support
- JWT Token based API authentication

#### Dashboard Updates
- Login Authentication support
- Visual case representation (Parallel Cordinates)
- Export functionality for retrievals
- Import CSV  validation and templating
- Add single cases from dashboard support
- Explanations added for similarity types
- Manage JWT Tokens


## Project Components

### Implementation Architecture

<img src="https://raw.githubusercontent.com/RGU-Computing/clood/master/images/clood_architecture.jpg">

## Clood Structure and Technologies
- Serverless Functions - REST API for communication from client apps (Serverless Framework with Python functions)
- Client - This is the demonstration dashboard (AngularJS)
- Elasticsearch - Managed ES service used as casebase 

### Serverless Functions

Project is available in the ```serverless-functions``` folder of the repository.

### Elasticsearch
For the Clood implementation we have used [AWS Elasticsearch service](https://aws.amazon.com/elasticsearch-service/).

## Start Using Clood? 🚀

### Local Development

We have simplified the entire CloodCBR development environment. You can easily start developing Clood CBR using the containarised environment now. Make sure you have [Docker](https://docs.docker.com/get-docker/)  installed.

Once cloned this repo you just have to run the following commands

Copy the default Configuration files:
```
cp dashboard/app/env.sample.js dashboard/app/env.js && cp api/config.sample.py api/config.py && cp other-services/ontology-sim/config.sample.py other-services/ontology-sim/config.py && cp other-services/semantic-sim/config.sample.py other-services/semantic-sim/config.py
```

Create the docker containers and run
```
docker compose up --build
```

Development Ports

- CloodCBR Dashboard - [http://localhost:8000/](http://localhost:8000/)
- CloodCBR API - [http://localhost:3000/](http://localhost:3000/)
- OpenSearch Dashboard - [http://localhost:5601/](http://localhost:5601/)
- OpenSearch API - [http://localhost:9200/](http://localhost:9200/)
- Clood USE Vectoriser API - [http://localhost:4100/](http://localhost:4100/)

### Deployment
### OpenSearch (Formerly ElasticSearch in AWS) 
Follow the guide [Here](https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-createupdatedomains.html) on getting started with Elasticsearch in AWS. All you need next is the ES url and the AWS access keys.

### Serverless functions (API)

We have built Clood with the [serverless](https://serverless.com/) framework which is a used deploy and test serverless apps across different cloud providers. The example installation here will be for AWS.

1. Make sure you have installed and setup serverless framework globally. [Guide](https://serverless.com/framework/docs/getting-started/)

2. Install Dependenices from CLI
```
npm install
```

3. Update the serverless.yml file as required. (Eg. region, service name..)

4. Add a conf.py file with the following structure

```python
aws = {
    "host": 'CLOUDSEARCH AWS URL', # domain.eu-west-1.es.amazonaws.com
    "region": 'eu-west-1',
    "access_key":   '',
    "secret_key": ''
}
```

4. Simply deploy now, it will package and run in CLI
```
serverless deploy
```

* Make sure that [docker](https://docs.docker.com/get-docker/) is running in your computer when deploying (it is required to package the python dependencies)

### API endpoints

End-point | Request Method | Description
--- | --- | ---
/project | HTTP GET | Retrieves all the CBR projects
/project/{id} | HTTP GET | Retrieves a specific CBR project with specified id
/project | HTTP POST | Creates a new CBR project. The details of the project are included as a JSON object in the request body
/project/{id} | HTTP PUT | Updates the details of a CBR project. Modifications are included as a JSON object in the request body
/project/{id} | HTTP DELETE | Removes a CBR project with specified id
/case/{id}/list | HTTP POST | Bulk addition of cases to the casebase of the project with specified id. Cases are included in the request body as an array of objects
/retrieve | HTTP POST | Performs the case retrieve task
/retain | HTTP POST | Performs the case retain task
/config | HTTP GET | Retrieves the system configuration
/config | HTTP POST | Adds or updates the system configuration


### Client Dashboard

The Client Dashboard demonstrates the use of Clood through API calls to create and configure projects and perform CBR tasks. Project is available in the ```dashboard``` folder of the repository. The readme at ```dashboard``` describes how to instal the client dashboard.

<img src="https://raw.githubusercontent.com/RGU-Computing/clood/master/images/screenshots/client_projects.png">

Guide to install and use the Clood Dashboard is available in the /dashboard folder. [Clood Dashboard](https://github.com/RGU-Computing/clood/tree/master/dashboard)



## License

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/RGU-Computing/clood">Clood CBR: Towards Microservices Oriented Case-Based Reasoning</a> by <span property="cc:attributionName">Nkisi-Orji, Ikechukwu; Wiratunga, Nirmalie; Palihawadana, Chamath; Recio-García, Juan A.; Corsar, David; Robert Gordon University Aberdeen</span> is licensed under <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International<br><img width="22px" style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img width="22px" style="width:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"></a></p>

----
Repo Maintained by [Ikechukwu Nkisi-Orji (RGU)](https://github.com/ike01), [Chamath Palihawadana (RGU)](https://github.com/chamathpali) and [Andrew McLeman (RGU)](https://github.com/Andrew-McLeman)
