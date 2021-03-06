
## Name
ts-flv - FLV streaming media, implement as plugin of Apache TrafficServer.

## Status
This module is under active development.

## Description
This module provides streaming media server support for FLV files. User can send a HTTP request to the server with `start` argument which is measured in seconds, and the server will respond with the stream such that its start position corresponds to the requested time, for example:

```c
http://v.foo.com/kenshin.flv?start=187.63
```

This allows performing a random seeking at any time. We can use flash player, vlc, mplayer to play the streaming media. 

We can write this in remap.config:

```c
map http://v.foo.com/ http://i.foo.com/ @plugin=/xx/libtsflv.so
```

## System Requirements
* linux/freebsd 64bits
* trafficserver

## Build
**step1**: get ts-flv

    git clone https://github.com/portl4t/ts-flv.git
    cd ts-flv/src

**step2**: build, requires linux/freebsd (64bits is recommended)

    make

**step3**: modify remap.config and restart the trafficserver

## Note
Large flv file is not recommended. As far as I know, many video sites will cut the large video file into many pieces, and each piece will be less than 70M(bytes), it will be a reasonable choice.

## History
* 2014-12-31, output from the last key frame if start time can not be reached.
* 2014-12-30, first commit.

## See Also
* [ts-mp4](https://github.com/portl4t/ts-mp4) MP4 streaming media, implement as plugin of Apache TrafficServer.

