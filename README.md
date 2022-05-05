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

There are two parts of a codec, the encoder and the decoder. the encoder compresses the video stream into a binary encoded bitstream. The decoder restores the encoded bitstream back into sequential pictures, or frames, for playback. This process results some losses of the original video quality. There are lossless codecs that  make the decompression high quality but their file size compared to lossy codecs are still very large and they can be very processor intensive to encode and decode, so the most common solution is to use a lossy codec at high bitrate that is more data per second in the stream if you want high quality playback without files that are so large you can't store them or easily send them anywhere.

![encoder](https://github.com/migon25/Video-player/blob/main/docs/video%20player/encoder.png?raw=true)![decoder](https://github.com/migon25/Video-player/blob/main/docs/video%20player/decoder.png?raw=true)

![code](https://github.com/migon25/Video-player/blob/main/docs/video%20player/code.png?raw=true)![quality](https://github.com/migon25/Video-player/blob/main/docs/video%20player/quality.png?raw=true)

There are lots of codecs, specialize for audio and video compression, for streaming media over the internet, speech, video conferencing, playing MP3s, and screen capture. Some create efficient files that are higher quality, but take up more space. Other codecs create small and efficient files but lack overall quality. Some common codecs are MP3, WMA, RealVideo, RealAudio, DivX, and XviD, but there are many others. AVI is a common file extension you see attached to lots of video files, but it is not in itself a codec. Instead, it is a container format that many different codecs can use. Hundreds of codecs are compatible with AVI content.

### What codecs are better?

There is no right answer for that question. Some codecs are best for high quality, while others maintain better playback on unreliable connections, while others still are designed to keep latency or delay very very low. That is why we need a wide variety of audio and video codecs that are optimized for  different uses.


### Container Formats

To make it simpler, we all know about the formats .mkv .mov .avi .mp4 .flv and more.. These are all container, which it's name itself sais it contains data.
It’s important to distinguish codecs from container formats, though sometimes they share the same name.
So what are they? As we said they are file formats that can contain specific types of data, including audio, video, closed captioning text, and associated metadata. Most container formats target one aspect of the production and distribution pipeline, like MXF for file-based capture on a camcorder, and FLV and WebM for streaming Flash and WebM content.


## Audio Codec

Like video, different audio codecs excel at different things. AAC (Advanced Audio Coding) and MP3 (MPEG-1 Audio Layer 3) are two lossy formats that are widely known among audio and video. Given that they are lossy, these formats, in essence, delete information related to the audio in order to compress the space required. The job of this compression is to strike the right balance, where a sufficient amount of space is saved without notably compromising the audio quality.

## What are the recommended codecs?

Favoring compatibility, H.264 and AAC are widely used, IBM’s video streaming and enterprise video streaming offerings support both the H.264 video codec and the AAC audio codec for streaming. While neither is cutting edge, both can produce high quality content with good compression applied. In addition, video content compressed with these codecs can reach large audiences, especially over mobile devices.


## Documentation and References

- https://www.gamedeveloper.com/audio/in-depth-playing-with-video
- https://www.lifewire.com/what-exactly-is-odec-2483426
- https://www.wowza.com/blog/video-codecs-encoding
- https://blog.video.ibm.com/streaming-video-tips/what-is-video-encoding-codecs-compression-techniques/
- https://www.techtarget.com/searchunifiedcommunications/definition/codec
- https://www.youtube.com/watch?v=sisvOeZItb0
- https://www.youtube.com/watch?v=7YQ1mikDhIo
- https://www.youtube.com/watch?v=GhWki9a7s18
