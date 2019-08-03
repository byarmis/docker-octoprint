This repository contains everything you need to run [Octoprint](https://github.com/foosel/OctoPrint) in a Docker environment along with a USB webcam streaming.

Note that I developed and used this on a desktop computer.  It should work on a Raspberry Pi, but I can't really make any guarantees.

# Getting started

```
git clone https://github.com/byarmis/docker-octoprint.git && cd docker-octoprint

docker-compose up --detach
```

You can then go to `http://localhost:5000` to view the status and the stream.

You can display the logs using `docker-compose logs -f`.

To stop the running containers, run `docker-compose down`.  This can be verified by running `docker ps`.

# Options

Depending on the webcam that you have, you can change the resolution in `streamer/Dockerfile` by changing the `-r 1280x720` bit of things.

