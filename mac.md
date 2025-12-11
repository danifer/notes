macOS specific commands for PHP version switching, alerts, rename files to lowercase, disk utilities, and partition management.

Switch PHP versions
    brew link php@7.4
    brew link php@8.0

Display an alert message from the terminal
    osascript -e 'display alert "Reminder" message "Did the cronjob run?"'

Find files with image metadata
    mdfind image -onlyin .

Rename files to all lowercase
    for f in *; do mv "$f" "$f.tmp"; mv "$f.tmp" "`echo $f | tr "[:upper:]" "[:lower:]"`"; done

Disk information
    diskutil listFilesystems
    diskutil list

Partition a drive (https://tobywf.com/2017/01/diskutil/)
    sudo diskutil partitionDisk disk3 1 JHFS+ one R

Install ext4 filesystem. Requires e2fsprogs (https://apple.stackexchange.com/questions/171506/formatting-usb-disk-as-ext3-on-mac)
    brew install e2fsprogs
    sudo $(brew --prefix e2fsprogs)/sbin/mkfs.ext4 /dev/diskXsX
