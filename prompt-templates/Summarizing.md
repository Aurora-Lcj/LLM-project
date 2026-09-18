#总结类prompt模板\
#文本内容\
text="""
        #文本内容\
"""
prompt="""\
          #总体的模糊任务\
          #总体任务中各个具体要求（包括字数、总结侧重点、输出格式）\
          ```{text}```\
#示例\
#示例文本
text = """\
Got this panda plush toy for my daughter's birthday, \
who loves it and takes it everywhere. It's soft and \ 
super cute, and its face has a friendly look. It's \ 
a bit small for what I paid though. I think there \ 
might be other options that are bigger for the \ 
same price. It arrived a day earlier than expected, \ 
so I got to play with it myself before I gave it \ 
to her.
"""

#text中文版
text = """
这个熊猫公仔是我给女儿的生日礼物，她很喜欢，去哪都带着。
公仔很软，超级可爱，面部表情也很和善。但是相比于价钱来说，
它有点小，我感觉在别的地方用同样的价钱能买到更大的。
快递比预期提前了一天到货，所以在送给女儿之前，我自己玩了会。
"""


#示例prompt
prompt = f"""
您的任务是从电子商务网站上生成一个产品评论的简短摘要。#总体任务
请对三个反引号之间的评论文本进行概括，最多30个词汇，并且聚焦在产品价格和质量上。#具体要求，如字数限制、总结侧重点
文本: ```{text}```
"""
response = get_completion(prompt)
print(response)


#可通过for循环进行多文本总结\

text_1="""\
          #文本内容
"""\
text_2="""\
          #文本内容
"""\
text_3="""\
          #文本内容
