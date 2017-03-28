# RPI Jeedom

* Master : [![Circle CI](https://circleci.com/gh/zeiot/rpi-jeedom/tree/master.svg?style=svg)](https://circleci.com/gh/zeiot/rpi-jeedom/tree/master)
* Develop : [![Circle CI](https://circleci.com/gh/zeiot/rpi-jeedom/tree/develop.svg?style=svg)](https://circleci.com/gh/zeiot/rpi-jeedom/tree/develop)

Docker image of [Jeedom][] to use on a [Raspberry PI][].
See releases on : https://www.jeedom.com/downloads/

Exposes Port `8080` 

Configure binfmt-support on the Docker host (works locally or remotely, i.e: using boot2docker):

    $ docker run --rm --privileged multiarch/qemu-user-static:register --reset

Then you can run an armhf image from your x86_64 Docker host :

    $ make run version=2.4

Or build :

    $ make build version=2.4


# Usage

Launch: 

    $ make run version=2.4


# Supported tags

* [![](https://images.microbadger.com/badges/version/zeiot/rpi-jeedom.svg)](http://microbadger.com/images/zeiot/rpi-jeedom "Get your own version badge on microbadger.com")


## License

See [LICENSE](LICENSE) for the complete license.


## Changelog

A [ChangeLog.md](ChangeLog.md) is available.


## Contact

Nicolas Lamirault <nicolas.lamirault@gmail.com>


[Raspberry PI]: https://www.raspberrypi.org/
[Jeedom]: https://jeedom.com/
