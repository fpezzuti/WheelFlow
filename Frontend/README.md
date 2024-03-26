# WheelFlow Frontend
Frontend android project for the application *WheelFlow*.

## Configuration
In order to the application to work, there are some configurations to apply.

Firstly a ngrok instance must be created by installing ngrok and then using the following command:
``` shell
ngrok http 5002
```

ngrok will respond by giving a "forwarding IP address" that must be set in some files of the android project:
- in *ContributorActivity* in the string *SERVER_IP*
- in *Utils* in string *url*

The *main.py* file in the server project must be run in order for the application to work.

## Activities
From the *main activity*, the WheelFlow's user can click on one of the three buttons:
- *Contribute*: goes to the *Contributor Activity* to **start contributing to the data collection**
- *Explore*: goes to the *Maps Activity* to **look on the map the accessibility** of the area where the user is at the moment
- *Route*: goes to the *Path Activity* to **find a path from source to destination and see the accessibility** of the path

### Contributor Activity
In the *contributor activity*, the user can contribute to the application by clicking on the *start button*:
- during the contribution the contributor user should put his phone into the trousers' pocket.
- the application will automatically collect vibration data using accelerometer, magnetometer, gyroscope and gps
- every 60 seconds data will be sent to the [Python server](./../PythonServer) hosted via _ngrok_.
- clicking on the *stop button*, the contribution will end and the remaining data will be sent to the python server.

### Maps Activity
In the *maps activity*, the user can see the set of landmarks (inaccessible points) that are present in the nearby. All the landmarks are stored in the server and will be automatically uploaded.

### Path Activity
From this activity the user can click a start point and a destination point in order to retrieve the path from source to destination and some information about the accessibility of the path. The routing request will be sent to the server that responds with the path (using google maps APIs) and with a set of additional information about the accessibility of the path (stored on the server).
