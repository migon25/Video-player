## VIDEO PLAYER

### Intro

A video player is a software that allows for the playback of video an multi media with the help of codec. A codec is a computer program that uses compression to shrink a large movie file or convert between analog and digital sound. The codec contains a digital to analog converter that allows to convert sound to a digital file and it also has an analog to digital converter to interpret digital files and turn those back into sound with the maximum fidelity as possible.

### Why do we need codecs?

Video and music files are huge, which means they are usually difficult to transfer over the internet. To speed up downloads, algorithms encode, or shrink, a signal for transmission and then decode it for viewing or editing. Without codecs, downloads of video and audio would take three to five times longer than they do now. take for example a 10 minute HD video that is compressed is only 500MB whereas a 12 bit raw uncompressed video file with the same resolution as the 10 minute video can take up to 60GB of space. That is why we need codec for efficiency.

### How does it work?

The codec computer programs take the original source video or audio data and compresses it in a specific format that adheres to a documented standard that allows to be interpreted easily by other devices that are capable of utilizing the same codec. They are necessary for two main rasons, first is so we can save device space and secondly to efficiently send those files over network. It uses an algorithm to convert data into a byte sequence for easy transmission, then convert the byte sequence back into audio or video again. How does it compress? Well, we know that a video is a sequence of images called frames, and if we take for example a 60 frame per second video we say that it has 60 images every second that passes, and since there are lots of images in a second, those images in each frame varies only slightly from the frames before it and those after it.

![video](https://github.com/migon25/Video-player/blob/main/docs/video%20player/personal%20research.png?raw=true)![frames](https://github.com/migon25/Video-player/blob/main/docs/video%20player/frames.png?raw=true)

Codecs work by removing similarities in the uncompressed frames, keeping only the differences, and coding the differences
as symbols. After all the redundacnies are removed, the resulting data, called the encoded bitstream, uses far less data than the uncompressed source.

![similarities](https://github.com/migon25/Video-player/blob/main/docs/video%20player/similar.png?raw=true)![symbols](https://github.com/migon25/Video-player/blob/main/docs/video%20player/differences.png?raw=true)

There are two parts of a codec, the encoder and the decoder. the encoder compresses the video stream into a binary encoded bitstream. The decoder restores the encoded bitstream back into sequential pictures, or frames, for playback. This process results some losses of the original video quality.

![encoder](https://github.com/migon25/Video-player/blob/main/docs/video%20player/encoder.png?raw=true)![decoder](https://github.com/migon25/Video-player/blob/main/docs/video%20player/decoder.png?raw=true)

![code](https://github.com/migon25/Video-player/blob/main/docs/video%20player/code.png?raw=true)![quality](https://github.com/migon25/Video-player/blob/main/docs/video%20player/quality.png?raw=true)

There are lots of codecs, to play video, audio and image files. Some codec create effixient files that are higher quality, but take up more space. Other codecs create small and efficient files but lack overall quality.
