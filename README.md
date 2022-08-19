# ci-config
Config for self-hosted CI, using [DroneCI](https://docs.drone.io).

## Initial setup

Set these envrionment variables:
```
$GITHUB_CLIENT_ID
$GITHUB_CLIENT_SECRET
$DRONE_RPC_SECRET
$WEB_ROOT_DOMAIN
$DOCKER_CONFIG_ROOT
```

The `$DOCKER_CONFIG_ROOT` is a path to a directory that will have a `ci/drone-config/` directory in that contains 
the config for the Drone server.

Then run:
```
docker-compose -p drone-ci pull && docker-compose -p drone-ci up -d
```

Then Drone will be running at `drone.$WEB_ROOT_DOMAIN`.

## Subsequent updates

Once Drone is up and running, this repository can be activated. Then subsequent commits will redeploy the stack, 
once all the secrets defined in `.drone.yaml` have been set in Drone.

## Runners

This `docker-compose.yaml` starts a Docker Runner, but additionally an [Exec Runner](https://docs.drone.io/runner/exec/overview/) needs to be installed.