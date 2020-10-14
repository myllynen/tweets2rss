# tweets2rss

[![License: GPLv2](https://img.shields.io/badge/license-GPLv2-brightgreen.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

A simple Python script to generate RSS feeds from Twitter feeds.

## Disclaimer

This tool is provided for educational purposes only.

Please read and comply with [Twitter Terms of Service](https://twitter.com/en/tos)
before downloading or using this tool.

## Requirements

* [Python 3](https://www.python.org/)
* [Twint](https://github.com/twintproject/twint)
  * Use [pip](https://pypi.org/project/pip/) to install the latest version,
    (and in case it is not recent enough, use the latest code from their repo)
    * `pip install --user --upgrade twint`

## Usage

1. Ensure twint is working as expected
  ```
  twint -u jack
  ```
2. Create directory for RSS feed files
  ```
  mkdir ~/.rss
  ```
3. Create configuration on whom to follow
  ```
  echo jack > ~/.rss/users.txt
  ```
4. Run the tool
  ```
  tweets2rss -Y -Z
  ```
5. Read the generated RSS feeds with your favorite RSS reader
   (run a simple HTTP server if needed)

## Tips

* Use the simple [rssserver](rssserver) script to start Python HTTP server
* Create configuration files for different types of users, for example:
  * One to be used with common options
  * One to be used with users retweeting a lot
* Use [cron](https://en.wikipedia.org/wiki/Cron) for periodic updates

An example of [crontab](https://man7.org/linux/man-pages/man5/crontab.5.html)
entries:

```Shell
@reboot $HOME/.local/bin/rssserver
5 * * * * $HOME/.local/bin/tweets2rss -Y -Z -u $HOME/.rss/users.txt > /dev/null 2>&1
5 * * * * $HOME/.local/bin/tweets2rss -Y -z -u $HOME/.rss/users-no-rt.txt > /dev/null 2>&1
```

## License

GPLv2+
