#分类类prompt\
prompt="""\
          #写出分类的标准\
          ```{text}```\
"""\


#示例\

#示例文本\
lamp_review = """\
Needed a nice lamp for my bedroom, and this one had \
additional storage and not too high of a price point. \
Got it fast.  The string to our lamp broke during the \
transit and the company happily sent over a new one. \
Came within a few days as well. It was easy to put \
together.  I had a missing part, so I contacted their \
support and they very quickly got me the missing piece! \
Lumina seems to me to be a great company that cares \
about their customers and products!!
"""\
# 中文\
lamp_review_zh = """\
我需要一盏漂亮的卧室灯，这款灯具有额外的储物功能，价格也不算太高。\
我很快就收到了它。在运输过程中，我们的灯绳断了，但是公司很乐意寄送了一个新的。\
几天后就收到了。这款灯很容易组装。我发现少了一个零件，于是联系了他们的客服，他们很快就给我寄来了缺失的零件！\
在我看来，Lumina 是一家非常关心顾客和产品的优秀公司！
"""\

#示例prompt

#输出单个类型
prompt = f"""
What is the sentiment of the following product review, 
which is delimited with triple backticks?\
Review text: ```{lamp_review}```
"""\
response = get_completion(prompt)\
print(response)\
# 中文
prompt = f"""
以下用三个反引号分隔的产品评论的情感是什么？\
评论文本: ```{lamp_review_zh}```
"""\
response = get_completion(prompt)\
print(response)\

#输出类型列表
prompt = f"""\
Identify a list of emotions that the writer of the \
following review is expressing. Include no more than \
five items in the list. Format your answer as a list of \
lower-case words separated by commas.
Review text: ```{lamp_review}```
"""\
response = get_completion(prompt)\
print(response)\
# 中文
prompt = f"""\
识别以下评论的作者表达的情感。包含不超过五个项目。将答案格式化为以逗号分隔的单词列表。
评论文本: ```{lamp_review_zh}```
"""\
response = get_completion(prompt)\
print(response)\
