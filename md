#!/bin/bash
# Function to handle errors
handle_error() {
    local exit_code=$1
    local message=$2
    echo "Error: $message"
    exit $exit_code
}

# Usage
#if [ $# -lt 1 ]; then
    #handle_error 1 "Usage: $0 <>"
#fi

# Check if stdin is empty
#if [ -t 0 ]; then
    #echo "Error: No input provided on stdin" >&2
    #exit 1
#fi

pandoc --pdf-engine=pdfroff --toc-depth=1 "$1" -o "$(basename $1 .md).pdf"
zathura "$(basename $1 .md).pdf"
