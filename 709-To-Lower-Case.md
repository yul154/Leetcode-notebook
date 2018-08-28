# 709. To Lower Case

> Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.


class Solution:
    def toLowerCase(self, str):
        """
        :type str: str
        :rtype: str
        """
        """str=str.lower()
        return str"""
        rst=""
        for s in str:
            if ord(s)>=ord('A') and ord(s)<ord('a'):
                rst+=chr(ord(s)+32)
            else:
                rst+=s
        return rst
 `
