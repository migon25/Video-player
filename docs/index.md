## VIDEO PLAYER

## Intro

This is a research on video players and a quick explanation and implementation of them for the subject Project II. In this page you will see a brief explanation on why they use videos in video gamese, how they are made, the components of a video player, codecs and container types. For the code of this research we are going to use Video for Windows libraries and DirectShow to open, read and decompress AVI files, also we need SDL to render the graphics.

## What are the uses of videos in video games?

Video games commonly use pre-rendered videos for cutscenes, but they also use it for the intro of the animation of the studio, credits, intermissions, and more. Pre-rendered cutscenes were pretty much used for the narrative part. Nowadays they use real time cutscenes for more interaction with the gameplay story and also for the game company is much easier and faster to develop a game since they don't have to invest the production for the pre-rendered scenes.

Here are some examples of a pre-rendered cutscenes and a real time in game cut-scene:

<iframe width="640" height="334" src="https://www.youtube.com/embed/pa1fi1gxxUw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Cutscene before a level.

<iframe width="640" height="334" src="https://www.youtube.com/embed/wFbWI0pwXH0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

 Real time cutscenes. 

## Video players and Codecs

Video and music files are huge, which means they are usually difficult to transfer over the internet. To speed up downloads, algorithms encode, or shrink, a signal for transmission and then decode it for viewing or editing. Without codecs, downloads of video and audio would take three to five times longer than they do now. take for example a 10 minute HD video that is compressed is only 500MB whereas a 12 bit raw uncompressed video file with the same resolution as the 10 minute video can take up to 60GB of space. That is why we need codec for efficiency.

### How does it work?

A video player is a software that allows for the playback of video an multi media with the help of codec. A codec is a computer program that uses compression to shrink a large movie file or convert between analog and digital sound. The codec contains a digital to analog converter that allows to convert sound to a digital file and it also has an analog to digital converter to interpret digital files and turn those back into sound with the maximum fidelity as possible.

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


### Audio Codec

Like video, different audio codecs excel at different things. AAC (Advanced Audio Coding) and MP3 (MPEG-1 Audio Layer 3) are two lossy formats that are widely known among audio and video. Given that they are lossy, these formats, in essence, delete information related to the audio in order to compress the space required. The job of this compression is to strike the right balance, where a sufficient amount of space is saved without notably compromising the audio quality.

### What are the recommended codecs?

Favoring compatibility, H.264 and AAC are widely used, IBM’s video streaming and enterprise video streaming offerings support both the H.264 video codec and the AAC audio codec for streaming. While neither is cutting edge, both can produce high quality content with good compression applied. In addition, video content compressed with these codecs can reach large audiences, especially over mobile devices.

## Code of the video player

How does it work? First, we read the avi file and the stream data. Then, on each loop we will take the bitmap data of a frame. With that, we will create a surface and a texture from that surface, and we will blit it on screen. Note that this code is not the best, there are many ways to do it, but this is how I managed to solve this problem and I hope you find it useful.

### The module

FUNCTIONS

We will have four esential functions.
 
-**OpenAVI**, that opens the avi file and reads its stream data.

-**Initialize**, that calls OpenAVI with the path to the file (we will call this function whenever we want to play a video)

-**GrabAVIFrame**, that gets the frame data, makes a surface and a texture, and blit it.

-**CloseAVI**, that will free the memory we have used.


```
void Initialize(char* file_path);
void OpenAVI(LPCSTR path);
bool GrabAVIFrame();
void CloseAVI();

```

VARIABLES

**frame** is the current frame we want to display from the animation. We start off at 0 (first frame). 
The **psi** structure will hold information about our AVI file later in the code. 
**pavi** is a pointer to a buffer that receives the new stream handle once the AVI file has been opened. 
**pgf** is a pointer to our GetFrame object. 
**lastframe** will hold the number of the last frame in the AVI animation. 
**width and height** will hold the dimensions of the AVI stream.
**pdata** is a pointer to the image data returned after we get a frame of animation from the AVI.
**mpf** will be used to calculate how many milliseconds each frame is displayed for. More on this later.


