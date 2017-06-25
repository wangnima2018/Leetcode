# -*- coding: utf-8 -*-
"""
Created on Sat Jun 24 22:43:23 2017

@author: pwu2
"""

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
        
        

# Your Codec object will be instantiated and called as such:
# codec = Codec()
# codec.decode(codec.encode(url))
