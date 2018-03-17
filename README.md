[hub]: https://hub.docker.com/r/spritsail/fivem
[git]: https://github.com/spritsail/fivem
[drone]: https://drone.spritsail.io/spritsail/fivem

# [spritsail/fivem][hub]

[![](https://images.microbadger.com/badges/image/spritsail/fivem.svg)](https://microbadger.com/images/spritsail/fivem)
[![Latest Version](https://images.microbadger.com/badges/version/spritsail/fivem.svg)][hub]
[![Git Commit](https://images.microbadger.com/badges/commit/spritsail/fivem.svg)][git]
[![Docker Pulls](https://img.shields.io/docker/pulls/spritsail/fivem.svg)][hub]
[![Docker Stars](https://img.shields.io/docker/stars/spritsail/fivem.svg)][hub]
[![Build Status](https://drone.spritsail.io/api/badges/spritsail/fivem/status.svg)][drone]

This docker image allows you to run a server for FiveM, a modded GTA multiplayer program.
Upon first run, the configuration is generated in the host mount for the `/config` directory.
The container should be stopped so fivem can be configured to the user requirements in the `server.cfg`.

## Licence Key

A freely obtained licence key is required to use this server, which should be entered in `server.cfg`. A tutorial on how to obtain a licence key can be found [here](https://forum.fivem.net/t/explained-how-to-make-add-a-server-key/56120)

## Usage

Use the docker-compose script provided if you wish to run a couchdb server with FiveM, else use the line below:

```sh
docker run -d \
  --name FiveM \
  --restart=on-failure \
  -e LICENCE_KEY=<your-license-here>
  -p 30120:30120 \
  -v /volumes/fivem:/config \
  spritsail/fivem
```

### Environment Varibles

- `LICENSE_KEY` - This can be optionally specified to be entered into the configuration file. Is only effective on container first-run, or when the configuration is absent.
- `RCON_PASSWORD` - A password to use for the RCON functionality of the fxserver. If not specified, a random 16 character password is assigned.
