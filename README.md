<p align="center">
<a href="https://github.com/GarudaID/niiru-whatsapp-bot">
    <img src="https://raw.githubusercontent.com/GarudaID/niiru-whatsapp-bot/main/niiru-bot.jpg">
  </a>
	
<h1 align="center"> Niiru Bot WhatsApps
</h1>

<p align="center">
<a href="#"><img title="Niiru Bot Multi Device." src="https://img.shields.io/badge/Niiru Bot Multi Device.-green?colorA=%1CF336&colorB=%23ff0000&style=for-the-badge"></a>
</p>

<p align="center">
<a href="https://github.com/GarudaID"><img title="Owner" src="https://img.shields.io/badge/Owner-GarudaID-white.svg?style=for-the-badge&logo=github" width="170px"></a>

 <a href="https://github.com/GarudaID/niiru-whatsapp-bot/blob/main/LICENSE">
  
<img src='https://img.shields.io/github/license/GarudaID/niiru-whatsapp-bot?color=%231e81b0&style=for-the-badge' width="114px">

<p align="center">
<a href="https://github.com/GarudaID"><img title="Open Source" src="https://img.shields.io/badge/Open%20Source-YES-green.svg?style=for-the-badge" width="150px"></a>
<a href="https://github.com/GarudaID"><img title="" src="https://img.shields.io/badge/Maintained-YES-green.svg?style=for-the-badge" width="143px"></a>
</p>
<br>

Niiru is a nodejs module which allows you to connect with whatsapp web by using Puppeteer.

It is not an official whatsapp module so I am not responsible for any ban. Although I have tried a lot and have not been banned, I cannot guarantee that this is the case for everyone or that in the future restrictions will apply to prevent its use.

# Installation

    npm i niiru

NOTE: Node 10.15.0+ is required

## Plugins 

The creation of new plugins is allowed to automate some tasks and achieve incorporation as a new method of the niiru class.

To create a new plugin it is required to export an object with the following properties:

 - **Id**: Plugin identifier (name)
 - **setup**: Initial configuration function with configuration parameters (optional function)
 - **plugin**: Function that contains the actions to be performed by the plugin, this function will have access to all the methods of the niiru function by using "this"

Once the plugin is created, the "plugins" parameter must be configured at the time of instantiating niiru through intentsConfig, then the possible modules to be used by the plugin must be installed separately through the console by "npm install module_name".

## Supported features

| Feature  | Status |
| ------------- | ------------- |
| Send messages  | ✅  |
| Receive messages  | ✅  |
| Send media (images/audio/documents)  | ✅  |
| Send media (video)  | ✅  |
| Send stickers | ✅ |
| Send stickers without background | ✅ |
| Receive media (images/audio/video/documents)  | ✅  |
| Send contact cards | ✅ |
| Send location | ✅ |
| Receive location | ✅ | 
| Message replies | ✅ |

## Example usage

```js
const niiru = require('niiru');

const niiru = new niiru();

// Default when no assignment is found for the message
niiru.on('message', (res) => {
    if (res.data.type === 'document' || res.data.type === 'video'){
        niiru.sendMessage({
            "idChat": res.data.from,
            "message": `Thanks for your file.`
        });

        niiru.downloadFile(res.data.id)
        .then((file) => {
            console.log('file downloaded...', file);
        })
        .catch((err) => {
            console.log('error downloading file', err);
        })
    } else {
        niiru.sendMessage({
            "idChat": res.data.from,
            "message": `You say: ${res.data.body}`
        });
    }
});

niiru.on('ready', (session) => {
	console.log('READY', session);
    //console.log('Clossing Session');
    //niiru.closeSession();
});

niiru.start(); 
```
	 
**intentsConfig**: 
```json
{
	"showContent": false,
	"debug": false,
	"removeBgApis": [],
	"plugins": {
        "folder": "../plugins",
        "plugins": [],
        "setup": {}
    },
	"executions": {
		"reponseUsers": true,
		"simulateTyping": true,
		"timeSimulate": 3000,
		"contorlExecutions": false,
		"maxExecutions": 30,
		"timeInterval": 10,
		"timePending": 3,
		"sendSeen": true,
		"sendSeenFull": false,
		"intervalSendSeen": 10
	},
	"bann": {
		"active": false,
		"timeInterval": 10,
		"maxBann": 3,
		"timeBann": 10,
		"timeInactive": 5,
		"whiteList": []
	},
	"messages":{
		"userBanned": "⛔😡 *Kami melaporkan bahwa Anda telah diblokir sementara karena menyalahgunakan layanan kami * \n _Silakan coba lagi setelahnya {{TIMEBANN}} minutes_ 🤬",
		"groupBanned": "⛔😡 *Kami melaporkan bahwa grup ini telah diblokir sementara karena penyalahgunaan layanan kami oleh '{{USER_NAME}}' (+ {{USER_NUMBER}}) * \n _Silakan coba lagi setelahnya {{TIMEBANN}} minutes_ 🤬",
		"privileges": "⛔ *Sayangnya Anda tidak memiliki hak istimewa, hubungi administrator sistem* ⛔"
	},
	"blocked": [],
	"whiteList": [],
	"commands": []
}
```
	
<br>
	 
<h2 align="center">🔰 Meet GarudaID 🔰
</h2>

[![Near Hoshinova](https://avatars.githubusercontent.com/u/48685463?v=4)](https://github.com/GarudaID)  | [![Riki-Kun](https://i.pinimg.com/750x/6b/4d/46/6b4d46511bce2c4cab8d0fc9eac64e00.jpg)](https://github.com/) | [![Dreyaan](https://avatars.githubusercontent.com/u/79951121?v=4)](https://github.com/Dreyaan) | [![Qalmurri](https://avatars.githubusercontent.com/u/86642474?v=4)](https://github.com/qalmurri) | [![Dayat-MD](https://pps.whatsapp.net/v/t61.24694-24/312232660_560313218864801_8972370498920019313_n.jpg?ccb=11-4&oh=01_AdRo0VI6ufcmVu-pSM8rXZxryaeZovPPNuQ3gxy7w0nLdw&oe=6469793E)](https://github.com/) | [![??](https://st3.depositphotos.com/3581215/18899/v/600/depositphotos_188994514-stock-illustration-vector-illustration-male-silhouette-profile.jpg)](https://github.com/)
----|----|----|----|----|----
[Near Hoshinova](https://github.com/GarudaID)  | [Riki-Kun](https://github.com/) | [Dreyaan](https://github.com/Dreyaan) | [Qalmurri](https://github.com/qalmurri) | [Dayat-MD](https://github.com/) | [??](https://github.com/)
Owner, Main Developer, Maintainer, Dubugger  | Co-Developer, Co-Maintainer | Support Developer | Support Developer | Support Developer | ???
	 
## Disclaimer

This module is not official WhatsApp so you must be careful with the number of interactions per minute to avoid possible bans, this module has the option of queuing responses to avoid such a situation but does not ensure that actions cannot occur on the part of the company.

This project is inspired by [Wbot](https://github.com/vasani-arpit/WBOT) I just dedicate myself to adding new options to it.
