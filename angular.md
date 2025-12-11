Angular CLI installation, project setup, npm commands, and ng serve configuration for development.

Install Node on Debian:
    apt-get install nodejs
        Appears to come bundled with npm

Install the Angular CLI
    (from the project directory)
        npm install @angular/cli

For convenience, alias the Angular CLI command "ng" by making a .bashrc in your project root.
    .bashrc
        alias ng="node_modules/@angular/cli/bin/ng"

Create a project
    npm new app
        - If you get errors, try "npm cache clean --force"

Run the serve command.
    ng serve
        - runs the server and compiles files on the fly. Make sure you have enough system memory.
     ng serve --host 192.168.1.216
        - serves to a network address