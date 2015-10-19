# TipsLinux
Tips and Tricks Linux



Awk:

  Extracting characters of a string:
    substr(s, i [, n]) Return the at most n-character substring of s starting at i.  If n is omitted, use the rest of s.

    Example:
    $ echo "test" | awk '{print substr ($0,1,2)}'
    te
    

Bash:

  Extracting characters of a string:
    ${string:position:length}
  
    Example:
    $ STRING=test ; echo ${STRING:0:2}
    te