To be able to declare those, we have to include the video for windows library and header files. I also included the direct show header files beacause vfw is a little bit old and outdated, and we will be able to decompress videos with diferent codecs.


```

int     frame = 0;			

AVISTREAMINFO       psi;      
PAVISTREAM	    pavi;     
PGETFRAME	    gf;      

long		    lastFrame;
int		    width;    
int		    height;   
char*		    pdata;		
int		    mpf;      

```

## 4. TODOs

### TODO 1: Call the initialize function.

- We have a function called "Initialize" in the video module. Call it in the start of the scene.
- You have to pass the path to the AVI file.

SOLUTION

```

App->video->Initialize("video/sample(good).avi");

```


### TODO 2: Open and then release the stream from the AVI file.

TODO 2.1: Open a single stream from the AVI file.
- Use AVIStreamOpenFromFile(...).
- The first parameter is a pointer to a buffer that receives the stream handle.
- The second parameter is the path to the file.
- The third parameter is the type of stream we want to open (in this case streamtypeVIDEO).
- The fourth parameter is which video stream we want (there can be more than one), in this case: 0.
- The rest (RGB masks), are 0 if you do not want to put a mask on it.
- Use LOG to write info in case it fails.

SOLUTION

```
if (AVIStreamOpenFromFile(&pavi, path, streamtypeVIDEO, 0, OF_READ, NULL) != 0)
		LOG("Failed To Open The AVI Stream");

```

TODO 2.2: Release the stream.
- Use AVIStreamRelease(...)

SOLUTION

```
AVIStreamRelease(pavi);

```


### TODO 3: Decompress video frames from the AVI file and deallocate the GetFrame resources.

TODO 3.1: Decompress video frames from the AVI file.
- Use AVIStreamFrameOpen(...).
- Hint: this function returns a PGETFRAME.
- On the second parameter you can pass AVIGETFRAMEF_BESTDISPLAYFMT to select the best display format. Cast it to LPBITMAPINFOHEADER.

SOLUTION

```
pgf = AVIStreamGetFrameOpen(pavi, (LPBITMAPINFOHEADER)AVIGETFRAMEF_BESTDISPLAYFMT);
	if (pgf == NULL)
		LOG("Failed To Open The AVI Frame");

```

TODO 3.2: Deallocate the getframe resources.
- AVIStreamGetFrameClose(...).

SOLUTION

```
AVIStreamGetFrameClose(pgf);

```

If the current solution breaks when it has to get the data from the AVI stream is because the video sample doesn't have the right codec. In this TODO you will learn how to prepare the right video for it to function well in the code.

### TODO 4: Prepare the video.
There are lots of video converters that allows you to chose an especific codec. In this case we will use Adobe Premiere. 
NOTE: You can aslo use other softwares if you feel more confortable with them.

Follow the next steps:
1. Go to File->Export->Media...
2. Go to Video Codec options and select "Códec Intel IYUV"

