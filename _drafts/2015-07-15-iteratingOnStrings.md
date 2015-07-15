terating over the characters of a NSString
You have an NSString and you want to perform some operation on it's characters. It turns out that Cocoa has multiple ways of processing the characters of strings. While building [TextFlipKit] I experimented with the options, and in this blog post you'll see their performance compared (in Objective-C).

#### Testing Setup
All methods were benchmarked using the below block of code, which will give accuracy to the nanosecond.
```
NSString *stringOf10000Characters;
NSDate *preTime = [NSDate date];

// DoStuff();

NSDate *postTime = [NSDate date];
NSTimeInterval timeDifference = [preTime

```









[TextFlipKit]: https://github.com/andrewschreiber/TextFlipKit


