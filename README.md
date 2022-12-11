# remote_receiver
Temporary remote_receiver component for Esphome

When using a remote_receiver in an ESP32-C3 project the receiver must be on channel 3 or 4. @RENOxDECEPTION reported that for a ESP32-S3 the receiver must be on channel 5, 6, 7 or 8. The current Esphome code has no option for that. Adding two dummy transmitters to push the receiver on channel 3 or beond will work, but that solution breaks the Neopixel bus.

This is a quick hack to go around this issue. Until Esphome includes an option to configure the channel, include this external component in your Esphome config.

The rmt_channel is 0 based. So to use the third channel, specify "rmt_channel: 2"

<pre>
external_components:
  - source: github://Jorre05/remote_receiver
    components: [ remote_receiver ]
</pre>

<pre>
remote_receiver:
  pin:
    number: GPIO18
    inverted: true
  rmt_channel: 2
  dump: all
</pre>

Ref: https://github.com/esphome/issues/issues/2934
