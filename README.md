# tweets2rss

[![License: GPLv2](https://img.shields.io/badge/license-GPLv2-brightgreen.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

A simple Python script to generate RSS feed from Twitter feeds.

## Disclaimer

This tool is provided for educational purposes only.

Please read and comply with [Twitter Terms of Service](https://twitter.com/en/tos)
before downloading or using this tool.

## Requirements

* [Python 3](https://www.python.org/)
* [Twint](https://github.com/twintproject/twint)
  * Use [pip](https://pypi.org/project/pip/) to install the latest version,
    and in case it is not recent enough, use the latest code in their repo
    * `pip install --user --upgrade twint`

## Usage

1. Create directory for RSS feed files
  * `mkdir ~/.rss`
2. Create configuration on whom to follow
  * `echo jack > ~/.rss/users.txt`
3. Run the tool
  * `tweets2rss -Y -Z`
4. Read the generated RSS feeds with your favorite RSS reader
  * Run a simple HTTP server if needed

## Tips

* Use the simple [rssserver](rssserver) script to start Python HTTP server
* Create configuration files for different types of users, for example:
  * One to be used with common options
  * One to be used with users retweeting a lot
* Use [cron](https://en.wikipedia.org/wiki/Cron) for periodic updates

```Shell
@reboot /home/testuser/.local/bin/rssserver
5 * * * * /home/testuser/.local/bin/tweets2rss -Y -Z -u /home/testuser/.rss/users.txt > /dev/null 2>&1
5 * * * * /home/testuser/.local/bin/tweets2rss -Y -z -u /home/testuser/.rss/users-no-rt.txt > /dev/null 2>&1
```

## License

GPLv2+
