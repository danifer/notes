# Does a string contain a string?
    if [[ "$string1" == *"$string2"* ]]; then
        echo "The string contains the substring."
    else
        echo "The string does not contain the substring."
    fi

# Is a value set and not empty?
    if [ -z "$empty_variable" ]; then
        echo "Empty variable is not defined."
    fi

# Make grep return return a success or failure status code (0/1). Not a boolean, but similar.
    COMMAND | grep "$string" > /dev/null

    #Used in a conditional as:
        if COMMAND | grep "$string" > /dev/null; then
             echo "$string found."
        fi
