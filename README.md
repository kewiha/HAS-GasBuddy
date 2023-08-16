# HAS-GasBuddy
Home Assistant sensor, templates and dashboard to display nearby gas prices from GasBuddy. 

Very limited testing has been done. Expect troubleshooting.

# Acknowledgements
* [JimSt24/home-assistant](https://github.com/JimSt24/home-assistant/) was used as a starting point, and thus was fundamental to this work.

# Installation 
The files/directories in this repo are to be installed in the same path as your configuration.yaml, and require customization to work.

## configuration.yaml.stub ##
If sensor: and template: are not already defined in Home Assistant's configuration.yaml (directly or in a file included in it), then the stub can be appended to the end of the existing configuration.yaml.
## sensors/gasbuddy_stations_nearby_info.yaml ##
Replace all instances of YOURPOSTALCODE with a postal code recognized by gasbuddy. Canadian postal codes can be input like so: A1BC2D
## templates/* ##
Replace all instances of YOURCURRENCY with the currency provided by gasbuddy (e.g. CAD in Canada).

Consider replacing instances of `minutes: '*'` with `minutes: 0` or any unsigned integer below 60 once intial setup and testing is complete. This may increase the time until valid results are available when Home Assistant is (re)started, but reduce overhead trivially.

Templates are hard-coded to only look at the first price listed at each station. This is typically regular gas. For higher grades, diesel, and more robustness, see how fuels were implemented in [JimSt24/home-assistant's gas_stations.yaml](https://github.com/JimSt24/home-assistant/blob/main/config/templates/gas_stations.yaml).

## dashboard.yaml ##
Create a new dashboard, take ownership, and use the "Raw Configuration Editor" for the entire dashboard to enter the provided yaml. 

The sensor graphs plot the daily price trends reported by GasBuddy over the last week and provide the current day's value (updated hourly). The cheapest and closest entity cards report the top 3 gas stations in each category (updated hourly).

![example picture of dashboard for postal code M7A2K1](https://github.com/kewiha/HAS-GasBuddy/blob/main/dashboard.PNG?raw=true)
