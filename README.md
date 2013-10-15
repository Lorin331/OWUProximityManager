# OWUProximityManager

Detect and connect to nearby devices with iBeacons and CoreBluetooth.

## Sample Project

To simulate entering a defined region, select Client on one device, **then** select Server on the other. As the devices will likely be next to eachother when the exchange takes place, it's likely that the Client device will enter the region, range the server and establish a connection pretty quickly.

![home](Screenshots/home.png) ![server](Screenshots/server.png) ![client](Screenshots/client.png)

## Usage
Just, create a few UUIDs for `OWUProximityManagerConstants.h`, `#import OWUProximityManager.h` and call `[[OWUProximityManager shared] startupClientWithDelegate:delegate]` or `[[OWUProximityManager shared] startupServerWithDelegate:delegate]` 

Server Setup:
`[[OWUProximityManager shared] startupServerWithDelegate:delegate]`

Client Setup:
`[[OWUProximityManager shared] startupClientWithDelegate:delegate]
[OWUProximityManager shared].desiredProximity = CLProximityImmediate \\ defaults to CLProximityNear`

Two things:
- `locationManager:DidEnterRegion:` and therefor `proximityClientDidEnterBeaconRegion` will not be called if the Client starts while already in range of the Server
- `locationManager:DidExitRegion:` and the resulting `proximityClientDidExitBeaconRegion` will not be called until about a minute after exiting the region ([dev forum link](https://devforums.apple.com/message/898335#898335))

## ToDo's
- More fine tuning of BeaconRegion measured power
- Handle invalidated services in `OWUProximityServer`
- Properly handle return from local notification
- And moar.
- Suggestions, issues and pull requests are more than welcome.

## License
OWUProximityManager is available under the MIT license. See the LICENSE file for more info.
