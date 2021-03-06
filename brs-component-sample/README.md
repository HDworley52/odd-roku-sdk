# Odd Networks BRS Component Roku Sample App

### Running the sample-app on the Roku

#####1) Setup:
- First get an instance of oddworks up and running on your local machine: https://github.com/oddnetworks/oddworks (don't worry, it's easy!)
- Make sure your Roku is set up for development: https://blog.roku.com/developer/2016/02/04/developer-setup-guide/ Take note of your device password, you will need it later
- Create a copy this file: ```dev/targets/nasa/config/app_config.sample.json``` in the same folder
- Rename the copy to ```app_config.json```
- Add your roku x-access-token (found in the logs where you are running oddworks) to 'deviceAccessToken' and change the 'odd_service_endpoint' to your computer's IP address

#####2) Install using makefile:
```
> make install APPNAME=nasa ROKU_DEV_TARGET=roku_device_ip_address_here
```
You will be prompted for a password, enter your password from when you set up your Roku for development

To access the logs for debugging:
```
> telnet device_ip_address 8085
```

#####Screenshots and Manual build upload:
Open a browser and navigate to your Roku's ip address. Username: rokudev, Password: your_rokudev_password

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
