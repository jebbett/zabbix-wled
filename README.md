# zabbix-wled
Zabbix Media Type to trigger basic alerts to WLED

**IMPORTANT: EVERYTHING IS CASE SENSITIVE, you must complete steps 1-3 below.**

1. Set "IPAddress" above to your WLED strip, WLED should be updated to the latest version.
EXAMPLE: 192.168.1.123
2. Update "HostsList" with your servers host name as specified in Zabbix, if you need to allocate two sections of the strip to 1 server (i.e. both sides of the rack) then list the server twice.
EXAMPLE: 'Server1','Server2','Server2'
3. Update "LEDRanges" for each of the hosts mentioned above, the first LED is LED 1, each host entry requires a start and an end LED number. [Start,End]
EXAMPLE: [8,18],[26,29],[48,51]
4. Set custom colours if you require, colours are in standard RGB format
5. The "DefaultColour" is set when an item is reported as "recovering" (NOTE: event_value = 1 for problem, 0 for recovering)

**Example how to use this Media Type:**
1. Add the media type to your user (Administration > Media Users > [User] > Media)
2. Enable an action to trigger events i.e. enable Configuration > Actions >  "Report problems to Zabbix administrators" with an operation type of "Send Message" and for "Recovery operations" you can use "Notify all involved"

**Limitations:**
1. This only outputs to the first segment of an LED strip (if you are using a segments in WLED)
2. It does not retain alerts if WLED triggers a different effect.
3. If a host has two alerts then only the latest alert will be represented 
