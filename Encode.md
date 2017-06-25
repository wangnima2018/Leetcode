# -*- coding: utf-8 -*-
"""
Created on Sat Jun 24 22:43:23 2017

@author: pwu2
"""
<h1>题意</h1>
<p>把一个长url转为一个短url，同时要求可以把短url解码回长的url<p> 

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
        
        
