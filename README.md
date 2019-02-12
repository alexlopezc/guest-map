# Guest Map
(ths is a fork from https://github.com/CodingGarden/guest-map)

* App detects users location (from browser or IP)
* Guests of the website can leave a message
* A pin will be added to the map with the users location and message

## Prerequisites:

In order to run this example wyou will need to install docker and docker-compose:
- https://docs.docker.com/install/ 
- https://docs.docker.com/compose/install/

## Brief introduction of the project

The project is composed of 3 services:
 - client: Single Page Application based on React that shows a map with all the messages stored in a db.
 - server: nodejs/express API server that receives all the requests from the client or any ther http client such as curl
 - database: Mongodb storing all the messages kept by the API.
 
The file docker-compose.yml allows the execution of the 3 services in different containers a exposes some ports in order to connect to the services: For example, the client listens in http://localhost:3000 and the server in http://localhost:5000

You can modify this file for listening in other ports if needed.

This is a development environemnt, where the react application is laucnhed using `react-scripts start`. For production you should build the react app and distribute it in any CDN like services (Netlify, Elastic Cloud Front) or with an nginx container base image.

## Run

Running this example is just a executing

```
docker-compose up
```

Point your browser to http://localhost:3000 and start storing messages.

There is also a simple example of how to use the api from a python script (ip_monitor.py)

## TODO

* [x] create-react-app
* [x] Install react-leaflet: https://github.com/PaulLeCam/react-leaflet
* [x] Get a map on the page!
* [x] Get the users location
  * [x] with the browser
  * [x] with their IP using an API
* [x] Show a pin at the users location
* [x] Show a form to submit a message
  * when form is submitted - POST /message
* [x] Setup server with create-express-api: https://www.npmjs.com/package/create-express-api
* [x] Add monk and joi
* [x] POST /messages
  * latitude
  * longitude
  * name
  * message
  * datetime
* [x] When the page loads get all messages
  * [x] GET /messages
* [x] Add pins to the map
* [x] Click a pin to see the message
* [x] DEPLOY!
  * [x] https://guestm.app
* Refactor React app
  * seperate components
  * seperate file for API requests
  * seperate file for Location requests

## Stretch
* [ ] Allow user to drag pin
* [ ] Login
* [ ] Users have their own guest map with their own markers and unique URL
