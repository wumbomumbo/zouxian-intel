# zouxian 走线

中文版请见[这里](https://github.com/CatMe0w/zouxian/blob/master/README_zh.md)。

This is a fork of zouxian which has the extra ability to enable the Apple Intelligence menu in settings on Intel Macs.

Currently, all this does is enable the menu in Settings, and makes it appear that it's doing something, but it really isnt.
IIRC the Anvil framework is blocking Apple Intellignece from working as it's detecting you are not using an M-series Mac.
You can force more functionality of Apple Intelligence by editing the FeatureFlags located in the system files, however this WILL make your Mac very slow, and it still won't properly function.

---

Persistent solution after rebooting, based on [Cyandev's guide](https://gist.github.com/unixzii/6f25be1842399022e16ad6477a304286).

## Version table

| From                   | To             |                                                                                                           |
| ---------------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| Macintosh System 1     | 14.6 (23G80)   | Not applicable                                                                                            |
| 15.0 Beta 1 (24A5264n) | 15.3.1 (24D70) | Install [Darwin Eligibility Override](https://github.com/CatMe0w/zouxian/blob/master/repatriate_guide.md) |
| 15.4 Beta 1 (24E5206s) | ?              | Install zouxian                                                                                           |

## Disclaimer

Disabling SIP will reduce the security of the system and make iOS apps in App Store and Apple Pay unusable.

## Install

### Prerequisites

- SIP debugging restrictions are disabled (via `csrutil enable --without debug` command in recovery mode).
- For Apple Intelligence: A non-China Apple ID signed in, region set to the United States, and language set to English (US).
- For Xcode Predictive Code Completion: Xcode is installed and run at least once.

> [!NOTE]  
> No need to install Xcode if you only want to use Apple Intelligence.

### Method 1: Via [Homebrew](https://brew.sh)

```shell
brew install catme0w/tap/zouxian
sudo brew services start zouxian
```

> Check out [the formula](https://github.com/CatMe0w/homebrew-tap/blob/master/Formula/zouxian.rb) if you're interested

### Method 2: Manually

```shell
sudo curl https://raw.githubusercontent.com/wumbomumbo/zouxian-intel/master/zouxian.sh -o /usr/local/bin/zouxian
sudo chmod +x /usr/local/bin/zouxian
sudo curl https://raw.githubusercontent.com/wumbomumbo/zouxian-intel/master/cat.me0w.zouxian.plist -o /Library/LaunchDaemons/cat.me0w.zouxian.plist
sudo launchctl load -w /Library/LaunchDaemons/cat.me0w.zouxian.plist
```

## Uninstall

### If Installed Via [Homebrew](https://brew.sh)

```shell
sudo brew services stop zouxian
sudo rm -rf /opt/homebrew/Cellar/zouxian
brew untap catme0w/tap
```

### If Installed Manually

```shell
sudo launchctl unload -w /Library/LaunchDaemons/cat.me0w.zouxian.plist
sudo rm /Library/LaunchDaemons/cat.me0w.zouxian.plist
sudo rm /usr/local/bin/zouxian
```

## Acknowledgement

Thanks for those who make this possible together: [Kyle-Ye](https://github.com/Kyle-Ye), [Cyandev](https://twitter.com/unixzii), [Lakr233](https://twitter.com/Lakr233), [Sou1gh0st](https://twitter.com/Sou1gh0st), Yuriko.

## License

MIT License
