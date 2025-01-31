---
layout: essay
type: essay
title: "Smart Questions, Good Answers"
# All dates must be YYYY-MM-DD format!
date: 2025-01-30
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/Smart Questions.png">

## Is there such thing as a stupid question?

The idea that there are no stupid questions is commonly expressed by teachers and philosophers as a way to encourage continuous learning. However, the reality can sometimes be ironic. Consider, for example, someone asking, "Do you have a bathroom?" while they are in a residential home. This type of question suggests that, in fact, there can be such a thing as a silly or obvious question. Nonetheless, the broader intent of the saying is to foster an environment where people feel safe to ask and learn, regardless of how basic the question might seem.The perceived depth or triviality of a question often depends on the context in which it's asked. For example, the question "Why are we here?" could spark an extensive philosophical debate in a philosophy class. However, in a math class, the same question might be met with a pragmatic reply like, "Because you need the credits to graduate." This demonstrates how the setting can significantly influence the interpretation and response to a question.

## What’s a smart question?

Stack Overflow, a question and answer site for programmers, is a great resource for anyone who may have issues with code or who may simply want to learn new or different methods of doing something. There I found examples of good questions and bad questions, which could probably be improved.

In the following example, we examine the components of a decent question. In this case, the asker is trying to figure out a way to get the date six months from the current date using the datetime Python module?

```
Q: Date of six months from the current date using the datetime python module

I am trying to get the date of six months from the current date using the datetime python module. Here is what I have tried:

date(2015, 3, 31) + relativedelta(months = 6) gives datetime.date(2015, 9, 30). Perl: DateTime->new(year=>2000, month=>3, day=>31)->add(months=>6) gives 2000-10-01T00:00:00. Php: date_create('2000-03-31', new DateTimeZone('UTC'))->add(new DateInterval('P6M')) gives 2000-10-01.

However, the above comments strike me as silly. The concept of "adding six months" is quite clear -- take the month component and add 6 to it, with support for rolling over the year (and cycling the month back to 1) if we go past December. This happens to be exactly what relativedelta.

I have solved this trouble with:

echo $(date -d"3 month ago" "+%G%m%d")

from datetime import date, timedelta

# it's a lot faster with a constant day
DAY = timedelta(1)

def add_month(a_date, months):
    "Add months to date and retain last day in month."
    next_day = a_date + DAY
    # calculate new year and month
    m_sum = next_day.month + months - 1
    y = next_day.year + m_sum // 12
    m = m_sum % 12 + 1
    try:
        return date(y, m, next_day.day) - DAY
    except ValueError:
        # on fail return last day in month
        # can't fail on december so I don't bother changing the year
        return date(y, m + 1, 1) - DAY
I have not tested this code and i don't want to use it anyway (unless I can't find any other way:/)

Thanks for your help!
```

The title of the question could be clearer, but it effectively communicates the user's intent. Typically, users might search for terms like "date six months from today using Python datetime module" on search engines, enhancing its discoverability. Another positive aspect of the question is that it is not merely an inquiry; the asker also demonstrates the effort they have put into solving the problem themselves. Additionally, the courtesy shown by the asker in their query may not be as crucial as the content, but it certainly helps in increasing the likelihood of receiving a response.

```
A: Actually can manage to do this using datetime and MonthDelta

1. Write an algorithm using datetime.timedelta
2. Use a 3rd party library which implements an algorithm

Regarding third-party libraries :

 >>> import datetime
 >>> month_dt = 4
 >>> today = datetime.date.today()
 >>> y,m = today.year, today.month
 >>> m += month_dt-1
 >>> year_dt = m//12
 >>> new_month = m%12
 >>> new_date = datetime.date(y+year_dt, new_month+1, 1)
 
```
 
The asker received 50 possible answers, and he or she was successful in inciting discussion from multiple users. The answers themselves were clear and were devoid of the rumored sarcasm and hostility of “hackers.” Since I myself have referenced this page and found it useful, I can confidently say that it is a good question.

## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how can I ask better questions on Stack Overflow beyond reading the "How do I ask a good question?"

```
Q: How do I ask a good question?

If it is a good question, people usually only give one or two upvotes. I have read the How do I ask a good question page but I think I fulfil all requirements stated there. Here is one of my good questions which has only 94 views in 2 months and only one upvote (at the time of asking). According to the Help Center, I should add correct tags and an informative title, but I think people don't see questions when they have too many tags or are too specific. Usually, they just come and downvote (sometimes even without reading the full question), but don't explain why my questions deserve them.


```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to via external search engine (Google, etc). The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we depend on the generosity and expertise of others to answer our questions, it is important that our inquiries are well-crafted. A smartly posed question not only aids us but also benefits the responders and anyone else who may have similar queries in the future. Therefore, if you are going to ask a question, make sure it is a thoughtful one. While asking questions does not always guarantee the best answers, framing them in a way that engages others can significantly boost the chances of receiving a helpful response and enhance the experience for everyone involved.
