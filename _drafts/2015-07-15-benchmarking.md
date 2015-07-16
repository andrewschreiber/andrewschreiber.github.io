OS Benchmarking (Speed)

>Optimizing code means taking an existing program and changing it to use less of something, usually time or memory. You don't have to think about what the program should do, just make it faster. For most programmers this is very satisfying work.  
-Paul Graham, Startup = Growth

On iOS, efficient code often translates into a golden user experience. This observation is best demonstrated by it's inverses: the boredom of watching a loading screen or the frustration of crashing to the home screen. Benchmarking code ferrets out performance bottlenecks and improves your understanding of your tools. Thereby benchmarking, like all forms of tests, helps deliver snappy, reliable apps to your users. And on iOS its a ton of fun.

##Setup
In this post, I will omit Instruments and focus entirely on benchmarking with code. Instruments is powerful for investigating a call stack and tracing allocations, but programmatic tools are more pragmatic when repeating tests thousands of times or when benchmarking outside of a debugging context. Benchmarking with code usually looks something like this:
```
-(void)testDoStuff
{
// Benchmark start
// DoStuff();
// Benchmark stop
// Report findings
}
```
You can create most benchmarks either in your test target or your main target. Creating benchmarks in your test target is generally the safer route, but you need to use your main target if you record benchmarks on live users. 
##Speed benchmarking
One of the joys of engineering is making things go faster.
![](https://www.aptitudesoftware.com/wp-content/uploads/FAST-TURTLE.jpg)
In Cocoa, I've found 6 different APIs that can be used to measure the speed of a given block of code: 
- **NSDate**
- **CACurrentMediaTime**
- **dispatch_benchmark**
- **mach_absolute_time( )**
- **measureBlock**
- **CFAbsoluteTimeGetCurrent()**

Let's create some criteria for the "best way", with that criteria being a combination of **precision**, **consistency**, and **ease of use**. I will append an NSMutableArray with 10,000 instances of NSNull on my iPhone 6 as a performance test. Let's see how the benchmarks benchmark!

####NSDate
```

```



##Memory benchmarking
// autorelease pool for loop vs without






[TextFlipKit]: https://github.com/andrewschreiber/TextFlipKit


