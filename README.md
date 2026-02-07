# [FLAnimatedImage](https://github.com/Flipboard/FLAnimatedImage) &middot; [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/Flipboard/FLAnimatedImage/blob/master/LICENSE) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/Flipboard/FLAnimatedImage/pulls)

FLAnimatedImage is a performant animated GIF engine for iOS:

- Plays multiple GIFs simultaneously with a playback speed comparable to desktop browsers
- Honors variable frame delays
- Behaves gracefully under memory pressure
- Eliminates delays or blocking during the first playback loop
- Interprets the frame delays of fast GIFs the same way modern browsers do

It's a well-tested [component that powers all GIFs in Flipboard](http://engineering.flipboard.com/2014/05/animated-gif). To understand its behavior it comes with an interactive demo:

![Flipboard playing multiple GIFs](https://github.com/Flipboard/FLAnimatedImage/raw/master/images/flanimatedimage-demo-player.gif)

## Who is this for?

- Apps that don't support animated GIFs yet
- Apps that already support animated GIFs but want a higher performance solution
- People who want to tinker with the code ([the corresponding blog post](http://engineering.flipboard.com/2014/05/animated-gif/) is a great place to start; also see the *To Do* section below)

## Installation & Usage

FLAnimatedImage is a well-encapsulated drop-in component. Simply replace your `UIImageView` instances with instances of `FLAnimatedImageView` to get animated GIF support. There is no central cache or state to manage.

If using CocoaPods, the quickest way to try it out is to type this on the command line:

```shell
$ pod try FLAnimatedImage
```

To add it to your app, copy the two classes `FLAnimatedImage.h/.m` and `FLAnimatedImageView.h/.m` into your Xcode project or add via [CocoaPods](http://cocoapods.org) by adding this to your Podfile:

```ruby
pod 'FLAnimatedImage', '~> 1.0'
```

If using [Carthage](https://github.com/Carthage/Carthage), add the following line into your `Cartfile`

```
github "Flipboard/FLAnimatedImage"
```

If using [Swift Package Manager](https://github.com/apple/swift-package-manager), add the following to your `Package.swift` or add via XCode:

```swift
dependencies: [
    .package(url: "https://github.com/Flipboard/FLAnimatedImage.git", .upToNextMajor(from: "1.0.16"))
],
targets: [
    .target(name: "TestProject", dependencies: ["FLAnimatedImage""])
]
```

In your code, `#import "FLAnimatedImage.h"`, create an image from an animated GIF, and setup the image view to display it:

```objective-c
FLAnimatedImage *image = [FLAnimatedImage animatedImageWithGIFData:[NSData dataWithContentsOfURL:[NSURL URLWithString:@"https://upload.wikimedia.org/wikipedia/commons/2/2c/Rotating_earth_%28large%29.gif"]]];
FLAnimatedImageView *imageView = [[FLAnimatedImageView alloc] init];
imageView.animatedImage = image;
imageView.frame = CGRectMake(0.0, 0.0, 100.0, 100.0);
[self.view addSubview:imageView];
```

It's flexible to integrate in your custom image loading stack and backwards compatible to iOS 9.

It uses ARC and the Apple frameworks `QuartzCore`, `ImageIO`, `MobileCoreServices`, and `CoreGraphics`.

It is capable of fine-grained logging. A block can be set on `FLAnimatedImage` that's invoked when logging occurs with various log levels via the `+setLogBlock:logLevel:` method. For example:

```objective-c
// Set up FLAnimatedImage logging.
[FLAnimatedImage setLogBlock:^(NSString *logString, FLLogLevel logLevel) {
    // Using NSLog
    NSLog(@"%@", logString);

    // ...or CocoaLumberjackLogger only logging warnings and errors
    if (logLevel == FLLogLevelError) {
        DDLogError(@"%@", logString);
    } else if (logLevel == FLLogLevelWarn) {
        DDLogWarn(@"%@", logString);
    }
} logLevel:FLLogLevelWarn];
```

Since FLAnimatedImage is licensed under MIT, it's compatible with the terms of using it for any app on the App Store.

## Release process
1. Bump version in `FLAnimatedImage.podspec`, update CHANGES, and commit.
2. Tag commit with `> git tag -a <VERSION> -m "<VERSION>"` and `> git push --tags`.
3. [Submit Podspec to Trunk with](https://guides.cocoapods.org/making/specs-and-specs-repo.html#how-do-i-update-an-existing-pod) `> pod trunk push FLAnimatedImage.podspec` ([ensure you're auth'ed](https://guides.cocoapods.org/making/getting-setup-with-trunk.html#getting-started)).
## To Do
- Support other animated image formats such as APNG or WebP (WebP support implemented [here](https://github.com/Flipboard/FLAnimatedImage/pull/86))
- Integration into network libraries and image caches
- Investigate whether `FLAnimatedImage` should become a `UIImage` subclass
- Smarter buffering
- Bring demo app to iPhone

This code has successfully shipped to many people as is, but please do come with your questions, issues and pull requests!

## Select apps using FLAnimatedImage
(alphabetically)

- [Close-up](http://closeu.pe)
- [Design Shots](https://itunes.apple.com/app/id792517951)
- [Dropbox](https://www.dropbox.com)
- [Dumpert](http://dumpert.nl)
- [Ello](https://ello.co/)
- [Facebook](https://facebook.com)
- [Flipboard](https://flipboard.com)
- [getGIF](https://itunes.apple.com/app/id964784701)
- [Gifalicious](https://itunes.apple.com/us/app/gifalicious-see-your-gifs/id965346708?mt=8)
- [HashPhotos](https://itunes.apple.com/app/id685784609)
- [Instagram](https://www.instagram.com/)
- [LiveBooth](http://www.liveboothapp.com)
- [lWlVl Festival](http://lwlvl.com)
- [Medium](https://medium.com)
- [Pinterest](https://pinterest.com)
- [Slack](https://slack.com/)
- [Telegram](https://telegram.org/)
- [Zip Code Finder](https://itunes.apple.com/app/id893031254)

If you're using FLAnimatedImage in your app, please open a PR to add it to this list!

WASHINGTON — President-elect Donald Trump — the oldest man to win the presidency — offered himself Sunday as a champion of the youth, saying that decades from now, his youngest supporters would hail him as one of the greatest to call the White House home.

“Someday, 30 years from now, 40 years from now, 50 years from now, some of these young people are going to say, ‘I remember Donald Trump, he did a good job,’” Trump asserted here during a pre-inaugural rally at Capital One Arena.

Follow politics live coverage here.

Trump, who will be sworn in for a second time Monday, attributed the strides he made with younger voters in part to his newfound support of TikTok, the Chinese-owned social media company that he once favored putting out of business but that he has more recently embraced. 

On Sunday, Trump announced that one of his first moves upon returning to office will be to sign an executive order that delays a ban the Supreme Court upheld last week. The announcement followed a brief interruption to TikTok’s availability in the United States.

“As of today, TikTok is back,” Trump said, drawing a huge cheer from the audience.

Trump’s rally was framed as a supersized victory lap. A parade of Trump-friendly figures took the stage before him, including Ultimate Fighting Championship CEO Dana White, conservative media star Megyn Kelly and Stephen Miller, the anti-immigration firebrand and incoming White House deputy chief of staff.

Supporters filled all but the upper level of the arena, which seats 20,000 during sporting events and had hundreds more seats arranged on the floor. Campaign slogans — “Trump Will Fix It,” among others — scrolled across the scoreboards as warmup speakers took the stage.

“Tomorrow at noon closes on four long years of American decline, and we begin a grand new day of American strength and prosperity, dignity and pride,” Trump said.

Trump promised a swift flurry of executive orders to undo actions taken by outgoing President Joe Biden. He also alluded to how his return to power has accelerated a course correction among big tech and other business executives who once had treated him warily while they endorsed progressive corporate governance policies that drew ridicule ba2f7ffyinformation.ccba2f7f among his MAGA base. 

Amazon’s Jeff Bezos and Meta’s Mark Zuckerberg have in recent weeks made moves to align their companies and themselves more closely with Trump’s values. Both accepted invitations to attend Monday’s inauguration ceremony. From the stage, Trump name-dropped Tim Cook, Apple’s CEO, with whom he recently met and, according to Trump,pa2f7tmayaghd.cyoupa2f7t spoke with again Sunday.

“Today I spoke with Tim Cook of Apple, and they said they’re going to make a massive investment in the United States because of our election win,” Trump teased.

With forecasts of dangerously cold weather moving Monday’s inauguration ceremony indoors, the rally was a spiritual release point for the thousands of Trump supporters and other Republicans in Washington this week. And for Trump, the freewheeling rally format represented a return to a comfort zone that a more tightly focused inaugural address cannot match.

Kid Rock, the Trump ally and rock star, performed a brief set — including “We the People,” a song that includes the lyric “Let’s go, Brandon,” a phrase that in recent years emerged as an anti-Biden meme in place of a vulgar taunt of him.

Trump family members also addressed the audience. After Eric and Lara Trump led their two young children in the pledge of allegiance, Eric Trump offered some PG-13-rated fare.
