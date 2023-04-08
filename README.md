# HomeAssistant-FirstBus


[![installation_badge](https://img.shields.io/badge/dynamic/json?color=41BDF5&logo=home-assistant&label=integration%20usage&suffix=%20installs&cacheSeconds=15600&url=https://analytics.home-assistant.io/custom_integrations.json&query=$.first_bus.total)](https://github.com/hacs/integration)

Custom component built to bring you bus times for First Buses. This was built because buses in my area stopped having live times available in [UK Transport integration](https://www.home-assistant.io/integrations/uk_transport/), and time tabled based times were only available using the more expensive `nextbuses` call.

** WARNING: This component uses a private API used by [First Bus website](https://www.firstbus.co.uk/next-bus), so it could break at any time. I will do my best to keep the component working. **

## How to install

You should take the latest [published release](https://github.com/BottlecapDave/HomeAssistant-FirstBus/releases). The current state of `develop` will be in flux and therefore possibly subject to change.

To install, place the contents of `custom_components` into the `<config directory>/custom_components` folder of your Home Assistant installation. Once installed, don't forget to restart your home assistant instance for the integration to be picked up.

### HACS

[![hacs_badge](https://img.shields.io/badge/HACS-Default-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

This integration can be installed directly via HACS.

## How to setup

Setup is done entirely via the [UI](https://my.home-assistant.io/redirect/config_flow_start/?domain=first_bus).

### ATCO code

The `ATCO code` for your stop can be found in the same way that [UK Transport](https://www.home-assistant.io/integrations/uk_transport/) outlines.
    
1. On [OpenStreetMap.org](https://www.openstreetmap.org/) zoom right in on a bus stop you’re interested in.
2. Click the layers picker button on the right hand side.
3. Tick the ‘map data’ layer, and wait for clickable objects to load.
4. Click the bus stop node to reveal its tags on the left.

However, there have been reports of missing ATCO codes. Therefore alternatively, you can follow the following instructions:

1. Navigate to https://www.firstbus.co.uk/next-bus and type your location
2. Open up the development tools on your browser (usually F12) and go to the network tab
3. Click on the stop that your after and look at the network request. This should make a request to https://www.firstbus.co.uk/api/get-next-bus?stop=XXX. The value you're after will be in the response and also the value of XXX.

### Buses

`Buses` are the buses you want to filter to. If you want all buses from this stop, leave this blank. If you want multiple buses, these must be separated by commas.