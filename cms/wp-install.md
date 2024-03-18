## Wordpress Installation 

There are three main ways to install wordpress locally to your machine:
- 1 - Local Worpress - this is an app developed for beginner users
- 2 - Varying Vagrant Vagrants - this is the same thing as above but devloped for seasoned developers
- 3 - XAMPP/MAMP/ etc - this is your normal local server environment


What is xampp?
- XAMPP is an acronym that stands for cross platform, Apache, MySQL, PHP, and Perl. It is a software that includes all the necessary tools for creating a local server for WordPress

### Algorithm for Installation

- 1 - Install a Local Server Environment: (XAMPP, MAMP, .. etc.)
- 2 - Download WordPress: (official website: https://wordpress.org/download/)
- 3 - Set Up the Database:
  - Open your local server environment control panel.
  - Create a new MySQL database for your WordPress installation. Note down the database name, username, and password.
- 4 - Install WordPress:
  - Extract the WordPress zip file you downloaded earlier.
  - Move the extracted WordPress folder to your local server's web directory. For XAMPP, it's usually `htdocs`. For MAMP, it's typically `htdocs` or `www`.
  - Rename the WordPress folder if desired (e.g., myproject).
  - Navigate to `http://localhost/yourfoldername` in your web browser.
  - Follow the WordPress installation wizard:
    - Select your language and click "Continue."
    - Enter the database details (database name, username, password, and host).
    - Click "Submit" and then "Run the installation."
    - Provide site information (site title, username, password, email).
    - Click "Install WordPress."
- 5 - Access Your Local WordPress Site: `http://localhost/yourfoldername` in browser.
- 6 - Customize Your Development Environment (code editors, git, ...etc normal development tools)
- 7 - Start Developing: (Themes, plugins, modify code, test features ... etc.)
