---
layout: essay
type: essay
title: "Programming is technical writing"
# All dates must be YYYY-MM-DD format!
date: 2025-02-13
published: True
labels:
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="800px" class="rounded float-start pe-4" src="../img/smart-questions/codestyle.png">

Throughout my undergraduate studies in India, I faced significant difficulties in understanding coding. I clearly remember the initial programming class I took; it seemed a foreign language that I was forced to learn overnight. While the professor was describing conditionals and loops, all I could see on the screen were perplexing symbols and arbitrary terms like while, if, and otherwise. Reading nonfiction is fun for me. Not just computing, but also biology, physics, philosophy, robotics, mechanical engineering, and other technical subjects.
Writing this code is significantly more challenging, as it involves not only instructing a computer but also contending with another user's cognitive framework regarding your code. Computer science and reasoning psychology are now equally important, or something. How can you facilitate that individual’s understanding of your code?In fact, I think that learning a programming language can be aided by certain coding standards.



Feynman famously said: Imagine how much harder physics would be if electrons had feelings. about something very different, but in a funny way I think this describes programming for humans a bit. The person interpreting your code actually has feelings!Humans are exceptional at recognizing patterns, whereas computers adhere to Boolean logic and execute precise commands. Developer tool documentation is frequently organized like a computer program. It begins by defining a fundamental data model together with its relationships and components. 
A human conversation on the other hand, or a novel, or a political speech, pulls on unseen associations via language, and they connote complex world views and intentions which cannot be ascribed to any particular moment or a smaller chunk of words. We are, in the parlance of data science, neural-net driven pattern recognition machines. However, the way it feels to listen to a politician on screen doesn’t feel anything like back-propagating a loss function through hidden layers to adjust the weights and biases of a neural net.

It feels gooey, and human. Just like writing.

```
Q: python date of the previous month

I am trying to get the date of the previous month with python. Here is what i've tried:

str( time.strftime('%Y') ) + str( int(time.strftime('%m'))-1 )

However, this way is bad for 2 reasons: First it returns 20122 for the February of 2012 (instead of 201202) 
and secondly it will return 0 instead of 12 on January.

I have solved this trouble in bash with:

echo $(date -d"3 month ago" "+%G%m%d")

I think that if bash has a built-in way for this purpose, then python, much more equipped, should provide something 
better than forcing writing one's own script to achieve this goal. Of course i could do something like:

if int(time.strftime('%m')) == 1:
    return '12'
else:
    if int(time.strftime('%m')) < 10:
        return '0'+str(time.strftime('%m')-1)
    else:
        return str(time.strftime('%m') -1)
        
I have not tested this code and i don't want to use it anyway (unless I can't find any other way:/)

Thanks for your help!
```

While the heading of his question could be better, it does convey what he’s trying to figure out. Usually something as brief as “python date of previous month” is what other users would enter in as search terms on Google, making it easily found. Another good thing about the question is that it’s not just a question. The asker shows what he or she has done and that he or she has put in some effort to answer the question. And while it may not be as important as the question itself, the asker shows courtesy, which does increase the chance of getting an answer.

```
A: datetime and the datetime.timedelta classes are your friend.

1. find today
2. use that to find the first day of this month.
3. use timedelta to backup a single day, to the last day of the previous month.
4. print the YYYYMM string you're looking for.

Like this:

 >>> import datetime
 >>> today = datetime.date.today()
 >>> first = datetime.date(day=1, month=today.month, year=today.year)
 >>> lastMonth = first - datetime.timedelta(days=1)
 >>> print lastMonth.strftime("%Y%m")
 201202
 >>>

```
 
The asker received six possible answers, and he or she was successful in inciting discussion from multiple users. The answers themselves were clear and were devoid of the rumored sarcasm and hostility of “hackers.” Since I myself have referenced this page and found it useful, I can confidently say that it is a good question.

## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how he would, in short, create a desktop application with Facebook.

```
Q: Facebook Desktop Notifier

I am a beginner programmer that have never used anything other than what's included in a language.

I am trying to create a desktop application that notifies me anytime I get an update onfacebook. 
How should go about doing this? Thanks in advance.

edit Sorry I was not clear. Is there any way to make a DESKTOP application with facebook?
```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to Facebook’s developer website. The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we rely on others’ generosity and expertise to provide answers to our questions, it should hold that the question we ask should be one that leads to efficient and effective help that not only benefits us, but also the people we ask and others who might ask the same question in the future. Thus, if you have a question… make it a smart one! Asking questions may not always get you the best answer, but asking them in a way that will make others want to answer them will increase the success of finding a good solution and make it a positive experience on all sides.
