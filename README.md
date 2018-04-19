Bash script for building epub/mobi ebook version of Domagoj Kurmaic's excellent [Mother of Learning](https://www.fictionpress.com/s/2961893/1/Mother-of-Learning)


## Instructions ##

1. Clone/Fork this project to your desired location.

1. Install pandoc and ImageMagick using your preferred package manager (apt-get, yum, dnf, etc).  For example:

        sudo dnf install pandoc ImageMagick

1. Grab [kindlegen](https://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000765211) from Amazon.  Extract and make sure kindlegen is in your $PATH.  For example:

        tar -xzf kindlegen_linux_2.6_i386_v2_9.tar.gz
        mv kindlegen_linux_2.6_i386_v2_9/kindlegen ~/usr/bin/

1. Clone https://github.com/kevinhendricks/KindleUnpack in directory mol-ebook exists in.

        cd .. && git clone https://github.com/kevinhendricks/KindleUnpack.git && cd mol-ebook


1. Update the numchapters file to contain the latest chapter number.

        echo 83 > numchapters

## Run ##

Run with `./build.sh`.  The script will download the chapters, clean them up, grab the cover, and craft the ebook/mobi.


## If you get errors ##

* You can safely ignore any `rm` warnings about files not existing. This could be repressed with `rm -f`, but you really don't want a script forcing removing stuff.  Can also break the script if you have an alias to `-i` when forcing.  We could also redirect warning output with `2> /dev/null` which is much less dangerous - but then rm could fail silently for some other reason (like permissions).  So just ignore any rm that fails because it can't find the file(s).

* If KindleUnpack doesn't seem to be working, it may have been updated in a way that breaks compatibility.  Go to the KindleUnpack repo and use the given commit - which is known to work at the current time.


        git checkout 102e2e732b680f8edfcfff56467876f4bcee836f

