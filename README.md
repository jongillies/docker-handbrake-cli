#docker handbrake-cli

This is a Dockerfile to set up HandBrakeCLI

Build from docker file:

```
git clone https://github.com/jongillies/docker-handbrake-cli.git
cd handbrake-cli
docker build -t handbrake-cli .
```

Run from hub.docker.com:

```
docker run -d  \
    -v <your input folder>:/input
    -v <your output folder>:/output
    --name handbrake-cli supercoder/handbrake-cli
```

Running HandBrakeCLI:

```bash
export HANDBRAKE_OPTIONS="-e x264  -q 20.0 -a 1,1 -E ffaac,copy:ac3 -B 160,160 -6 dpl2,auto -R Auto,Auto -D 0.0,0.0 --audio-copy-mask aac,ac3,dtshd,dts,mp3 --audio-fallback ffac3 -f mp4 --decomb --loose-anamorphic --modulus 2 -m --x264-preset medium --h264-profile high --h264-level 4.1"
run -v /media/Pre-Release:/input \
    -v /media/converting:/output \
    handbrake-cli \
    -i /input/movie.mkv
    -o /output/movie.mkv \
    $HANDBRAKE_OPTIONS
```