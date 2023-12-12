Shortcuts
    Auto-complete file and folder names
        Tab

    Go to the beginning of the line you're currently typing on
        Ctrl + A

    Go to the end of the line you're currently typing on
        Ctrl + E

    Clear the line before the cursor
        Ctrl + U

    Clear the line after the cursor
        Ctrl + K

    Delete the word before the cursor
        Ctrl + W

    Swap the last two characters before the cursor
        Ctrl + T

    Swap the last two words before the cursor
        Esc + T

    Clear the screen
        Ctrl + L

    Kill whatever you're running
        Ctrl + C

    Exit the current shell
        Ctrl + D

    Move cursor one word forward
        Option + →

    Move cursor one word backward
        Option + ←

    Move cursor one character forward
        Ctrl + F

    Move cursor one character backward
        Ctrl + B

    Paste whatever was cut by the last command
        Ctrl + Y

    Puts whatever you're running into a suspended background process
        Ctrl + Z

    Undo the last command
        Ctrl + _

    Copy plain text
        Option + Shift + Cmd + C

    Paste the selection
        Shift + Cmd + V

    End a shell session
        exit

Basics
    Top level directory
        / (Forward Slash)

    Current directory
        . (Single Period)

    Parent directory
        .. (Double Period)

    Home directory
        ~ (Tilde)

    Run command with the security privileges of the super user
        sudo [command]

    Opens the Terminal editor
        nano [file]

    Opens a file
        open [file]

    Get help about a command
        [command] -h

    Show the help manual of the command
        man [command]

    Home directory
        cd

Change Directory
    Change directory, e.g. cd Documents
        cd [folder]

    Home directory
        cd ~

    Root of the drive
        cd/

    Previous directory or folder you last browsed
        cd -

    Show your working directory
        pwd

    Move up to the parent directory
        cd..

    Move up two levels
        cd../..

List Directory Contents
    Display the name of files and subdirectories in the directory
        ls

    Force multi-column output of the listing
        ls -C

    List all entries including those with .(period) and ..(double period)
        ls -a

    Output the list of files in one entry per line format
        ls -1

    link
        ls -F

    Sort files or entries by size
        ls -S

    List in a long format. Includes file mode, owner and group name, date and time file was modified, pathname, and more
        ls -l

    List of the file system from root with symbolic links
        ls -l /

    List the files sorted by time modified (most recent first)
        ls -lt

    Long listing with human readable file sizes in KB, MB, or GB
        ls -lh

    List the file names with size, owner, and flags
        ls -lo

    List detailed directory contents, including hidden files
        ls -la

    List usage for each subdirectory and its contents
        du

File Size and Disk Space
    Human readable output of all files in a directory
        du -sh [folder]

    Display an entry for each specified file
        du -s

    List files and folders, totaling the size including the subfolders. Replace sk* with sm* to list directories in MB
        du -sk* | sort -nr

    Calculate your system's free disk space
        df -h

    Calculate free disk space in powers of 1,000 (as opposed to 1,024)
        df -H

File and Directory Management
    Create new folder named <dir>
        mkdir <dir>

    Create nested folders
        mkdir -p <dir>/<dir>

    Create several folders at once
        mkdir <dir1> <dir2> <dir3>

    Create a folder with a space in the filename
        mkdir "<dir>"

    Delete a folder (only works on empty folders)
        rmdir <dir>

    Delete a folder and its contents
        rm -R <dir>

    Create a new file without any extension
        touch <file>

    Copy a file to the folder
        cp <file> <dir>

    Copy a file to the current folder
        cp <file> <newfile>

    Copy a file to the folder and rename the copied file
        cp <file>~/<dir>/<newfile>

    Copy a folder to a new folder with spaces in the filename
        cp -R <dir> <"new dir">

    Prompts you before copying a file with a warning overwrite message
        cp -i <file><dir>

    Copy multiple files to a folder
        cp <file1> <file2> <file3>/Users/<dir>

    Copy the contents of a folder to new folder. In here "-V" print a line of status for every file copied
        ditto -V [folder path][new folder]

    Delete a file (This deletes the file permanently; use with caution.)
        rm <file>

    Delete a file only when you give confirmation
        rm -i <file>

    Force removal without confirmation
        rm -f <file>

    Delete multiple files without any confirmation
        rm <file1> <file2> <file3>

    Move/rename
        mv <file> <newfilename>

    Move a file to the folder, possibly by overwriting an existing file
        mv <file> <dir>

    Optional -i flag to warn you before overwriting the file
        mv -i <file> <dir>

    Move all PNG files from current folder to a different folder
        mv *.png ~/<dir>

