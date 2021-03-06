# MMM-Traffic
This a module for the [MagicMirror](https://github.com/MichMich/MagicMirror/tree/v2-beta). It can display commute time between two given addresses by car, walking, bicycling, or transit. The module uses the Google Maps Directions API to get commute time, which factors in traffic information.

## Installation
1. Navigate into your MagicMirror's `modules` folder and execute `git clone https://github.com/SamLewis0602/MMM-Traffic.git`. A new folder will appear, navigate into it.
2. Execute `npm install` to install the node dependencies.

## Usage
The entry in `config.js` can include the following options:

#### Required config options
You can get an api key [here](https://developers.google.com/maps/documentation/directions/).
```
api_key: 'your_apikey_here'
```
Address of starting/ending locations just as you would write them on an envelope, i.e. "123 North Main Street Chicago, Illinois 55555"
```
origin: 'origin_address_here',
destination: 'destination_address_here'
```
#### Optional
Mode of transportation, default is 'driving', can also be 'walking', 'bicycling', or 'transit'
```
mode: 'driving'
```
Nickname for the route to help clarify when you have multiple instances of the module, or if you just like the look of it.
```
route_name: 'Home to school'
```
Show the route's summary after the nickname, for example "Home to Work <b>via Route 1/Main St</b>". Default is true, but it won't show if you don't have a `route_name` in your config.
```
show_summary: true
```
What kind of traffic estimate you want, default is 'best_guess'. Can also be 'optimistic' or 'pessimistic'.
```
traffic_model: 'optimistic'
```
When `changeColor` is set to true, the color of the commute info will change based on traffic. If traffic increases the commute by 20%, the symbol and commute text will be yellow. An increase of 50% will change the color to red. If the traffic doesn't increase the commute by at least 20%, the color will be green. The default value for `changeColor` is false, leaving the symbol/text white.
```
changeColor: true
```
If you would like the commute info to change to yellow and red based on traffic but otherwise remain white, set `changeColor` to true and `showGreen` to false, like so:
```
changeColor: true,
showGreen: false
```
Update interval in milliseconds, default is 300000 (5 minutes)
```
interval: 120000 //2 minutes
```
The text used when loading the initial commute time.
```
loadingText: 'Loading commute...'
```
The text used in front of the commute time.
```
prependText: 'Current commute is'
```
Define the commute time language.
```
language: 'en' // By default it uses config.language;
```

Here is an example of an entry in `config.js`
```
{
	module: 'MMM-Traffic',
	position: 'top_left',
	classes: 'dimmed medium', //optional, default is 'bright medium', only applies to commute info not route_name
	config: {
		api_key: 'your_apikey_here',
		mode: 'driving',
		origin: '4 Pennsylvania Plaza, New York, NY 10001',
		destination: '1 MetLife Stadium Dr, East Rutherford, NJ 07073',
		route_name: 'Home to Work',
		changeColor: true,
		showGreen: false,
		traffic_model: 'pessimistic',
		interval: 120000 //2 minutes
	}
},
```

## Dependencies
- [request](https://www.npmjs.com/package/request) (installed via `npm install`)

## Important Notes
- This is my first project using Node, so feel free to submit pull requests or post on the issues/wiki and I will do my best to improve the project.

## Special Thanks
- [Michael Teeuw](https://github.com/MichMich) for creating the awesome [MagicMirror2](https://github.com/MichMich/MagicMirror/tree/v2-beta) project that made this module possible.
- [Paul-Vincent Roll](https://github.com/paviro) for creating the [Wunderlist](https://github.com/paviro/MMM-Wunderlist) module that I used as guidance in creating this module.
