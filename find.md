Suppress error messages
    find . -name example 2>/dev/null

Delete files by matching name
    find . -wholename '*/www.website.com/*.html' -delete

Plain old find-by-name
    find . -name "*file*"

Find and delete files older than X days
    find /directory/location -name '*' -type f -daystart -mtime +1 -exec rm -f {} \;

Find and replace across multiple files
    Original for Linux
        find . -name "*.php" -print | xargs sed -i 's/foo/bar/g'
    Alternate for Mac
        find . -name "*.php" -exec sed -i '' 's/find/replace/g' {} \;

Find files by permission
    find . -type f -perm 0777

Find, tar, gzip with name based on original filename, then delete files. Useful for compressing log files.
    find . -name "*.csv" -type f -exec tar -czf {}.tar.gz {} --remove-files \;

Find and delete files older than 10 days in the /tmp directory
    find /tmp -ctime +10 -exec rm -rf {} +

Find the latest file (recursively) in the current directory. This will take a while, and you probably want to output to a log file.
    find $PWD -type f -printf "%T@ %p\n" | sort -n | cut -d' ' -f 2- | tail -n 1

Find files between date range
    find $PWD -type f -newermt "2024-04-01" ! -newermt "2024-06-01"

