Ubuntu cli tool to send key and mouse events to xserver windows to implement macros

https://www.semicomplete.com/projects/xdotool/
https://manpages.ubuntu.com/manpages/trusty/man1/xdotool.1.html

xdotool search --class google-chrome windowactivate key ctrl+n type 'chrome://bookmarks/?id=699\n'


```
pids=$(xdotool search --class "gvim")
for pid in $pids; do
    name=$(xdotool getwindowname $pid)
    if [[ $name == *"TODO"* ]]; then
        #Do what you want, $pid is your sought for PID,
        #matching both class gvim and TODO in title
    fi
done
```

[[MOC - Software Tools]]

#reference/software/ubuntu
