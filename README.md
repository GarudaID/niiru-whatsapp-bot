### Niiru Bot WhatsApps

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
