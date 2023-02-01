Full TTY Shell

```bash
SHELL=/bin/bash script -q /dev/null
      ctrl+z
      
      echo $TERM
      stty -a
      stty raw -echo && fg
      
      reset
      xterm-256color
      stty rows ### columns ###
      export TERM=xterm
```

