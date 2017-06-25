# -*- coding: utf-8 -*-
"""
Created on Sat Jun 24 22:43:23 2017

@author: pwu2
"""
<h1>题意</h1>
<p>把一个长url转为一个短url，同时要求可以把短url解码回长的url<p> 

<h1>题解</h1>
<p>encode过程：把所有字母和数字放在一个string集合里，用生成的随机数，抽取6次char，然后生成一个短string。
如果string不在之前生成过的string set里，那么就使用这个string. 使用了两个字典：hashToUrl(记录短str应该被还原为哪个长str), urlToHash(如果有url，被第二次input，那么直接返回短str)<p> 

<p>decode过程，使用hashToUrl字典进行查找，并返回<p>

<h1>需要注意的</h1>
<p>建立urlbase，并正确使用<p>


```python
class Codec:

    
    def __init__(self):
        self.hashToUrl = {}
        self.urlToHash = {}
        self.urlBase = "http://tinyurl.com/"
        self.charSource = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"

    def encode(self, longUrl):
        """Encodes a URL to a shortened URL.
        
        :type longUrl: str
        :rtype: str
        """

        if longUrl in self.urlToHash:
            return self.urlBaes+self.urlToHash[longUrl]
        
        hashstr = ""
        while True:
            for i in range(6):
                hashstr += self.charSource[random.randint(0,len(self.charSource)-1)]
            if hashstr not in self.hashToUrl:
                break
        self.hashToUrl[hashstr] = longUrl
        self.urlToHash[longUrl] = hashstr
        return self.urlBase+hashstr
                
        

    def decode(self, shortUrl):
        """Decodes a shortened URL to its original URL.
        
        :type shortUrl: str
        :rtype: str
        """
        return self.hashToUrl.get(shortUrl[len(self.urlBase):])
```
