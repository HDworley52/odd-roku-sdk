# Odd Networks Roku App

### Running the sample-app on the Roku

#####Setup
- Create a copy this file: ```dev/targets/nasa/config/app_config.sample.json``` in the same folder
- Rename the copy to ```app_config.json```
- Add your x-access-token to 'deviceAccessToken' and change the 'odd_service_endpoint' to your computer's IP address
- Make sure you have an instance of oddworks up and running on your local machine: https://github.com/oddnetworks/oddworks

#####Install using makefile:
```
> make install APPNAME=nasa ROKU_DEV_TARGET=roku_device_ip_address_here
```
You will be prompted for a password, the password is: _rokudev_

To access the logs for debugging:
```
> telnet device_ip_address 8085
```

#####Screenshots and Manual build upload:
Open a browser and navigate to your Roku's ip address. Username: _rokudev_ Password: _rokudev_

### Deep Linking

####Param names for request from deep link:
- videos & livestreams: contentID=content_id_here&mediaType=video/livestream_here
- videoCollections: mediaType=videoCollections&collectionID=collection_id_here
- video inside a video collection: contentID=content_id_here&mediaType=videoCollections&collectionID=collection_id_here

Local Deeplink to a video example:
```
curl -d '' "http://your_roku_ip_here:8060/launch/dev?contentID=your_content_id_here&mediaType=videos"
```

Notes:
- *media types have an 's' at the end unless a livestream*
- *Deep link content shown before home page, when user backs out, home page loads*
