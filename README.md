# pat-test-rig

The purpose of this repository is to facilitate development and debugging of
transport packages for Pat, by providing a containerized setup simulating a
pair of software modems talking to each other "over the air". 

By using the alsa loopback module (snd-aloop) we're able to couple the modems
"acoustically". It's far from a perfect simulation, but good enough to test the
basics of interfacing with the modem from an app's perspective.

## Prerequisites 

You'll probably need a Linux box to run this, as I don't think your vanilla
Docker Desktop provides the alsa subsystem with the snd-aloop module loaded.

## Getting started

On a Linux system, load the module with `sudo modprobe snd-aloop` before
starting any **one of** the modem pairs using `docker-compose up`.

Refer to the docker-compose.yml file for port definitions.
