## Projects list (old)
I thought it would be a good idea to document the projects I recently started (but not necessarily completed). Newer ones listed first. Some of the bigger projects might get special in-depth posts of their own (later…)

- Solar powered Raspberry Pi ‘monitoring station’ – $5 200W panels + MPPT charge controller + unused safe + RPi 2B + RTL-SDR v3 (incl. LNA, V-dipole on a bamboo pole) + camera(s). Web servers running – motion (stream + motion detection), dump1090-fa (ADS-B plane tracking), graphs1090 (ADS-B + system info). Some lessons learnt:
    - MPPT is a must & don’t trust eBay listings (if it’s <$50 it’s probably PWM). Otherwise I lose half the power because of the 24V panel and 12V battery mismatch
    - Raspberry Pi behaving weirdly? Check the power supply
You have to manually activate the bias tee every time you start the RTL-SDR! Otherwise that unpowered LNA is dead weight (spent a few days confused about this, thought the FM bandstop filter was to blame)
    - Add ventilation holes to the enclosure (luckily it’s winter right now)
- BLE Smartwatch reverse engineering – still ongoing. Bought a cheap v-fitness branded smartwatch, thought it would be interesting to do some RE and make my own app so I don’t have to trust the Play Store version which requests a lot of permissions.
    - Lots of issues with gattacker, choosing a suitable adapter for sniffing and so on
    - Ended up grabbing a $10 BBC micro:bit off eBay which coupled with this brilliant software makes things workable
    - More info in another post (update: nope)
- Telstra Air WiFi – big idea was to leech off the WiFi from the pink Telstra payphones, essentially giving unlimited internet for $5 (cheapest Telstra data plan was on discount)
    - $10 15dBi Yagi from eBay – good sector antenna (radome enclosed), picked up a lot of the nearby Telstra Air/Fon WiFi home hotspots (limited to an unbearable 2Mbps)
    - Underestimated my distance to the nearest payphone (1.6km RF LOS, oops). Plugged the values into a free space path loss calculator and it’s just physically impossible unless I have a point to point link
    - Turns out the payphones are not fiber connected, speedtest only shows ~8Mbps anyway…
- Telstra SMS Qt – desktop app to talk to the Telstra Messaging API, sends & receives text messages
Pretty basic API stuff
Personal tool to handle ‘burner’ phone numbers for SMS registrations, etc.
Telstra SMS Kivy – Android app, similar idea, using the Kivy framework
    - UI design and I do not mix very well
    - Kivy overhead is huge! Startup time is not great
probably some other ones I’ve forgotten