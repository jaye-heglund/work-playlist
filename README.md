# Downloading a Youtube playlist

youtube-dl was taken down, so I'm now using yt-dlp. This program is easier to use than youtube-dl, and automatically checks if a file has already been downloaded before downloading it.

The main reason to do this is for archival purposes. Sometimes videos get taken down from Youtube for copyright reasons, and some of my old playlists are noticeably smaller than they used to be because of this.

```

## Other download options

# Run with the -x option to download the audio with no video. My preferred option to save space. Here, -S searches for the m4a extension since m4a is a nice, high quality audio format.
yt-dlp -x PLAYLIST_URL -S res,ext:m4a

# To download videos from your work playlist, just run this
yt-dlp https://www.youtube.com/playlist?list=PLylfBmdQ1h3aIwXc3-QGiUxzQ2W14gdKS -S "res:720,ext:mp4" --recode mp4 --check-formats --rm-cache-dir -4

# Run without the -S option if you want to download the video file with the best-available quality
yt-dlp PLAYLIST_URL

# This downloads them in 720p quality. -S searches for videos that fit a few parameters
## res:720 - downloads the video with the largest resolution no better than 720p or the video with the next-smallest resolution above 720p if 720p is not available.
## I want video that looks nice enough, but not taking up a huge amount of space on my disk. This isn't a hardcore archival project :P
## ext:mp4 - prefer mp4 or m4a videos over webm since webm can have compatibility issues

# If you want a standard format for videos after downloading, you can process by copying them to mp4
# since mkv and webm are just video containers, you use -c copy to very quickly change th e format without any additional video encoding or processing (which can take around 1 minute per video)
```

## Handling common errors
```
# 403: Access Denied error
# This video suggests using these extra options (--check-formats --rm-cache-dir -4) to deal with the error.
# https://www.youtube.com/watch?v=4YPaBPs27FM
# I also downloaded + installed Deno, but idk if that did anything since I still get this warning WARNING: [youtube] No supported JavaScript runtime could be found. Only deno is enabled by default;

# "Download stopped, please log in to prove you're not a bot" error
# After downloading many videos (~40-50), you will usually get an error like this. If you log in, it may flag your YT account for piracy and delete it (!!!), but this error usually clears itself within a few days, so just wait a few days and continue your download.
# There are also options to do something with cookies from a private browser window (to prevent your personal YT from being associated with the download processes), but I don't really get how that works.
# https://www.reddit.com/r/youtubedl/comments/1rlj3xv/cookies_for_ytdlp/
```

