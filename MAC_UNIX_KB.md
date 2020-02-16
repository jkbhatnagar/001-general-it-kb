# OSX and Unix Knowledge-base

## Hide/Show Hidden Files/Folders
    COMMAND + SHIFT + .

## Set up BASH Profile 

    // if file does not exist, create one:
    touch ~/.bash_profile
    
    // Open in Textedit
    open ~/.bash_profile
    
    //Set Env Variable
    export env_varname=somevalue
    
    //Add values to Path Variable
    export PATH=$PATH:/usr/local/bin/carthage
    
    // Save and close the file
    // Use latest bash profile without restarting Terminal window.
    source ~/.bash_profile
    
    // Check Sys Var
    echo $env_varname
    
    // Check Path Var
    echo $PATH

## Set up SSH Private/Public Key Pair (generally used for secure communication between your Mac and Git provider)

    cd ~
    
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    
    // Enter location and passphrase (your should remember and securely store the passphrase)
    // default location is ~/.ssh
    // default name is id_rsa (private key) and id_rsa.pub (public key)
    // if you want different SSH key for different application, set a different name like app_id_rsa
    
    //Copy your key to clipboard and paste if as required in your application
    pbcopy < ~/.ssh/id_rsa.pub
    
    // Add private key to SSH Agent
    ssh-add -K ~/.ssh/id_rsa

## Set-up Mac Homebrew

    // Homebrew is Dev software/package manager for Mac.
    
    // Install XCode Command line Tools
    xcode-select --install
    
    // Install Homebrew
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    
    brew update
    
    brew doctor
    
    //To list all apps installed by Homebrew    
    brew list
    
    //To remove an installed application    
    brew remove packagename 
    
    //To see what packages are out of date but not to upgrade them    
    brew outdated
    
    //To see what upgrade packages all or singular    
    brew update
    brew update packagename    
    brew install wget
    
    // Uninstall (rarely required)
    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"
    
    // install graphical apps
    brew cask search appname
    brew cask search appname
    brew cask uninstall appname
    
    //  install UNIX and open-source utilities
    brew search appname
    brew search appname
    brew uninstall appname
    
    

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
