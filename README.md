# bandcamp-downloader
Download your Bandcamp collection using this python script.

It requires you to have a browser with a logged in session of bandcamp open. Cookies from the browser will be used to authenticate with Bandcamp.

Supported browsers are the same as in browser_cookie3: Chrome, Chromium, Firefox, Brave, Opera, and Edge

Albums will be downloaded into their zip files and singles will just be mp3 files. Downloads are organized by Artist name. Downloads will happen in parallel, by default using a pool of 5 threads. Already existing files of the same name will have their file sizes checked against what it should be, and if they are the same, the download will be skipped, otherwise it will be over-written.

## Requirements
- Python3
- [BeautifulSoup 4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) `pip install bs4`
- [requests](https://github.com/psf/requests) `pip install requests`
- [browser_cookie3](https://github.com/borisbabic/browser_cookie3) `pip install browser-cookie3`
- [TQDM](https://tqdm.github.io/) `pip install tqdm`

## Usage
```
usage: bandcamp-downloader.py [-h] [--browser {firefox,chrome,chromium,brave,opera,edge}] [--directory DIRECTORY]
                              [--parallel-downloads PARALLEL_DOWNLOADS] [--verbose]
                              username

Download your collection from bandcamp. Requires a logged in session in a supported browser so that the browser
cookies can be used to authenticate with bandcamp. Albums are saved into directories named after their artist.
Already existing albums will have their file size compared to what is expected and re-downloaded if the sizes
differ. Otherwise already existing albums will not be re-downloaded.

positional arguments:
  username              Your bandcamp username

options:
  -h, --help            show this help message and exit
  --browser {firefox,chrome,chromium,brave,opera,edge}, -b {firefox,chrome,chromium,brave,opera,edge}
                        The browser whose cookies to use for accessing bandcamp. Defaults to "firefox"
  --directory DIRECTORY, -d DIRECTORY
                        The directory to download albums to. Defaults to the current directory.
  --parallel-downloads PARALLEL_DOWNLOADS, -p PARALLEL_DOWNLOADS
                        How many threads to use for parallel downloads. Set to '1' to disable parallelism. Default
                        is 5. Must be between 1 and 32
  --verbose, -v
```

## TODO
- Support filetypes other than mp3-320
- Allow filtering by artist?
