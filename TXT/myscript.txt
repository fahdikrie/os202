#!/bin/bash

# quick os rsync script!
# author: fahdikrie
# how to use:
#   0. IMPORTANT! it is required to have an open tunnel to badak in order for this script to run
#   1. change filename & format to <filename>.sh
#   2. run the scripts using the command 'bash <filename>.sh'

# greetings
echo "ayo slim! have any files u want to sync?"
echo "say 'yessir' if u'd like to continue"

# read input as conditional flag
read -p "(yessir/naw)? : " flag
if ! [ $flag == "yessir" ]; then
    echo "aye, we'll take that as a no den"
    echo "aight! i'll catch u around cuh"
    exit 1
fi

echo
echo "generating commands..."
echo

# asks which folder do the user want to sync
# textbooks/slides/docs
echo "which files do u want to sync den?"
read -p "(textbooks/slides/docs)? : " files

# conditional blocks
if [ $files == "textbooks" ]; then
    rsync -auv --delete -e 'ssh -p 6023' fahdii.ajmalal91@localhost:/extra/Silberschatz/ ~/Data/academics/Ilmu Komputer/Semester 3/Sistem Operasi/textbook
elif [ $files == "slides" ]; then
    rsync -auv --delete -e 'ssh -p 6023' fahdii.ajmalal91@localhost:/extra/Slides/ ~/Data/academics/Ilmu Komputer/Semester 3/Sistem Operasi/slides
elif [ $files == "docs" ]; then
    rsync -auv --delete -e 'ssh -p 6023' fahdii.ajmalal91@localhost:/extra/Docs/ ~/Data/academics/Ilmu Komputer/Semester 3/Sistem Operasi/docs
else
    echo "aye slim our bad we don't have $files yet"
    exit 1
fi

echo
echo "'$files' is all wrapped up cuh y'all good to go now"
echo "see ya!"