"""\
texts=[text,text_1,text_2,text_3]\
for i in range(len(texts)):
  prompt="""\
            #总体任务\
            #具体要求\
            ```{texts[i]}```
  """
  response = get_completion(prompt)
  print(i,response,"\n")
  
#示例同时总结多文本\
# review for a standing lamp
text_1 = """
Needed a nice lamp for my bedroom, and this one \
had additional storage and not too high of a price \
point. Got it fast - arrived in 2 days. The string \
to the lamp broke during the transit and the company \
happily sent over a new one. Came within a few days \
as well. It was easy to put together. Then I had a \
missing part, so I contacted their support and they \
very quickly got me the missing piece! Seems to me \
to be a great company that cares about their customers \
and products.
"""
# review for an electric toothbrush
text_2 = """
My dental hygienist recommended an electric toothbrush, \
which is why I got this. The battery life seems to be \
pretty impressive so far. After initial charging and \
leaving the charger plugged in for the first week to \
condition the battery, I've unplugged the charger and \
been using it for twice daily brushing for the last \
3 weeks all on the same charge. But the toothbrush head \
is too small. I’ve seen baby toothbrushes bigger than \
this one. I wish the head was bigger with different \
length bristles to get between teeth better because \
this one doesn’t.  Overall if you can get this one \
around the $50 mark, it's a good deal. The manufactuer's \
replacements heads are pretty expensive, but you can \
get generic ones that're more reasonably priced. This \
toothbrush makes me feel like I've been to the dentist \
every day. My teeth feel sparkly clean!
"""
# review for a blender
text_3 = """
So, they still had the 17 piece system on seasonal \
sale for around $49 in the month of November, about \
half off, but for some reason (call it price gouging) \
around the second week of December the prices all went \
up to about anywhere from between $70-$89 for the same \
system. And the 11 piece system went up around $10 or \
so in price also from the earlier sale price of $29. \
So it looks okay, but if you look at the base, the part \
where the blade locks into place doesn’t look as good \
as in previous editions from a few years ago, but I \
plan to be very gentle with it (example, I crush \
very hard items like beans, ice, rice, etc. in the \
blender first then pulverize them in the serving size \
I want in the blender then switch to the whipping \
blade for a finer flour, and use the cross cutting blade \
first when making smoothies, then use the flat blade \
if I need them finer/less pulpy). Special tip when making \
smoothies, finely cut and freeze the fruits and \
vegetables (if using spinach-lightly stew soften the \
spinach then freeze until ready for use-and if making \
sorbet, use a small to medium sized food processor) \
that you plan to use that way you can avoid adding so \
much ice if at all-when making your smoothie. \
After about a year, the motor was making a funny noise. \
I called customer service but the warranty expired \
already, so I had to buy another one. FYI: The overall \
quality has gone done in these types of products, so \
they are kind of counting on brand recognition and \
consumer loyalty to maintain sales. Got it in about \
two days.
"""
texts = [text,text_1,text_2,text_3]

#中文版
# review for a standing lamp
text_1 = """
我想为我的卧室找一个漂亮的灯，这款灯还有额外的存储空间，价格也不太高。\
购买后很快就收到了，两天就送到了。但在运输过程中，灯的拉链断了，公司态度\
很好，发来了一条新的。新的拉链也在几天内就到了。这个灯非常容易装配。后来，我\
发现缺少一个部分，所以我联系了他们的客户支持，他们很快就给我寄来了缺失的部件\
！我觉得这是一家非常关心他们的客户和产品的好公司。
"""
# review for an electric toothbrush
text_2 = """
我的牙科卫生师推荐我使用电动牙刷，这就是我购买这款牙刷的原因。目前为止，我发现电池的\
续航时间颇为令人印象深刻。在初次充电并在第一周保持充电器插头插入以调节电池状态之后，我\
已经将充电器拔掉，并在过去的3周里，每天两次刷牙都使用同一次充电。然而，这款牙刷的刷头实\
在太小了。我见过的婴儿牙刷都比这个大。我希望牙刷头能做得更大一些，搭配不同长度的刷毛更好\
地清洁牙齿间缝，因为现有的无法做到这一点。总的来说，如果你能以大约50美元的价格购入这款电动\
牙刷，那它就物超所值。厂家配套的替换刷头价格相当昂贵，但你可以买到价格更为合理的通用款。\
使用这款牙刷让我感觉像每天都去看了牙医一样，我的牙齿感觉洁净如新！
"""
# review for a blender
text_3 = """
他们还在11月把17件套系统以大约$49的优惠价格销售，几乎是五折。但不明原因（轻易就可以归咎为价格欺诈）\
在到了12月第二周，同一套系统的价格一下儿飙升到了$70-$89之间。11件套系统的价格也从之前的优惠价$29上\
升了大概$10。看上去还算公道，但如果你仔细观察底部，会发现刀片锁定的部位相比几年前的版本要略逊一筹，所\
以我打算非常小心翼翼地使用（例如，我会将像豆子、冰块、大米之类的硬质食材先用搅拌机压碎，然后调到我需要\
的份量，再用打发刀片研磨成更细的粉状，制作冰沙时我首选交叉刀片，如果需要更细腻些或者少些浆糊状，我会换成\
平刀）。在制作果昔时，把将要用的水果和蔬菜切片冷冻是个小技巧（如果你打算用菠菜，要先稍微焖炖软，再冷冻，\
制作雪葩时，用一个小到中号的食品加工器就行）这样就不用或者很少加冰块到你的果昔了。大约一年后，电机开始发出\
一些可疑的声音。我联系了客服，但保修期已经过期，所以我只好另购一台。友情提示：这类产品的整体质量都在下滑，\
所以他们更多的是利用品牌知名度和消费者的忠诚度来保持销售。我在两天之后就收到了它。
"""
texts = [text,text_1,text_2,text_3]

for i in range(len(texts)):
    prompt = f"""
    Your task is to generate a short summary of a product \
    review from an ecommerce site. 

    Summarize the review below, delimited by triple \
    backticks in at most 20 words. 

    Review: ```{texts[i]}```
    """
    response = get_completion(prompt)
    print(i, response, "\n")
  