![ppexportbox](https://user-images.githubusercontent.com/25648776/39608158-dd1d762a-4f3f-11e8-9b08-48c021585434.PNG)

![dzfasdf](https://user-images.githubusercontent.com/25648776/39608159-df167738-4f3f-11e8-93ee-30a9618f5fa3.PNG)


SOLUTION
If you have done that steps right, the program should not break now.

### TODO 5: Create the surface and the texture, and then free them.

TODO 5.1: Create a surface using the bitmap data we have above this TODO, and create the texture of the frame with that surface (use LoadSurface from textures module)
- pdata holds the texture data (pixels)
- biBitCount holds the depht in bits and is contained in the LPBITMAPINFOHEADER structure
- pitch is the length of a row of pixels in bytes (widht x 3)

SOLUTION

```

SDL_Surface* surface = SDL_CreateRGBSurfaceFrom(pdata, width, height, lpbi->biBitCount, width * 3, 0, 0, 0, 0);
	SDL_Texture* texture = App->tex->LoadSurface(surface);

```

TODO 5.2: Unload the texture and free the surface after the blit.
- Use UnLoad(...) from the textures module and SDL_FreeSurface(...).

SOLUTION

```

App->tex->UnLoad(texture);
	SDL_FreeSurface(surface);

```

### TODO 6: Blit the texture of the frame.

TODO 6.1: Do the blit with the texture we have created in the last TODO.

SOLUTION

```

App->render->Blit(texture, 0, 0);

```


Now you should see the video playing, but fliped in vertical and way too fast. Let's flip it! We will deal with the speed in the next TODO.

TODO 6.2: Prepare the blit function to recieve a SDL_RenderFlip flag.
- Remember to put a default value (SDL_FLIP_NONE).

SOLUTION

```

bool Blit(SDL_Texture* texture, int x, int y, const SDL_Rect* section = nullptr, SDL_RendererFlip rendererFlip = SDL_FLIP_NONE, float speed = 1.0f, double angle = 0, int pivot_x = 0, int pivot_y = 0) const;

```

```

bool j1Render::Blit(SDL_Texture* texture, int x, int y, const SDL_Rect* section, SDL_RendererFlip rendererFlip, float speed, double angle, int pivot_x, int pivot_y) const
{

...

```

TODO 6.3: Use the flag on SDL_RenderCopyEx(...).

SOLUTION

```

if(SDL_RenderCopyEx(renderer, texture, section, &rect, angle, p, rendererFlip) != 0)
	{
		LOG("Cannot blit to screen. SDL_RenderCopy error: %s", SDL_GetError());
		ret = false;
	}


```

### TODO 7: Limit the change of the frame to one out of two times.

-  Hint: We want to blit a diferent frame only when our counter, i, is an even number.

SOLUTION

```

if (i % 2 == 0) 
	{
		frame++;
	}
	i++;

```

### TODO 8: Play the music of the video.

-  Use the audio module.

SOLUTION

```

App->audio->PlayMusic("video/sample.ogg", 0.0f);

```


## Documentation and References

- [www.gamedeveloper.com/audio/in-depth-playing-with-video](https://www.gamedeveloper.com/audio/in-depth-playing-with-video)
- [www.lifewire.com/what-exactly-is-odec-2483426](https://www.lifewire.com/what-exactly-is-odec-2483426)
- [www.wowza.com/blog/video-codecs-encoding](https://www.wowza.com/blog/video-codecs-encoding)
- [blog.video.ibm.com/streaming-video-tips/what-is-video-encoding-codecs-compression-techniques/](https://blog.video.ibm.com/streaming-video-tips/what-is-video-encoding-codecs-compression-techniques/)
- [www.techsmith.com/blog/understanding-video-file-types-codecs-containers-and-outputs/](https://www.techsmith.com/blog/understanding-video-file-types-codecs-containers-and-outputs/)
- [www.techtarget.com/searchunifiedcommunications/definition/codec](https://www.techtarget.com/searchunifiedcommunications/definition/codec)
- [https://stackoverflow.com/questions/39059959/vfw-avistreamgetframeopen-returns-null](https://stackoverflow.com/questions/39059959/vfw-avistreamgetframeopen-returns-null)
- [http://nehe.gamedev.net/tutorial/playing_avi_files_in_opengl/23001/](http://nehe.gamedev.net/tutorial/playing_avi_files_in_opengl/23001/)
- - [http://www.any-video-converter.com/mac-tutorial/video-codec.php](http://www.any-video-converter.com/mac-tutorial/video-codec.php)
- [www.youtube.com/watch?v=sisvOeZItb0](https://www.youtube.com/watch?v=sisvOeZItb0)
- [www.youtube.com/watch?v=7YQ1mikDhIo](https://www.youtube.com/watch?v=7YQ1mikDhIo)
- [www.youtube.com/watch?v=GhWki9a7s18](https://www.youtube.com/watch?v=GhWki9a7s18)
