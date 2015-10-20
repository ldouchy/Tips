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

  Redirect stdin:

    cmd > file

  Redirect error:

    cmd 2> file

  Redirect stdin and error:

    cmd > file 2>&1

Sed:

  Find and replace inline:

    sed -i 's/FIND/REPLACE/g' file

    /!\ In case of variable usage:
    sed -i "s/FIND/${REPLACE}/" file
