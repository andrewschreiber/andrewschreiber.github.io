---
layout: post
title: Iterating on NSAttributedStrings
categories: 
tags:
description: Code findings from working on TextFlipKit
---

If you don't need the attributes of the characters, use:

```
NSString *plainString = attributedString.string;
```
Then do normal string iteration. However, if you **do** need the attributes of the characters (as I did in [TextFlipKit]), use the following :

    [attributedString enumerateAttributesInRange: NSMakeRange(0, attributedString.length)

             options: NSAttributedStringEnumerationLongestEffectiveRangeNotRequired 
    
          usingBlock: ^(NSDictionary *attrs, NSRange range, BOOL *stopAttributed)
    {
        [attributedString.string enumerateSubstringsInRange: range 
        
                        options: NSStringEnumerationByComposedCharacterSequences 
                     usingBlock: ^(NSString *nextCharacter, 
                                   NSRange substringRange, 
                                   NSRange enclosingRange, 
                                   BOOL *stopString)
        {
           //Do stuff with nextCharacter
        }];
    }];

The above takes about 7 milliseconds on my iPhone 6 to iterate over 10,000 characters. Also, you're guaranteed to get only one value at a time, unlike iterating over unicode buffers which can sometimes give you multiple values representing a single character. If you want to stop the loop midway through, you can call:

``` 
*stopString = YES;
```









[TextFlipKit]: https://github.com/andrewschreiber/TextFlipKit


