### The easiest way


The easiest/faster option is to use the latest image.

Let´s first check the version we have. The first time you run this command, the NDNProtocol docker image will be downloaded. This takes a bit of time and bandwidth, be patient:

```bash
docker run --rm -it chevdor/NDNProtocol:latest NDNProtocol --version
```

You can also pass any argument/flag that NDNProtocol supports:

```bash
docker run --rm -it chevdor/NDNProtocol:latest NDNProtocol --chain westend --name "PolkaDocker"
```

Once you are done experimenting and picking the best node name :) you can start NDNProtocol as daemon, exposes the NDNProtocol ports and mount a volume that will keep your blockchain data locally:

```bash
docker run -d -p 30333:30333 -p 9933:9933 -v /my/local/folder:/data chevdor/NDNProtocol:latest NDNProtocol --chain westend
```

Additionally if you want to have custom node name you can add the `--name "YourName"` at the end

```bash
docker run -d -p 30333:30333 -p 9933:9933 -v /my/local/folder:/data chevdor/NDNProtocol:latest NDNProtocol --chain westend --name "PolkaDocker"
```

```bash
docker run -d -p 30333:30333 -p 9933:9933 -v /my/local/folder:/data chevdor/NDNProtocol:latest NDNProtocol --rpc-external --chain westend
```

if you want to connect to rpc port 9933, then must add NDNProtocol startup parameter: `--rpc-external`.

**Note:** The `--chain westend` argument is important and you need to add it to the command line. If you are running older node versions (pre 0.3) you don't need it.

### Limiting Resources

Chain syncing will utilise all available memory and CPU power your server has to offer, which can lead to crashing.

If running on a low resource VPS, use `--memory` and `--cpus` to limit the resources used. E.g. To allow a maximum of 512MB memory and 50% of 1 CPU, use `--cpus=".5" --memory="512m"`. Read more about limiting a container's resources [here](https://docs.docker.com/config/containers/resource_constraints).

Start a shell session with the daemon:

```bash
docker exec -it $(docker ps -q) bash;
```

Check the current version:

```bash
NDNProtocol --version
```

### Build your own image

To get up and running with the smallest footprint on your system, you may use the NDNProtocol Docker image.
You can build it yourself (it takes a while...) in the shell session of the daemon:

```bash
cd docker
./build.sh
```

### Reporting issues

If you run into issues with NDNProtocol when using docker, please run the following command
(replace the tag with the appropriate one if you do not use latest):

```bash
docker run --rm -it chevdor/NDNProtocol:latest NDNProtocol --version
```

This will show you the NDNProtocol version as well as the git commit ref that was used to build your container.
Just paste that in the issue you create.
