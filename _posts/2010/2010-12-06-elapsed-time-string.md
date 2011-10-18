---

title: Elapsed Time String in Objective-C
layout: default

---

Here's a simple but useful NSString category for getting the elapsed time from a given date until now and formatting it ("posted 5 minutes ago"). You can learn more about categories [here](http://cocoadevcentral.com/d/learn_objectivec/).

    #import <Foundation/Foundation.h>

    @interface NSString (Extensions)
    + (NSString *)timeAgoStringFromDate:(NSDate *)fromDate;
    @end

    #import "NSString+Extensions.h"

    #define FormatterString @"%i %@ ago"

    @implementation NSString (Extensions)

    + (NSString *)timeAgoStringFromDate:(NSDate *)fromDate
    {
        NSUInteger desiredComponents = NSYearCalendarUnit | NSMonthCalendarUnit | NSWeekCalendarUnit | NSHourCalendarUnit | NSDayCalendarUnit | NSMinuteCalendarUnit | NSSecondCalendarUnit;
        NSDateComponents *elapsedTime = [[NSCalendar currentCalendar] components:desiredComponents 
                                                                             fromDate:fromDate
                                                                               toDate:[NSDate date]
                                                                              options:0];
        NSString *timeAgo = nil;
        
        if ([elapsedTime year]) {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime year],
                       ([elapsedTime year] == 1) ? @"year" : @"years"];
        }
        else if ([elapsedTime month]) {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime month],
                       ([elapsedTime month] == 1) ? @"month" : @"months"];
        }
        else if ([elapsedTime week]) {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime week],
                       ([elapsedTime week] == 1) ? @"week" : @"weeks"];
        }
        else if ([elapsedTime day]) {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime day],
                       ([elapsedTime day] == 1) ? @"day" : @"days"];
        }
        else if ([elapsedTime hour]) {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime hour],
                       ([elapsedTime hour] == 1) ? @"hour" : @"hours"];
        }
        else if ([elapsedTime minute]) {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime minute],
                       ([elapsedTime minute] == 1) ? @"minute" : @"minutes"];
        }
        else {
            timeAgo = [NSString stringWithFormat:FormatterString, [elapsedTime second],
                       ([elapsedTime second] == 1) ? @"second" : @"seconds"];
        }

        return timeAgo;
    }

    @end

#### Potential Problems

Make sure both dates are translated to the correct time zone. If you start seeing wrong values ("this was posted -4 hours ago!") then that's probably what's going on.

    // set the time zone of the date value used
    [dateFormatter setTimeZone:[NSTimeZone timeZoneWithAbbreviation:@"GMT"]];

    // To set the time zone of the calendar that we use to get the elapsed time, do this:
    NSCalendar *cal = [NSCalendar currentCalendar];
    [cal setTimeZone:[NSTimeZone localTimeZone]];
    NSDateComponents *elapsedTime = [cal components:desiredComponents fromDate:fromDate toDate:[NSDate date] options:0];

For more information check out the [Apple time & date docs](http://developer.apple.com/library/ios/#documentation/cocoa/Conceptual/DatesAndTimes/DatesAndTimes.html#//apple_ref/doc/uid/10000039i).
