---
title: "YouTube Video Downloader Using Python"
excerpt: "Learn how to download YouTube playlists and single videos using Python and yt-dlp with this comprehensive guide."

header:
  image: "../assets/images/posts/2023-12-30-youtube-downloader/cover.jpg"
  teaser: "../assets/images/posts/2023-12-30-youtube-downloader/cover.jpg"
  caption: "Automate YouTube Video and Playlist Downloads with Python. - Abdul Rahman"
  categories: [YouTube Downloader, Python, Automation]
  tags: [YouTube Downloader, yt-dlp, Python, Automation, Playlist Download, Video Download]
---

# Introduction

This guide introduces a simple but powerful YouTube downloader using Python and the `yt-dlp` library. You'll learn how to download entire playlists and single videos with ease using two Python scripts.

If you're tired of relying on online services or need more control over your downloads, this solution is for you. Plus, the scripts are available on my [GitHub repository](https://github.com/Abd-al-RahmanH/Youtube-downloader). 

## 🎉 Key Features
- **Download YouTube Playlists:** Easily download all videos from a YouTube playlist.
- **Download Single Videos:** Download any individual YouTube video.
- **Highly Configurable:** Customize formats, output paths, and more using `yt-dlp`.
- **Python-based Solution:** Lightweight and fully open-source.

Feel free to give a ⭐️ on GitHub!

---

## 📦 Prerequisites

Before running the scripts, make sure you have:

- Python installed on your system. You can download it [here](https://www.python.org/downloads/).
- Install the `yt-dlp` library using the following pip command:

```bash
pip install yt-dlp
```

This library handles all the downloading processes seamlessly.

---

## 📜 How to Download a YouTube Playlist

The following script downloads all videos from a specified YouTube playlist. Here’s how it works:

### Script: `download_playlist.py`

```python
import yt_dlp

def download_playlist(playlist_url, download_path):
    ydl_opts = {
        'format': 'bestvideo+bestaudio/best',
        'merge_output_format': 'mp4',  # You can change to 'mkv' if needed
        'outtmpl': f'{download_path}/%(title)s.%(ext)s',
        'noplaylist': False,  # Set to True to download only one video
    }

    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download([playlist_url])

playlist_url = 'https://youtube.com/playlist?list=PLihCJJ6_IteEo46nNNA4ksZw7ITDQ7nkS'
download_path = 'D:/Yt_videos'
download_playlist(playlist_url, download_path)
```

### How to Run:

1. Replace `playlist_url` with the playlist you want to download.
2. Update `download_path` with your preferred folder to store the videos.
3. Run the script using:

```bash
python download_playlist.py
```

This script downloads all videos from the playlist to the specified directory, saving them in `.mp4` format by default.

---

## 🎥 How to Download a Single YouTube Video

Need just one video? Here’s a script to download a single video:

### Script: `download_video.py`

```python
import yt_dlp

def download_video(video_url, download_path):
    ydl_opts = {
        'format': 'bestvideo+bestaudio/best',
        'merge_output_format': 'mp4',  # Change to 'mkv' if preferred
        'outtmpl': f'{download_path}/%(title)s.%(ext)s',
        'noplaylist': True,  # Ensures only one video is downloaded
    }

    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download([video_url])

video_url = 'https://www.youtube.com/watch?v=OoHPhLV43gg'
download_path = 'E:/Yt_single_videos'
download_video(video_url, download_path)
```

### How to Run:

1. Replace `video_url` with the YouTube video URL.
2. Set your desired `download_path`.
3. Execute the script using:

```bash
python download_video.py
```

The video will be saved in the specified folder in `.mp4` format.

---

## 🛠️ Customizing the Scripts

Both scripts are flexible. Here are some adjustments you can make:

- **Format:** Change the `'merge_output_format': 'mp4'` to `'mkv'` if you prefer a different video format.
- **Output Template:** Modify the `'outtmpl': f'{download_path}/%(title)s.%(ext)s'` to change the naming and directory structure.
- **Download Path:** Ensure your download path is properly set, especially if you’re using different drives or OS environments.

---

## 🌐 GitHub Repository

You can find both scripts, along with detailed instructions, in my GitHub repository:

[YouTube Downloader on GitHub](https://github.com/Abd-al-RahmanH/Youtube-downloader)

Feel free to contribute or raise any issues you encounter while using the tool.

---

## 🚀 Conclusion

With these simple Python scripts, downloading YouTube videos and playlists has never been easier. Whether you're saving content for offline use or creating a personal video library, this tool offers a robust solution.

Give it a try, and don’t forget to ⭐️ the GitHub repo if you find it helpful!

Happy downloading!

---
 
