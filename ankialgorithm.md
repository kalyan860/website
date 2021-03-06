# Anki Algorithm

# Learning steps
It is the number of times you have to see a card before it graduates. 
It contains minimun 2 values (or more ), first indicates time after hitting again and places you in the first step again.
Hitting good advances you to next learning step, hitting good on last learning step graduates the card. 
Hitting easy finishes learning steps, graduates the card and the "easy interval" will be the next interval used, which will be longer than the graduating interval.
The card is now reviewed at a fixed interval set manually called "graduating interval"
From now on, anki uses its algorithm to determine next interval by using graduating interval as the base. Default is 2.5 times the previous interval.
Ease factor does not change during learning steps upon hitting any button.

# Optimising learning steps
It is useful to extend learning steps upto 3 days days so that ease factor changes don't apply and hard material can be safely internalised without making it a frequent card forever.
Idea is to set learning steps as follows: 1min (again), 10 min, 1 day, 3 day. And to set graduating interval to 7 days.
Easy interval could also be set to 7 days or a bit more.  
Longer intervals, mixing up new cards in random order allows short term memory to not interfere with learning thus not creating a false sense of knowledge.

# Next interval for review.
The formula is: **New interval = current interval x Interval modifier x ease factor x ease bonus x fuzz factor.**
current interval is either the graduating interval for "good" card, ease interval set for easy card during learning, or the new interval set for lapses.
ease factor is 2.5 by default and changes whenever you use any button other than good.
Interval modifier is a constant which is by default 1. (so does nothing).
Ease bonus is also a constant, set at 1.3 by default and is applied to easy cards further lengthening the easy card review time.
Fuzz factor is a random variable ranging from 0.8 to 1.2 set so that all reviews do not fall on the same day. This is useful if you do a ton of cards on a single day and not many on other days.

# Buttons
Default ease factor is 2.5. Buttons change it this way.
Again -20%
Hard -15%
Easy %15
Good no change
Ease factor is the only permanent change for a card, rest of them change easily.

# Lapses, new interval
When you press again, the review card will be marked as a lapse and is put in learning phase again.
You can customise these relearning steps which can be set same as learning steps or different.
Once graduated, instead of using graduating intervals, review cards use **"new interval for lapses = current interval x interval modifier"**
Setting interval modifier to 0 treats the card as totally new cards and makes it use the normal graduating interval.
Setting it a value, for eg. 0.5 gives it the next interval value as half of the previous one.

# Hard interval
Is the multiplier added to cards when pressing hard. It is 1.2 by default.
In contrast, new interval is the multiplier used when again is pressed, it is 0 by default but best to set it to 0.5 or 0.6. 

# Leeches
Leeches are those which you repeatedly get wrong like 4 or 5 times. Consider either deleting them, rephrasing them or suspending for a while. 

# Tweaking the algorithm to avoid ease hell
As you press "again" many times, the ease factor decreases and card will keep appearing again and again. (pressing ease on them could improve them but it can cause the problem to be shifted to the other extreme end. 
First, stop pressing Hard and easy buttons. They change ease factor permanently.
Change ease factor default value to 1.3 as it can't go lower than that when "again" is pressed.
Change interval modifier to 1.9 to compensate as 1.9 x 1.3 is 2.5 which is same as setting EF to 2.5.
You can use refold ease add on to set ease values of all cards back to normal which were damaged.

# Sample examples for understanding.
Assuming cards graduate with one day interval and the 2.5 multiplier for good:
The next days for review will be (counted from day 1, not intervals): 
- 1 day
- 4 day
- 2 week
- 1 month
- 2 month
- 4 month
- 6 month 
- 1 year
So after 7 reviews, the interval will be 6 months. Thus some 7 reviews are needed to make something fixed in longterm memory.

