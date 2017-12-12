---
layout: post
title: "Tiju George, Inverted Index Structure"
date: 2017-12-12
---

##Inverted Index Structure learning python code

```python
import re
import random
import pandas as pd
class MakeDictionary:
	def __init__(self):
		self.newDicti = {}  #newDicti = {doc1: 'sentence1'; doc2: 'sentence2'}
		self.dicti = {}

	def clearingString(self, *argv):
		pageNo = iter(range(1,1000000000))
		for arg in argv:
			arg = arg.lower()
			newarg = re.sub('[^a-zA-Z0-9 \n]', '', arg)
			if not newarg in self.newDicti:
				self.newDicti[next(pageNo)] = newarg 

		for docID, sentence in self.newDicti.items():
			for word in sentence.split():
				if not word in self.dicti:
					self.dicti[word] = [1, [docID]]
				else:
					self.dicti[word] = [self.dicti[word][0] + 1 , self.dicti[word][1] + [docID]]

	def printResult(self):
		return self.dicti

Doc1 = 'new home sales top forecasts' 
Doc2 = 'home sales rise in july' 
Doc3 = 'increase in home sales in july' 
Doc4 = 'july new home sales rise'

md = MakeDictionary()
md.clearingString(Doc1, Doc2, Doc3, Doc4)
df = pd.DataFrame([[key,value[0], value[1]] for key,value in md.printResult().items()],
     columns=["Word","Frequency", "Found_in_pages"])   #value[0] has frequency and value[1] has pages
df.index+=1
df.index.name = 'Index'

print(df)

Result is 

![Screenshot](https://github.com/tijugeorge/tijugeorge.github.io/blob/master/img/Capture.JPG)

