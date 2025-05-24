#  &nbsp; 📝 Hashtag-Wordlist

<div align="center">

### Download Collection of useful and categorize wordlist 

&nbsp;&nbsp;[![Python](https://img.shields.io/static/v1?label=&labelColor=lightblue&message=Python&color=blue&style=flat&logo=python&logoColor=black)](Python)&nbsp;&nbsp;[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

<img src="./static/hashtag-wordlist-logo.png" style="width:600px; height:400px">

##### This tool able to automate download selective type of wordlsit in popular providers

[Installation](https://github.com/Hashtag-AMIN/hashtag-wordlist#Installation) &nbsp;[Usage](https://github.com/Hashtag-AMIN/hashtag-wordlist#Usage) &nbsp; [Documentation](https://github.com/Hashtag-AMIN/hashtag-wordlist#Documentation)

</div>

**Hashtag-Wordlist** is a flexible command-line tool designed to help you **download and manage curated wordlists** from multiple popular wordlist providers. Whether you want to use pre-built wordlists or provide your own list of wordlist URLs, this tool enables selective downloading with ease and efficiency.

It is perfect for security researchers, bug bounty hunters, and penetration testers who rely on high-quality, updated wordlists for scanning, fuzzing, or enumeration tasks.

## Features

- 🎯 Supports multiple wordlist providers such as Assetnote, SecList, fuzzdb and ...
- 📥 Download selective wordlists type by specifying either a built-in list or an external input file with wordlist URLs.
- 🔄 Automatically updates URLs based on the latest available wordlists from Assetnote.
- ⚡ Reliable downloads handle with request parameters for download.
- 📂 categorize downloaded wordlists in directories for easy integration into your pentesting process.
- 🛠️ Multithreading and make faster downloading.

## Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/Hashtag-AMIN/hashtag-wordlist.git
cd hashtag-wordlist
./hashtag-wordlist
```

All library used is built-in python library, No need pip ;)

## Usage:

```bash
└─# ./hashtag-wordlist -h

        _     _            _                                                 _ _  _
        (_)   (_)          | |     _                                         | | |(_)       _
        _______ _____  ___| |__ _| |_ _____  ____ _____ _ _ _  ___   ____ __| | | _  ___ _| |_
        |  ___  (____ |/___)  _ (_   _|____ |/ _  (_____) | | |/ _ \ / ___) _  | || |/___|_   _)
        | |   | / ___ |___ | | | || |_/ ___ ( (_| |     | | | | |_| | |  ( (_| | || |___ | | |_
        |_|   |_\_____(___/|_| |_| \__)_____|\___ |      \___/ \___/|_|   \____|\_)_(___/   \__)
                                            (_____|
                                                                    Hashtag-Wordlist
                                                            https://github.com/Hashtag-AMIN

    usage: hashtag-wordlist [-h] [-S] [-D] [-A] [-F] [-W] [-P] [-H] [-N] [-U] [-Ps] [-T] [-Py] [-Ws] [-Dy] [-a] 
                            [-i INPUT] [-o OUTPUT] [-t THREAD] [-s] [-v] [-r RETRY] [-to TIMEOUT] [-rd RETRY_DELAY]

    options:
    -h --help          show this help message and exit
    -S --subdomain     Download subdomin wordlists
    -D --directory     Download directory wordlists
    -A --api           Download api wordlists
    -F --file          Download file wordlists
    -W --word          Download word wordlists
    -P --parameter     Download parameter wordlists
    -H --header        Download header wordlists
    -N --number        Download number wordlists
    -U --username      Download username wordlists
    -Ps --password     Download number wordlists
    -T --technology    Download technology wordlists
    -Py --payload      Download payload wordlists
    -Ws --webshell     Download webshell files
    -Dy --dynamic      Download/Update wordlists with dynamic tag
    -a --all           Download all wordlists
    -i --input         Input Json file contains objects of wordlist for download
    -o --output        Output directory name for download wordlists [default = "./"]
    -t --thread        Thread for download files [default = 4]
    -s --silent        Silent mode
    -v --verbose       Verbose mode
    -r --retry         Retry to download wordlist [default = 3]
    -to --timeout      Http Requet timeout [default = 5s]
    -rd --retry-delay  Delay after each retry to downlaod [default = 2s]

```

#### usage for download some type of wordlist:

```bash
./hashtag-wordlist -S -D -F
```
```bash
./hashtag-wordlist --webshell --payload --technology
```

In help meno can see all type of wordlist for download, aslo can customize type, folder and name


#### Also able download all wordlist together:
```bash
./hashtag-wordlist --all
```

#### able to use input file that contain object of wordlist:
```bash
./hashtag-wordlist -i ./static/wordlist-objects.json
```

#### if use dynamic flag, update links from [Assetnote](https://wordlists-cdn.assetnote.io/data/automated.json) for dynamic file (28th every month)

```bash
./hashtag-wordlist -S --file -Ws -Dy
```
```bash
./hashtag-wordlist -a -Dy
```
```bash
./hashtag-wordlist -i ./static/wordlist-objects.json --dynamic
```

#### You can control the thread and request parameters according to your speed and bandwidth:

```bash
./hashtag-wordlist -a --thread 1 --retry 5 -to 10 -rd 5
```

```bash
./hashtag-wordlist -i ./static/wordlist-objects.json --timeout 3 --retry-delay 1 -t 15 -r 2
```
default value of parameter:
- Thread:      4
- Retry:       3
- Timeout:     5
- Retry-delay: 2


#### Best-Usage:
```bash
./hashtag-wordlist -a -Dy
```
I try collect useful wordlist, make more efficient parameter by default for downlaod, but all can changeable


# Documentation

If you create your custom wordlist, you can make a file following this object pattern

Simple object:

```json
{
    "url": "WORDLIST_URL", 
    "fileName": "WORDLIST_FILENAME",
    "folder": "WORDLIST/FOLDER/PATH",
    "provider": "WORDLIST_PROVIDER",
    "type":"STATIC/DYNAMIC"
}
```

Main structure of wordlist type:
```json
{
    "wordlist":[

        {"subdomain" : []},
        {"directory" : []},
        {"file" : []},
        {"api" : []},
        {"parameter" : []},
        {"header" : []},
        {"username" : []},
        {"password" : []},
        {"word" : []},
        {"technology" : []},
        {"payload" : []}
    ]
}

```

In wide and combin 2 last structure and create wordlsit file for download:

```json
{"wordlist":[
        {"TYPE_1" : [
                {
                "url": "WORDLIST_URL", 
                "fileName": "WORDLIST_FILENAME",
                "folder": "WORDLIST/FOLDER/PATH",
                "provider": "WORDLIST_PROVIDER",
                "type":"STATIC/DYNAMIC"
                },
                {
                "url": "WORDLIST_URL", 
                "fileName": "WORDLIST_FILENAME",
                "folder": "WORDLIST/FOLDER/PATH",
                "provider": "WORDLIST_PROVIDER",
                "type":"STATIC/DYNAMIC"
                }
            ]
        },
        {"TYPE_2" : [
                {
                "url": "WORDLIST_URL", 
                "fileName": "WORDLIST_FILENAME",
                "folder": "WORDLIST/FOLDER/PATH",
                "provider": "WORDLIST_PROVIDER",
                "type":"STATIC/DYNAMIC"
                },
                {
                "url": "WORDLIST_URL", 
                "fileName": "WORDLIST_FILENAME",
                "folder": "WORDLIST/FOLDER/PATH",
                "provider": "WORDLIST_PROVIDER",
                "type":"STATIC/DYNAMIC"
                }
            ]
        }
    ]
}
```

Sample file in [./static/](./static/) directory.


### Contributing

Hashtag-wordlist is young and new friend for wordlist provider and make useful wordlist form these provider:

<hr style="width: 40%;" >

- [https://wordlists.assetnote.io/](https://wordlists.assetnote.io/)
- [https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)
- [https://github.com/fuzzdb-project/fuzzdb](https://github.com/fuzzdb-project/fuzzdb)
- [https://github.com/PortSwigger/param-miner](https://github.com/PortSwigger/param-miner)
- [https://github.com/n0kovo/n0kovo_subdomains](https://github.com/n0kovo/n0kovo_subdomains)
- [https://github.com/xajkep/wordlists](https://github.com/xajkep/wordlists)
- [https://github.com/kkrypt0nn/wordlists](https://github.com/kkrypt0nn/wordlists)
- [https://github.com/six2dez/OneListForAll](https://github.com/six2dez/OneListForAll)
- [https://github.com/0xPugal/fuzz4bounty](https://github.com/0xPugal/fuzz4bounty)
- [https://github.com/the-xentropy/samlists](https://github.com/the-xentropy/samlists)
- [https://github.com/YA551N3/Bug-Bounty-Wordlists](https://github.com/YA551N3/Bug-Bounty-Wordlists)
- [https://github.com/Karanxa/Bug-Bounty-Wordlists](https://github.com/Karanxa/Bug-Bounty-Wordlists)
- [https://github.com/Escape-Technologies/graphql-wordlist](https://github.com/Escape-Technologies/graphql-wordlist)
- [https://github.com/HacktivistRO/Bug-Bounty-Wordlists](https://github.com/HacktivistRO/Bug-Bounty-Wordlists)
- [https://github.com/payloadbox/directory-payload-list](https://github.com/payloadbox/directory-payload-list)
- [https://github.com/orwagodfather/My-WordLISTs](https://github.com/orwagodfather/My-WordLISTs)
- [https://github.com/bashexplode/directory-wordlists](https://github.com/bashexplode/directory-wordlists)
- [https://github.com/s0md3v/Arjun/tree/master/arjun/db](https://github.com/s0md3v/Arjun/tree/master/arjun/db)
- [https://github.com/tamimhasan404/Wordlist404](https://github.com/tamimhasan404/Wordlist404)

<hr style="width: 40%;" >

Thanks for all repository for share these wordlist, you can make better this script too:)

Contributions are always welcome! I believe that great tools are built by great communities. Whether you’re fixing a bug, suggesting a feature, or simply sharing an idea, your contributions are invaluable. Together, we can make this project even better!

Dive in, share your expertise, and let’s create something amazing. Every pull request, issue, or suggestion helps shape the future of this tool. Let’s collaborate and innovate! 🌟

<hr style="width: 40%;" >


***Happy Learning :)***

***Happy Hunting*** 🎯