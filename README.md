# Twinkly for Home-Assistant

This projects lets you control your [twinkly christmas lights](https://twinkly.com/) 
from [Home-Assistant](https://www.home-assistant.io/)

Using this component you are able to:
- Turn lights on and off 
- Configure the brigthness

![integration example](./assets/integration.png "Integration example")

## Setup
This integration is currently acheived as a _"custom component"_ which has to be installed manually:

1. From the root directory of your HA, create a directory `custom_components/twinkly`
1. Downalod all files from the [`twinkly` directory](./twinkly) of this repo and copy them in the folder you just created
1. In you `configuration.yaml`, in the `light` section add your twinkly device:

```yaml
light:
  - platform: twinkly
    host: 192.168.123.123 # cf. remaks below
```

> **Remaks**
> 
> We currently do not support floating IP address, so make sure to assign a static IP to your twkinly device.
> You can configure it in your router.

## FAQ
### Is it possible to change the effect from HA?
Unfortunately, when you change the effect from the Twinkly app, it actually re-write the full light effect to the device.
So it means that to change the effect from HA, we would have to copy those effects and push them from HA each time. 
If it's possible for the "default effects" this would however override the mapping made from the app.
And for the "custom effect" (or defaults with mapping) it would require a way to extract the effect from the twinkly app,
which does not seam to be supported.

## Road map
- [ ] Configure HACS
- [ ] Add support of online / offline (and make sure that we don't have to restart HA when we plug-in a device)
- [ ] Add discovery of devices on LAN
- [ ] Add support of floating IP adress
- [ ] Merge as a component in the HA repo

## Thanks and ref
https://labs.f-secure.com/blog/twinkly-twinkly-little-star

@joshkay https://github.com/joshkay/home-assistant-twinkly

https://xled-docs.readthedocs.io/en/latest/rest_api.html
