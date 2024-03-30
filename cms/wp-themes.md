## WordPress Themes

`Definition` - A WordPress theme is a collection of templates and stylesheets used to define the appearance and display of a WordPress-powered website

### Themes Basic Info

- `Parts of a wordpress theme`
  - Stylesheet (style.css): This file controls the overall look and feel of your site. It contains CSS
  - Template Files: These PHP files control the structure and layout of different parts of your site (some common ones) (header.php, footer.php, functions.php .etc)
  - Images and Assets: Themes often include images, icons, JavaScript files, and other assets used for styling and functionality.

- `Finding and Installing a Theme` 
  - WordPress Theme Directory: You can find thousands of free themes in the official WordPress Theme Directory.
  - Third-party Marketplaces: There are also many third-party marketplaces where you can find both free and premium themes. Popular ones include ThemeForest, Elegant Themes, and StudioPress.
  - Installing a Theme: Once you've found a theme you like, you can install it directly from your WordPress dashboard. Go to "Appearance" -> "Themes" -> "Add New", then search for the theme by name or upload the theme's ZIP file directly to your Wordpress folder in "wp-content/themes".

## Custom Theme Dev

> When you are developing a custom theme it is best to first create a static-responsive design with just html-css-js and than convert it into a wordpress theme.

- 1 - Set Up Your Development Environment: (xampp, ..etc you already have these from previous cheatsheets)
- 2 - Create a New Theme Directory: Navigate to the "wp-content/themes" directory in your WordPress installation and create a new folder for your custom theme. Choose a name for your theme (e.g., "custom-theme").
- 3 - Create a Stylesheet (style.css): (Inside your theme folder, create a file named style.css. This file is essential and must contain the following comment block at the top:)
    ```css
    /*
    Theme Name: Custom Theme
    Author: Your Name
    Description: A custom WordPress theme.
    Version: 1.0
    */
    ```
- 4 - Create a Functions File (functions.php): In the same theme folder, create a file named functions.php. This file will contain any custom functions or PHP code needed for your theme.
- 5 - Create Template Files: WordPress uses template files to determine how different types of content are displayed. Here are some essential template files you might want to include:
    - index.php: The main template file.
    - header.php: Contains the header section.
    - footer.php: Contains the footer section.
    - single.php: Displays single blog posts.
    - page.php: Displays single pages.
    - archive.php: Displays archive pages.
    - search.php: Displays search results.
  You can also create custom template files for specific purposes, such as home.php, category.php, tag.php, etc., based on your site's needs.
- 6 - Add Basic HTML Structure: In each template file, add the necessary HTML structure along with WordPress template tags to dynamically display content. Template tags allow you to output data from the WordPress database, such as post titles, content, and metadata.
    ```php
    // For example, to display the post title, you would use:
    <h2><?php the_title(); ?></h2>
    ```
