## OpenWebRX remote setup with RTL-SDR and MSi.SDR

This is a follow-on from last week's post. I initially set up a Raspberry Pi 4 with OpenWebRX to be able to access the 2 receivers remotely. This worked well but I was concerned about the heat warping the 3D printed case and wearing out the boot SSD, so I have replaced it with a quad-core fanless mini PC with the decent J4125 CPU / 8GB RAM / 256GB SSD (which used to be my remote astrophotography PC).

Installation is mostly straightforward with a few catches.

1. Use a recent, supported distro i.e. Debian Buster or Ubuntu 21.10. See the [repo instructions][1] and check the [actual packages][2] are up-to-date. As of writing, the instructions mention Ubuntu 21.04 which is actually EOL.
2. Install the [RTL-SDR drivers][3] as usual, making sure to blacklist the default DVB-T drivers.
3. Download the SDRPlay API v3.07 from [here][4] and run with `sudo bash`. For some reason their website is so convoluted and blocks multiple downloads per session, which is weird considering [direct links][5] work. Again, make sure to blacklist the default msi drivers.
4. Install `libsoapysdr-dev` and `soapysdr-tools` from the package manager (manually compiling the latest version will not work). 
5. Build the [SoapySDRPlay3 library][6].
6. Check that both dongles show up using `SoapySDRUtil --probe="driver=sdrplay"` and `=rtlsdr`.
7. Install `openwebrx` from the repo in step 1.
8. Enjoy OpenWebRX at `http://[IP]:8073/`.

The [background decoding][8] feature is fantastic. I have the MSi.SDR monitoring FT8/FT4/WSPR on 20m during the day and 40m during the night, and the RTL-SDR listening for APRS packets on 145.175MHz. Note: this frequency needs to be changed in `/etc/openwebrx/bands.json` to match your region!

I've really enjoyed browsing various bands on OpenWebRX. It has impressive performance considering it only streams an image of the spectrum and the decoded audio, which helps a lot as my laptop is far from the access point. My only suggestion would be to allow unrestricted tuning, because manually creating and switching between different profiles is tedious, but it seems that won't be happening [anytime soon][7].

*couple hours of FT8/APRS shown in the built-in map*
![](/img/openwebrx/map.png)

[1]: https://www.openwebrx.de/download/ubuntu.php
[2]: https://repo.openwebrx.de/ubuntu/
[3]: https://www.rtl-sdr.com/tag/install-guide/
[4]: https://www.sdrplay.com/softwarehome/
[5]: https://www.sdrplay.com/software/SDRplay_RSP_API-Linux-3.07.1.run
[6]: https://github.com/pothosware/SoapySDRPlay3
[7]: https://groups.io/g/openwebrx/message/937
[8]: https://github.com/jketterl/openwebrx/wiki/Background-decoding