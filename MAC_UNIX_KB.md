# OSX and Unix Knowledge-base







## Shell Scripting

Create a Shell Script

    $   cd <dir>
    $   touch <filename>.sh
        
Edit file and add code:

    #!/bin/bash
    ls
        
Change file permission and execute:

    $   chmod +x <fileName>
    $   ./<fileName>

### Shell Scripting Basics:

Comment

    # First line can start with a She-Bang (which Shell to use)

She-Bang

    #!/bin/bash
        
Source command (include external shell file and access it's vars and methods)

    source config.sh
        
Variables

    var1 = Hello
    echo $var1
        
$ Variables, Shift, and Operators

    # Script Name
    $0
    
    # cmd line first arg
    $1

    # cmd line second arg
    $2

    # cmd line 3rd arg
    $3

    # Script PID
    $$

    # Last command return code
    $?

    # cmd line any arg present?
    "$#"

    # Cycle to next parameter
    shift

    # Equality operator
    ==

Exit statement

    exit 0
    exit 1

if Statements

    var1=1, var2=2, var3=3
    
    if [ $var1 == $var2 ]
    then
        echo 1
    elif [ $var2 == $var3 ]
    then
        echo 2
    else
        echo 3
    fi        
        
for loop
        
    for((i=0; i< 10; i++))
    do
        echo "$i"
    done

while loop

    i=10
    while [ $i -ge 0 ]
    do
        echo you gave me $i
        ((i--))
    done
        
Functions
        
    function Welcome () {
        echo Welcome $1 and $2
    }
    
    Welcome Jatin Sandeep
        
Case statements

    var1=2
    
    case $var1 in
        "2")
          echo 2
          ;;
        "5")
          echo 5
          ;;
        "10")
          echo 10
          ;;
    esac
        
## Shell Snippets
        
Iterate Through Command line Args

    if[ "$#" == "0" ]
    then
        echo pass at least 1 parameter
        exit 1
    fi

    while(( $# ))
    do
        echo you gave me $1
        shift
    done

Exit when any command fails
    
    set -e
    

Exit when last command fails

    exit_on_error() {
        exit_code=$1
        last_command=${@:2}
        if [ $exit_code -ne 0 ]; then
            >&2 echo "\"${last_command}\" command failed with exit code ${exit_code}."
            exit $exit_code
        fi
    }
    
    # enable !! command completion
    set -o history -o histexpand
    
    ls --fake-option
    exit_on_error $? !!
    
    
Catch Exit Code and return custom error code

    mvn clean test
    rc=$?
    
    if [[ $rc -ne 0 ]] ; then
      echo 'could not perform tests'; exit $rc
    fi

keep track of the last executed command

    trap 'last_command=$current_command; current_command=$BASH_COMMAND' DEBUG

echo an error message before exiting
    
    trap 'echo "\"${last_command}\" command filed with exit code $?."' EXIT
