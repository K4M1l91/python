# fix: resolve audio dropout issues by forcing PipeWire quantum size

Fixed an issue where audio was not working correctly on Linux by defining 
a fixed quantum size in PipeWire configuration.

Solution:
Created a custom configuration file at:
~/.config/pipewire/pipewire.conf.d/custom-quantum.conf

Content added:

### context.properties = {
###     default.clock.quantum       = 256
###     default.clock.min-quantum   = 256
###     default.clock.max-quantum   = 256
###     default.clock.force-quantum = 256
### }

This change stabilizes the buffer size and prevents timing issues 
that were causing audio failures.
