#代码生成类prompt\
prompt="""\
		#一个目标明确的任务\
		#任务的具体要求（任务所需的环境、skills、参数等各种细微要求）\
		#输出格式\
"""\
#示例\
prompt="""\
请使用Python语言写一段函数递归的代码，要求时间复杂度不能超过10^3,空间复杂度不能超过10^2，\
每次递归的结果都要输出并且输出结果要用列表整理。
""""\
response = get_completion(prompt)\
print(response)\

