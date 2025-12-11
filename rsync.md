Rsync file synchronization commands for mirroring directories, SSH sync, compare checksums, and backup operations with delete options.

---

Make a copy of a directory, deleting files in the destination that don't exist in the origin. Useful for mirroring a directory.  The -p flag keeps the permissions intact.
    rsync -avp --delete source/ destination/
        -a: archive
        -v: verbose
        -p: permissions
        --delete: delete files on the receiving side that do not exist on the sending side.

Find files that would be transferred or deleted with differing content between two sources. Useful for comparing directories to see which one has more data.
You probably want to output this to a log file, and it will take a while with large directories.
    rsync -rvc --delete --dry-run source/ destination/
        -r: recursive
        -v: verbose
        -c: compare checksums, not filesize/modified time
        --delete: delete files on the receiving side that do not exist on the sending side.

Sync over SSH defining a user with sudo rights on the receiving side. Good for remote backups without having to update multiple authorized_keys files on the source.
Running this as a user on the receiving side will set that user as the owner. Running it from root will set the ownership to users that don't exist on the destination.
    rsync --rsync-path 'sudo -u sudouser /usr/bin/rsync' -avP  user@sourcemachine:/source/ /destination/
        -P --partial: keep partially transferred files
        --rsync-path: specify the instructions to execute rsync with a user/location

Bring the destination into sync with the source without discarding data that doesn't exist on the source.
    rsync --archive --verbose --human-readable --update /personal_data/Users/ /personal_data/data/Users/
        --update: skip files that are newer on the receiver
