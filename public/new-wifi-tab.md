Summary of the proposals: [Summary](./new-wifi-tab-summary.md)

## Original state

What we started with is

![Original WiFi Tab Look](../pics/network-wifi-current.png)

## Minimal improvement

* First try for improving the look and feel of the wifi tab, was to re-arrange existing widgets to make new layout more transparent.
* Main change was to replace a combobox which currently stores list of ESSID by a table. Motivation was to have list of available wifi networks better visible.
* Rest of widgets should be filled according to which ESSID is selected

![Minimal WiFi Redesign](../pics/network-wifi-proposal.png)

## More improvements

* Here was motivation to use opportunity and improve the view a bit more
* Changes would be related to adding more details into network overview, like e.g. signal strength, to putting more details into Scan results - not only populate a list of available ESSIDs but also displaying some more details to make the choice easier for the user
* Add a button (e.g.) for activating connection explicitly. Currently we use the network which is active at time of clicking "Next" button. This can lead to unintended change of connection due to user's confusion.

![WiFi tab with network details](../pics/network-wifi-proposal_details.png)

* When user invokes Network Scan manually we can either populate the left column with results directly and left user to see details after clicking on particular essid name. This would require implementing a feature "Activate connection to selected network". Another possibility is to display a table with available networks overview and let user pick one as on following picture

	- Pros - filling left column directly
		- less dialogues to click through
	- Cons
		- when searching for a network which connect to and searching for more details user has to click through
	- Cons - additional overview Popup
		- additional dialogue, which might contain huge list with lot of columns
		- the solution can fall to previous solution when user doesn't want to change existing connection (or create new one) immediately

![Network scan result](../pics/network-wifi-scan_result.png)

* Another changes would be related to a workflow how yast parses wifi networks information

### Changes in workflow - Approach 1

* When wlan device is available in the system, yast performs network scan as a part of lan module startup.
* Pros:
	- list of networks (ESSIDs) would be available immediately once user switches to the WiFi tab. Scan network button could be used only when looking for changes
	- details of network would be loaded when particular network is selected
* Contras:
	- influences module startup time even when user doesn't want to touch wifi configuraion at all

### Changes in workflow - Approach 2

* WiFi network scan is postponed to the time when user switches to the WiFi Tab

* The network scan can be done automatically when (first time) switching to the WiFi Tab or (only) by explicitly clicking at Scan network button

* Pros:
	- no impact on startup time
	- close to the current behaviour

* Contras:
	- list of available networks / ESSIDs is not available when switching to the tab but the one which is potentialy currently in use
