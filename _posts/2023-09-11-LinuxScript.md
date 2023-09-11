---
toc: False
comments: False
layout: post
title: Linux Script
description: check if your things are updated and working
courses: {'csp': {'week': 3}}
categories: ['C3.8']
type: hacks
---

#!/bin/bash

# Function to check if a program is installed and at least a minimum version
check_program_version() {
    local program_name="$1"
    local min_version="$2"
    
    # Check if the program is installed
    if ! command -v "$program_name" > /dev/null 2>&1; then
        echo "$program_name is not installed."
        return 1
    fi
    
    # Get the program's version
    local version
    version="$("$program_name" --version | awk '{print $NF}')"
    
    # Compare the version to the minimum required version
    if [[ "$version" < "$min_version" ]]; then
        echo "Error: $program_name version $min_version or higher is required, but you have $version."
        return 1
    fi
}

# Check Python and its version
check_program_version "python" "3.6"

# Check Jupyter and its version
check_program_version "jupyter" "1.0"

# Check Ruby and its version
check_program_version "ruby" "2.5"

# Check Jekyll and its version
check_program_version "jekyll" "4.0"

# If all checks passed, display a success message
echo "All required programs and versions are installed."
