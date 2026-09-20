#推理类prompt\
prompt="""\
          #具体的任务\
          #已知的条件\
          #推理要求（逐步分析，得出答案）\
          #输出格式\
          ```{text} ```\
"""\
#示例\
prompt = f"""\
Determine if the student's solution is correct or not.\
Question:\
I'm building a solar power installation and I need
 help working out the financials. \
- Land costs $100 / square foot
- I can buy solar panels for $250 / square foot\
- I negotiated a contract for maintenance that will cost \ 
me a flat $100k per year, and an additional $10 / square 
foot\
What is the total cost for the first year of operations 
as a function of the number of square feet.\
Student's Solution:\
Let x be the size of the installation in square feet.\
Costs:\
1. Land cost: 100x\
2. Solar panel cost: 250x\
3. Maintenance cost: 100,000 + 100x\
Total cost: 100x + 250x + 100,000 + 100x = 450x + 100,000
"""\
response = get_completion(prompt)\
print(response)\
#中文\
prompt = f"""
判断学生的解决方案是否正确。\
问题:\
我正在建造一个太阳能发电站，需要帮助计算财务。\
    土地费用为 100美元/平方英尺\
    我可以以 250美元/平方英尺的价格购买太阳能电池板\
    我已经谈判好了维护合同，每年需要支付固定的10万美元，并额外支付每平方英尺10美元\
    作为平方英尺数的函数，首年运营的总费用是多少。\
学生的解决方案：\
设x为发电站的大小，单位为平方英尺。\
费用：\
    土地费用：100x\
    太阳能电池板费用：250x\
    维护费用：100,000美元+100x\
    总费用：100x+250x+100,000美元+100x=450x+100,000美元
"""\
response = get_completion(prompt)\
print(response)\

