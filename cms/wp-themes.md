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

## Custom Theme

> When you are developing a custom theme it is best to first create a static-responsive design with just html-css-js and than convert it into a wordpress theme.

Here is a step by step way to convert your static site to a wordpress theme:
- 1 - Set Up a Local WordPress Environment: Install WordPress on your local machine using software like XAMPP, MAMP, or a local development tool like Local by Flywheel. This allows you to work on your theme without affecting your live site.
- 2 - Create a New Theme Directory: Inside the `wp-content/themes` directory of your WordPress installation, create a new folder for your theme. Choose a unique name for your theme directory.
- 3 - Create Necessary Files and Directories: Inside your theme directory, create the necessary files and directories for a WordPress theme. At a minimum, you'll need `style.css`, `index.php`, `header.php`, `footer.php`, and `functions.php`.
    ```css
    /*
    Theme Name: Custom Theme
    Author: Your Name
    Description: A custom WordPress theme.
    Version: 1.0
    */
    ```
- 4 - Copy Static Site Content: Copy the HTML, CSS, JavaScript, and any other assets from your static site into their respective files within your WordPress theme directory. Adjust paths and links as needed to work within the WordPress environment.
- 5 - Break HTML into WordPress Template Parts: WordPress themes typically use template parts to separate different sections of a page. Break your HTML markup into template parts such as `header.php`, `footer.php`, `sidebar.php`, etc., to follow WordPress theme structure conventions.
- 6 - Integrate WordPress Template Tags: Replace static content with WordPress template tags and functions to dynamically generate content. For example, `use get_header()`, `get_footer()`, `wp_head()`, `wp_footer()`, `the_title()`, `the_content()`, etc.
- 7 - Convert CSS to WordPress Stylesheet: Replace any static URLs in your CSS with WordPress functions like `get_stylesheet_directory_uri()` or `get_template_directory_uri()` to ensure proper linking to assets.
- 8 - Enqueue Styles and Scripts: Add CSS and JavaScript files to your theme using WordPress's `wp_enqueue_style()` and `wp_enqueue_script()` functions. This ensures proper loading and handling of styles and scripts.
- 9 - Implement WordPress Features: If your static site includes features like navigation menus, widgets, custom post types, or custom fields, implement them using WordPress APIs and features.
- 10 - Test Your Theme: Test your theme thoroughly to ensure everything works as expected. Check different pages, templates, and functionalities to ensure they function correctly within the WordPress environment.
- 11 - Optimize for Performance and SEO: Ensure your theme follows best practices for performance and SEO. Optimize images, minify CSS and JavaScript, use caching plugins, and implement SEO-friendly practices like schema markup and meta tags.
- 12 - Make Responsive: Ensure your theme is responsive and looks good on various devices and screen sizes. Use media queries and responsive design principles to adjust layout and styling as needed.
- 13 - Prepare for Deployment: Once you're satisfied with your theme, you can deploy it to your live WordPress site. Zip the theme directory and upload it through the WordPress admin interface, or transfer the files directly to your server.
- 14 - Final Testing and Maintenance: Test your theme again on the live site to ensure everything works as expected. Monitor for any issues and be prepared to make adjustments as needed.


## Folder Structure

> You actually do not need anything else other than style.css, functions.php, index.php but still it is in your best interest to follow a standard

Here is a folder strucutre standart for your wordpress theme:
```python
your-theme-folder/
│
├── css/
│   ├── style.css            # Main stylesheet
│   └── responsive.css       # Responsive styles
│
├── js/
│   ├── script.js            # JavaScript files
│   └── vendor/              # Third-party libraries
│
├── images/                  # Theme images
│
├── fonts/                   # Theme fonts
│
├── template-parts/          # Reusable template parts
│   ├── header.php          # Header template
│   ├── footer.php          # Footer template
│   └── content.php         # Content template
│
├── template-parts/          # Reusable template parts
│   ├── header.php          # Header template
│   ├── footer.php          # Footer template
│   └── content.php         # Content template
│
├── inc/                     # PHP includes
│   ├── theme-setup.php      # Theme setup functions
│   ├── customizer.php       # Theme customizer options
│   └── widgets.php          # Custom widgets
│
├── languages/               # Translation files
│
├── page-templates/          # Custom page templates
│
├── 404.php                  # 404 page template
├── functions.php            # Theme functions
├── index.php                # Main template file
├── single.php               # Single post template
├── page.php                 # Single page template
├── archive.php              # Archive template
├── search.php               # Search results template
├── category.php             # Category archive template
├── tag.php                  # Tag archive template
│
├── style.css                # Theme metadata
└── screenshot.png           # Theme screenshot
```

