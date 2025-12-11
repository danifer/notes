Subversion (SVN) version control commands for switch repository, export, find ignored files, and remove version control.

---

- Change location of the repository using the "switch" command, not "relocate" which is unavailable in earlier versions of Subversion
    svn switch --relocate FROM TO
        svn switch --relocate https://oldserver.example.com/svn/myproject/trunk svn+altssh://newserver.example.com/home/svn/myproject/trunk

- Export a repository to remove it from version control
    svn export [source] [destination]
        - note: will not export untracked files, so you need to move things that aren't under version control manually (stored data files, .pdfs, etc.).

- Recursively find all ignored files
    svn propget -R svn:ignore
    svn status --no-ignore | grep "I  "
        - http://stackoverflow.com/questions/2579483/get-recursive-list-of-svnignored-files

- Remove version control from a project without the "svn export" command
    find . -type d -name .svn -exec rm -rf {} \;
