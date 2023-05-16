<p align="center">
<a href="https://github.com/GarudaID/niiru-whatsapp-bot">
    <img src="https://raw.githubusercontent.com/GarudaID/niiru-whatsapp-bot/main/niiru-bot.jpg">
  </a>
	
<h1 align="center"> Niiru Bot WhatsApps
</h1>

<p align="center">
<a href="https://github.com/GarudaID"><img title="Owner" src="https://img.shields.io/badge/Owner-GarudaID-white.svg?style=for-the-badge&logo=github" width="170px"></a>

 <a href="https://github.com/GarudaID/niiru-whatsapp-bot/blob/main/LICENSE">
  
<img src='https://img.shields.io/github/license/GarudaID/niiru-whatsapp-bot?color=%231e81b0&style=for-the-badge' width="114px">

<p align="center">
<a href="https://github.com/FantoX001"><img title="Open Source" src="https://img.shields.io/badge/Open%20Source-YES-green.svg?style=for-the-badge" width="150px"></a>
<a href="https://github.com/FantoX001"><img title="" src="https://img.shields.io/badge/Maintained-YES-green.svg?style=for-the-badge" width="143px"></a>
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
	
<br>
	 
<h2 align="center">🔰 Meet Team Atlas 🔰
</h2>

[![Near Hoshinova](https://avatars.githubusercontent.com/u/48685463?v=4)](https://github.com/GarudaID)  | [![Ahmii-kun](https://github.com/Ahmii-kun.png)](https://github.com/Ahmii-kun) | [![Pratyush](https://github.com/pratyush4932.png)](https://github.com/pratyush4932) | [![Devime](https://github.com/Devime69.png)](https://github.com/Devime69) | [![Kai](https://github.com/Kai0071.png)](https://github.com/Kai0071) | [![JayJay Ops](https://github.com/jayjay-ops.png)](https://github.com/jayjay-ops)
----|----|----|----|----|----
[Near Hoshinova](https://github.com/GarudaID)  | [Ahmii Kun](https://github.com/Ahmii-kun) | [Pratyush](https://github.com/pratyush4932) | [Devime](https://github.com/Devime69) | [Kai](https://github.com/Kai0071) | [Jayjay Ops](https://github.com/jayjay-ops)
Owner, Main Developer, Maintainer, Dubugger  | Co-Developer, Co-Maintainer | Support Developer, Modules | Designing, API Maintainer | Ideas, Testing, Re-Checking | Ideas, Testing, Re-Checking
