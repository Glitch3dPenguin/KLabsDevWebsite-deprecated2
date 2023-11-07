---
title: Caffeine.tv VOD Downloader
date: 2022-06-04
categories: [Caffeine.tv, Streaming]
tags: [caffeine.tv,script,streaming,bash,]
---
## Introduction
I am a full-time streamer and partner with Caffeine TV. I spend a lot of time live and recording every broadcast to make clips or YouTube videos would consume loads of space on my NAS. Since Caffeine.tv records all broadcasts and saves them for viewing later, why not just download and save the VODs when needed. For the time being Caffeine does not have any features allowing any easy VOD downloading for their broadcasters. 

So I set out to build an easy, small script that will do this for me. 

## How it Works
- A very short script directly in batch that allows Caffeine.TV streamers to download their VODs to save and edit.
- Uses ffmpeg to read HLS stream data from Caffeine.TV.
- Coverts stream data and saves VOD file as .mp4 for easy editing and compatibility with most editors/devices.

## Where to Download
The latest version can be downloaded from my GitHub page [**here**](https://github.com/Glitch3dPenguin/CaffVodDownloader). 

## How to Use

- **Step 1)** On desktop, open your Caffeine profile. You want to be able to see all your VODs. The page should look like this:

![Screen shot of a list of Caffeine VODS](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader01.png)


- **Step 2)** Press F12 to open the browser console.

![Screen recording opening the console](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader02.gif)


- **Step 3)** Open the network tab

![Open the network tab](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader03.gif)


- **Step 4)** Now it's time to pick the VOD that you want to download. With the Network tab still open, scroll through your VODs and click on the video you want to download. Then look on the network tab and find the new row that appeared called main.m3u8.

![Ntworks tab](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader04.gif)


- **Step 5)** Right-click on main.m3u8. Then hover over Copy. You will want to choose Copy link address.

![Right-clicking on the correct vod link](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader05.gif)


- **Step 6)** Paste the URL into the script once you run it and press ENTER.

![Adding the VOD link to the program](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader06.png)


- **Step 7)** Now choose a name for your VOD to be saved and press ENTER.

![Naming the vod in the program](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader07.png)


- **Step 8)** Now choose what format to save the VOD as and press ENTER.

![Choose file type in program](https://cdn.klabsdev.com/klabsdev/images/CaffeineVodDownloader08.png)



DONE! Your VOD will now be downloaded and saved in the new "CaffeineVODs" folder located in Downloads.
## Conclusion
This was a fun utility project that I worked on to help me save some space. The code for this project is posted on Github and free for anyone to use or make changes to. If this program helped you download any of your VODs please leave a star on my GitHub page! 

Thanks for reading!

Written By: Max Kulik