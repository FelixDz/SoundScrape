![SoundScrape!](http://i.imgur.com/nHAt2ow.png)

SoundScrape [![Build Status](https://travis-ci.org/Miserlou/SoundScrape.svg)](https://travis-ci.org/Miserlou/SoundScrape) [![Python 2](https://img.shields.io/badge/Python-2-brightgreen.svg)](https://pypi.python.org/pypi/soundscrape/) [![Python 3](https://img.shields.io/badge/Python-3-brightgreen.svg)](https://pypi.python.org/pypi/soundscrape/) [![PyPI](https://img.shields.io/pypi/v/soundscrape.svg)](https://pypi.python.org/pypi/SoundScrape)
==============

**SoundScrape** makes it super easy to download artists from SoundCloud (and Bandcamp and MixCloud) - even those which don't have download links! It automatically creates ID3 tags as well (including album art), which is handy.

Usage
---------

###Installation

#####Manually (after fork)

```bash
setup.py install
```

#####Via pip

```bash
pip install soundscrape
```

Note that if you are having problems, please first try updating to the latest version:

```bash
pip install soundscrape --upgrade
```

Then, just call soundscrape and the name of the artist you want to scrape:

```bash
soundscrape rabbit-i-am
```

And you're done! Hooray! Files are stored as mp3s in the format **Artist name - Track title.mp3**.

You can also use the *-n* argument to only download a certain number of songs.

```bash
soundscrape rabbit-i-am -n 3
```

###Sets / playlists

Soundscrape can also download sets / playlists, but you have to include the full URL of the set you want to download:

```bash
soundscrape https://soundcloud.com/vsauce-awesome/sets/awesome
```

###Tracks

Soundscrape can also download specific tracks, just with the straight URL:

```bash
soundscrape https://soundcloud.com/foolsgoldrecs/danny-brown-dip
```

###Folder structure

By default, SoundScrape acts like a download manager and sorts songs into the following format:

```
Artist/Year - Album/Tracknumber - Title.mp3
```

With the *-nf* (no folders) argument, Soundscrape acts more like _wget_, downloading all songs in the same directory.

It will also skip previously downloaded tracks.

```bash
soundscrape murdercitydevils -nf
```

###Save location

By default, Soundscrape saves the downloaded songs (with eventual subfolder structure for artist / album) in your Downloads directory on Windows and in `/home/Downloads` on other OS. You can specify another download folder with the *-sd* (save directory) argument:

```bash
soundscrape https://soundcloud.com/alizarinamusic -sd "D:\Music\New"
```

###Likes

Soundscrape can also download all of an Artist's Liked items with *-l*:

```bash
soundscrape troyboi -l
```

or with just the straight URL:

```bash
soundscrape https://soundcloud.com/troyboi/likes
```

###High-Quality Downloads Only

By default, SoundScrape will try to rip everything it can. However, if you only want to download tracks that have an official download available (which are typically at a higher-quality 320kbps bitrate), you can use the *-d* argument.

```bash
soundscrape sly-dogg -d
```

###Keep Preview Tracks

By default, SoundScrape will skip the 30-second preview tracks that SoundCloud now provides. You can choose to keep these preview snippets with the *-k* argument.

```bash
soundscrape chromeo -k
```

***

Bandcamp
--------

SoundScrape can also pull down albums from Bandcamp. For Bandcamp pages, use the *-b* argument along with an artist's username or a specific URL. It only downloads one album at a time. This works with all of the other arguments, except *-d* as Bandcamp streams only come at one bitrate, as far as I can tell.

Note: Currently, when using the *-n* argument, the limit is evaluated for each album separately.

```bash
soundscrape warsaw -b -nf
```

This also works for non-Bandcamp URLs that are hosted on Bandcamp:

```bash
soundscrape -b http://music.monstercat.com/
```

Note that the full URL must be included.

Mixcloud
--------

SoundScrape can also grab mixes from Mixcloud. This feature is extremely expermental and is in no way guaranteed to work!

Finds the original mp3 of a mix and grabs that (with tags and album art) if it can, or else just gets the raw m4a stream.

Mixcloud currently only takes an invidiual mix. Capacity for a whole artist's profile due shortly.

```bash
soundscrape https://www.mixcloud.com/corenewsuploads/flume-essential-mix-2015-10-03/ -of
```

Audiomack
--------

Just for fun, SoundScrape can also download individual songs from Audiomack. Not that you'd ever want to.

```bash
soundscrape -a http://www.audiomack.com/song/bottomfeedermusic/top-shottas
```

MusicBed
--------

For some strange reason, it also works for MusicBed.com. Thanks @brachna for this feature.

```bash
soundscrape https://www.musicbed.com/albums/be-still/2828
```

Opening Files
--------

As a convenience method, SoundScrape can automatically _'open'_ files that it downloads. This uses your system's 'open' command for file associations.

```bash
soundscrape lorn -of
```

Issues
-------

There's probably a lot more that can be done to improve this. Please file issues if you find them!
