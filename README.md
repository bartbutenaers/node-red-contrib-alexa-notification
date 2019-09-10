# node-red-contrib-alexa-notification
Node-RED node to take control of your Alexa using the ```Notify Me``` skill, by sending it your own notifications.
NOTE: ```Notify Me``` is only available in the countries that allow English-speaking skills.

## Install
Run the following npm command in your Node-RED user directory (typically ~/.node-red):
```
npm install node-red-contrib-alexa-notifyme
```

## Node configuration

### Notification
This notification will be send to the Alexa device.  

Remarks:
There are two ways to send notifications: 
+ hard coding the notification in the node or 
+ sending the notification to the node in ```msg.payload```.

If you hard code the notification in the node, that notification will always be used no matter what you have in ```msg.payload```.

If you leave the 'notification' option empty in the node, then the contents of ```msg.payload``` will be sent. Valid msg.payload types are string', 'number', 'boolean', and 'timestamp'. 'JSON' and 'buffer' are not allowed.

When empty, the notification needs to be specified in ```msg.payload``` of the input message.

### Access code
```Access Code``` is ```required``` for communications with Alexa. See this <a target="_blank" href="https://www.thomptronics.com/about/notify-me">link</a> for detailed information how to get your own private access code.</p>

## Node Usage
The following flow can be used to test all the possible testcases. Make sure to read the comments because you will have to insert your Access Code into two of the node's instances and leave it out of the other two.
```
[{"id":"7ca37add.75fe24","type":"tab","label":"Alexa NotifyMe","disabled":false,"info":"test cases for the Alexa NotifyMe node"},{"id":"f69477a4.88a128","type":"alexa-notifyme","z":"7ca37add.75fe24","name":"","notification":"hard coded notification","x":530,"y":420,"wires":[["3d0a6c4c.18f1fc"]]},{"id":"f77d26b3.f61ec","type":"inject","z":"7ca37add.75fe24","name":"This is a string","topic":"","payload":"This is a string","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":110,"y":540,"wires":[["f69477a4.88a128"]]},{"id":"3d0a6c4c.18f1fc","type":"debug","z":"7ca37add.75fe24","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","x":830,"y":420,"wires":[]},{"id":"ef1c5dcd.c30cd","type":"inject","z":"7ca37add.75fe24","name":"blank string","topic":"","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":110,"y":420,"wires":[["f69477a4.88a128"]]},{"id":"73e5ecad.98be64","type":"inject","z":"7ca37add.75fe24","name":"boolean 'true'","topic":"","payload":"true","payloadType":"bool","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":110,"y":460,"wires":[["f69477a4.88a128"]]},{"id":"dd2ea589.37d068","type":"inject","z":"7ca37add.75fe24","name":"Number","topic":"","payload":"47.5","payloadType":"num","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":90,"y":580,"wires":[["f69477a4.88a128"]]},{"id":"125ccb44.c6e94d","type":"inject","z":"7ca37add.75fe24","name":"JSON","topic":"","payload":"{ \"name\":\"John\", \"age\":30, \"car\":null }","payloadType":"json","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":90,"y":700,"wires":[["f69477a4.88a128"]]},{"id":"1cc27740.d6ca39","type":"inject","z":"7ca37add.75fe24","name":"Buffer","topic":"","payload":"[72,101,108,108,111,32,87,111,114,108,100]","payloadType":"bin","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":90,"y":740,"wires":[["f69477a4.88a128"]]},{"id":"bd101000.f1bf1","type":"inject","z":"7ca37add.75fe24","name":"","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":100,"y":620,"wires":[["f69477a4.88a128"]]},{"id":"4f55135e.0d6344","type":"inject","z":"7ca37add.75fe24","name":"boolean 'false'","topic":"","payload":"false","payloadType":"bool","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":120,"y":500,"wires":[["f69477a4.88a128"]]},{"id":"baed133c.d0ef38","type":"alexa-notifyme","z":"7ca37add.75fe24","name":"No notification or Access Code","notification":"","x":570,"y":100,"wires":[["ab9d3b84.c39548"]]},{"id":"d9b2b88f.735bb8","type":"alexa-notifyme","z":"7ca37add.75fe24","name":"Hard coded notification but no Access code ","notification":"This is hard coded","x":610,"y":240,"wires":[["c1a7835f.41313"]]},{"id":"ab9d3b84.c39548","type":"debug","z":"7ca37add.75fe24","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","x":850,"y":100,"wires":[]},{"id":"d0d51fce.a586a8","type":"comment","z":"7ca37add.75fe24","name":"test case (1) no Access code no notification - result should be a message from the node saying \"No Access Code\"","info":"","x":470,"y":60,"wires":[]},{"id":"b7ab5adc.00e018","type":"inject","z":"7ca37add.75fe24","name":"blank string","topic":"","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":100,"wires":[["baed133c.d0ef38"]]},{"id":"58a241ca.85f93","type":"inject","z":"7ca37add.75fe24","name":"This is a string","topic":"","payload":"This is a string","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":140,"wires":[["baed133c.d0ef38"]]},{"id":"6dca28fc.14b45","type":"inject","z":"7ca37add.75fe24","name":"blank string","topic":"","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":240,"wires":[["d9b2b88f.735bb8"]]},{"id":"742d4c6a.a9dfb4","type":"inject","z":"7ca37add.75fe24","name":"This is a string","topic":"","payload":"This is a string","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":280,"wires":[["d9b2b88f.735bb8"]]},{"id":"c1a7835f.41313","type":"debug","z":"7ca37add.75fe24","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","x":850,"y":240,"wires":[]},{"id":"30a5d42d.36a0f4","type":"comment","z":"7ca37add.75fe24","name":"test case (2) no Access code Hard coded notification - result should be a message from the node saying \"No Access Code\"","info":"","x":500,"y":200,"wires":[]},{"id":"19a31725.f973c1","type":"comment","z":"7ca37add.75fe24","name":"test case (3) Access code and Hard coded notification - this should always send the hard coded notification","info":"","x":410,"y":340,"wires":[]},{"id":"78a159bc.3637b8","type":"comment","z":"7ca37add.75fe24","name":"bad data types - however the hard coded notification will be used","info":"","x":270,"y":660,"wires":[]},{"id":"8d758962.80d53","type":"alexa-notifyme","z":"7ca37add.75fe24","name":"","notification":"","x":520,"y":880,"wires":[["5171eae9.8a7ccc"]]},{"id":"4b973cf2.cf7304","type":"inject","z":"7ca37add.75fe24","name":"This is a string","topic":"","payload":"This is a string","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":1000,"wires":[["8d758962.80d53"]]},{"id":"5171eae9.8a7ccc","type":"debug","z":"7ca37add.75fe24","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","x":850,"y":880,"wires":[]},{"id":"28fe05a9.8b722a","type":"inject","z":"7ca37add.75fe24","name":"blank string","topic":"","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":880,"wires":[["8d758962.80d53"]]},{"id":"3a0c8e26.ebdf92","type":"inject","z":"7ca37add.75fe24","name":"boolean 'true'","topic":"","payload":"true","payloadType":"bool","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":920,"wires":[["8d758962.80d53"]]},{"id":"931aba63.7a57a8","type":"inject","z":"7ca37add.75fe24","name":"Number","topic":"","payload":"47.5","payloadType":"num","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":110,"y":1040,"wires":[["8d758962.80d53"]]},{"id":"1aace202.575296","type":"inject","z":"7ca37add.75fe24","name":"JSON","topic":"","payload":"{ \"name\":\"John\", \"age\":30, \"car\":null }","payloadType":"json","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":110,"y":1160,"wires":[["8d758962.80d53"]]},{"id":"28592b5f.f59174","type":"inject","z":"7ca37add.75fe24","name":"Buffer","topic":"","payload":"[72,101,108,108,111,32,87,111,114,108,100]","payloadType":"bin","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":110,"y":1200,"wires":[["8d758962.80d53"]]},{"id":"4c3026fe.3ed74","type":"inject","z":"7ca37add.75fe24","name":"","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":120,"y":1080,"wires":[["8d758962.80d53"]]},{"id":"da79f8ce.9cecb8","type":"inject","z":"7ca37add.75fe24","name":"boolean 'false'","topic":"","payload":"false","payloadType":"bool","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":140,"y":960,"wires":[["8d758962.80d53"]]},{"id":"5e19a90b.465d28","type":"comment","z":"7ca37add.75fe24","name":"test case (4) Access code and NO hard coded notification - this should use the msg.payload value if valid","info":"","x":400,"y":800,"wires":[]},{"id":"1b472c7b.65b5c4","type":"comment","z":"7ca37add.75fe24","name":"bad data types - this will not work","info":"","x":200,"y":1120,"wires":[]},{"id":"94a3bef2.3dfb38","type":"comment","z":"7ca37add.75fe24","name":"NOTE: before testing add your Access Code in this node","info":"","x":550,"y":841,"wires":[]},{"id":"28547840.62b5a8","type":"comment","z":"7ca37add.75fe24","name":"NOTE: before testing add your Access Code in this node","info":"","x":530,"y":380,"wires":[]}]
```

## Disclaimer
Remark: The icon made by <a href="https://www.flaticon.com/authors/those-icons" title="Those Icons">Those Icons</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/" title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a>
