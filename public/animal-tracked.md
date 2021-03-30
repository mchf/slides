several notes regarding my this year hackweek project.

Target: Low power GPS tracker for animals, mostly horses
Motivation: there exist a few of such devices, but most of them
1) are expensive,
2) requires regular monthly payments
3) have (unknown) quality of their cell phone apps
4) are not able to communicate with anything else than cell phone
5) uses SMS for communication
6) powe efficiency is ... not that good

So, my main part of the hackweek projet was research if any of the above
(or all) can be improved.

Initially I was playing with an idea to use RFID based solution, but it
1) wouldn't be tracker ... it could easily measure whether it can detect
the RFID beacon but not its possition (at least not "easily")
2) would be expensive. As it would require active RFID transponders.
There exist quite some, which works in distances up to 400m, but they
were developed for industry. So neither transponders nor readers are
cheap.

Positives of RFID would be:
1) "stupid" and "small" stations on animals
2) smart central "server" (but this is also a negative - central point
is usable only if you monitor an animal in a restricted area such as
pasture)
3) low power and small tokens for animals

So, as an alternative I switched to idea of "a little bit smarter animal
tokens" and used Arduino together with GPS / GPRS chip. It

1) has low power consumption (when talking about Arduino Nano or Mini
pro). Moreover there are some more arduino like boards which might be
even more effective. Power consumption in depends on exact configuration
and usage, but in teoretical layer I was able to get up to one month of
uptime when running on with two 18650 accumulators and reporting the
position once per hour (power effective scenario for horses on pasture)
2) I was also thinking of RPI Pico as an alternative to Arduino. It is
more powerful piece of hw. In size comparable to Arduino Nano, but a
little bit more hungry. As computing power is currently not that much
needed I've decided to use Arduino, but keeps RPi Pico in mind
3) Position will be reported via GPRS (not SMS as most of comercial
trackers do). It allows to e.g. store and process data on a desktop.
However, SMS is still useful alternative which can be easily supported
4) Android app is most probably something for next week.
5) I have several alternatives how to "mount" the tracker to an animal.
Time shows which is safer (e.g. horse can easily hook himself to a
branch when having a kind of loop on his head) and easily usable.

As this short summary is getting quire long, it is better to end now ;-)