Command History
    Search through previously used commands
        Ctrl + R

    Shows the previous commands you've typed. Add a number to limit to the last n items
        history n

    Execute the last command typed that starts with a value
        ![value]

    Execute the last command typed
        !!

Permissions
    Display the default permission for a home directory
        ls -ld

    Display the read, write, and access permission of a particular folder
        ls -ld/<dir>

    Change the permission of a file to 755
        chmod 755 <file>

    Change the permission of a folder (and its contents) to 600
        chmod -R 600 <dir>

    Change the ownership of a file to user and group. Add -R to include folder contents
        chown <user>:<group> <file>

    Processes
    Output currently running processes. Here, a shows processes from all users and x shows processes that are not connected with the Terminal
        ps -ax

    Shows all the processes with %cpu, %mem, page in, PID, and command
        ps -aux

    Display live information about currently running processes
        top

    Display processes sorted by CPU usage, updating every 5 seconds
        top -ocpu -s 5

    Sort top by memory usage
        top -o rsize

    Quit process with ID <PID>. You'll see PID as a column in the Activity Monitor
        kill PID

    Find a process by name or PID
        ps -ax | grep <appname>

Network
    Ping host and display status
        ping <host>

    Output whois info for a domain
        whois <domain>

    Download file via HTTP, HTTPS, or FTP
        curl -O <url/to/file>

    Establish SSH connection to <host> with user <username>
        ssh <username>@<host>

    Copy <file> to a remote <host>
        scp <file><user>@<host>:/remote/path

    View a list of all devices on your local network. It will show you the IP and MAC address of all the devices
        arp -a

    View your device IP and MAC address
        ifconfig en0

    Identify the path and the hops traversed by the packets from your device to the destination address
        traceroute [hostname]

Homebrew
    Check brew for potential problems
        brew doctor

    List of useful homebrew formula and cask commands
        brew help

    Install a formula or cask
        brew install <formula>|<cask>

    Uninstall a formula or cask
        brew uninstall <formula>|cask>

    List only installed formulas
        brew list --formula

    List only installed cask
        brew list --cask

    List all the dependencies of a formula or cask
        brew deps <formula>|<cask>

    Search formula or cask through regex
        brew search text|/regex/

    Upgrade the formula or cask
        brew upgrade <formula>|<cask>

    Search for outdated formula or cask
        brew outdated <formula>|<cask>

    Search for outdated formula
        brew outdated --formula

    Search for outdated cask
        brew outdated --cask

    Pin a formula from getting upgraded
        brew pin [installed_formula]

    Unpin to upgrade a package
        brew unpin [installed_formula]

    Remove stale lock files and outdated packages for all formula and casks.
        brew cleanup

Environment Variable or Path
    Display a list of currently set environment variables. Also tells you which shell you're using
        printenv

    Tells the terminal to print something and show it to you
        $echo

    Check the value of the PATH variable which storea a list of directories with executable files
        echo $PATH

    Export the path directory to a text file
        echo $PATH >path.txt

    Execute a program via terminal only in your current session. If you use a program regularly, add the path to shell configuration file.
        export PATH=$PATH:absolute/path to/program/

    Search
    Find all files named <file> inside <dir>. Use wildcards (*) to search for parts of filenames
        find <dir> -name <"file">

    Output all occurrences of <text> inside <file> (add -i for case insensitivity)
        grep "<text>" <file>

    Search for all files containing <text> inside <dir>
        grep -rl "<text>" <dir>

Output
    Output the content of <file>
        cat <file>

    Output the contents of <file> using the less command that supports pagination and more
        less <file>

    Output the first 10 lines of <file>
        head <file>

    Appends the output of <cmd> to <file>
        <cmd> > > <file>

    Direct the output of <cmd> into <file>
        <cmd> > <file>

    Direct the output of <cmd1> to <cmd2>
        <cmd1> | <cmd2>
