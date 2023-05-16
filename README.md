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
