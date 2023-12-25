---
title: "Code Chronicles: Unraveling the Credit Card Tracking Mystery"
slug: code-chronicles-cc-tracking-1
date: 2023-12-26
authors:
  - abrar-ajaz
image: /static/img/visa-credit-card-feature-compressed.jpg
toc: false
comments: false
tags:
  - programming
isFeatured: true
description: Explore the intriguing journey of solving a misplaced digit mystery
  in a credit card tracking ID with this programming tale. Discover O as a
  skilled Full Stack Developer leveraged programming prowess to tackle a unique
  challenge. Follow along as the narrative unfolds—from the excitement of credit
  card approval to the unexpected hurdle of a misplaced tracking ID digit.
---
BismillahirRahmanirRahim
Recently, I was approached by my bank saying that I was meeting all the requirements to have a credit card. Having a credit card is cool as it lets you build your CIBIL score and avail exciting offers available out there. So, I thought of giving it a shot and I applied for it.

After some couple of days my credit card was delivered to my primary branch that is in Srinagar. But the problem was - I was in my native village beloved Sogam and didn’t have plans to travel to the capital city for a while. Therefore, I asked my bank associate to redirect my credit card to my nearest branch that was situated in the main town Kupwara.

My bank associate redirected my card through Indian Post and provided me with a tracking ID. Upon tracking my card using the tracking ID it showed no records. For a couple of days I thought the ID was not yet registered but finally I decided to check out the format. Generally, the Indian Post’s tracking id is 13 digit long but the id i received (**EE91885758IN**) was only 12 digits. So 1 digit was misplaced. I asked my bank associate to resend me the correct ID but he didn’t have it by then.

As I am a programmer, I saw this situation as a programming challenge. The misplaced digit could be anything from `0-9` and it could be at any place between E to I. Therefore, I opened my ChatGPT and asked it to write a program to enumerate the combination for a tracking ID at a single placeholder. My ChatGPT replied with a program in the python programming language that was able to generate tracking id by replacing X in the original id with 0,1,2,3 ... .9. 

```python
def generate_combinations(pattern):
    combinations = []
    for digit in range(10): 
        combination = pattern.replace('X', str(digit))
        combinations.append(combination)
    return combinations

# Example with the India Post tracking ID pattern
india_post_pattern = "EE91885758XIN"
all_combinations = generate_combinations(india_post_pattern)

# Displaying all generated combinations
for combination in all_combinations:
    print(combination)
```

This program was cool but not clever. As it required to enter different patterns one by one as the missing digit could be anywhere from EE to IN. After modifying the program looked good to go for my situation:

```python
def generate_combinations(pattern):
    combinations = []
    for digit in range(10):
        combination = pattern.replace('X', str(digit))
        combinations.append(combination)
    return combinations

# Example with the India Post tracking ID pattern
def generate(india_post_pattern):
    all_combinations = generate_combinations(india_post_pattern)
    # Displaying all generated combinations
    for combination in all_combinations:
        print(combination)


india_post_pattern = ["EE91885758XIN",'EE9188575X8IN', 'EE918857X58IN','EE91885X758IN', 'EE9188X5758IN', 'EE918X85758IN', 'EE91X885758IN', 'EE9X1885758IN','EEX91885758IN']

for i in india_post_pattern:
    generate(i)
```

After running this program I got around 90 different tracking IDs generated.

Now the problem was to validate them and find which ids are working. And among the working IDs which one is mine. I found a website called https://www.trackingmore.com/ which lets you to track multiple Ids at the same time. 

![Screenshot](/static/img/post/post-1.png "Screenshot")

So I copied IDs and pasted it into this website. Upon looking at the results I found just two working IDs. One ID belong to some courier for some personal at Air Defence and the another was mine (**EE918865758IN**).

By this I concluded that computers when met with creativity and passion can be a great solution to the wide range of problems. Finally, I have my credit card now and an adventurous story behind its tracking.