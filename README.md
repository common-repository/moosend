# Wordpress Subscription Forms

With Wordpress Subscription Forms you can link your forms with your Moosend account. Customize design elements on the form so that it aligns with the user's brand as well as save time segmenting by automatically determining which mailing list each subscription form is linked to.

Wordpress Subscription Forms provide an easy-to-use admin panel that enables you to: 
- Register, if you're not already a Moosend user.
- Connect your wordpress forms with your Moosend account using your unique API Key.
- Create a subscription form for your site and find it's [shortcode](https://codex.wordpress.org/Shortcode_API) in the `All Forms` tab.
- Edit and Manage your existing forms.

### Download/Installation

Notes on how to download and install the plugin lay [here](https://wordpress.org/plugins/moosend/#description)
Or
Your can install the plugin to your [wordpress](https://wordpress.org/) site by browsing to your admin panel -> Plugins and searching for Moosend Subscription Forms.

### Developement

[Wordpress Plugin Boilerplate](https://github.com/devinvinson/WordPress-Plugin-Boilerplate/) was used, as it provides you with helpful comments and a project structure.

##### Includes
Note that if you include your own classes, or third-party libraries, there are three locations in which said files may go:

`plugin-name/includes` is where functionality shared between the admin area and the public-facing parts of the site reside
`plugin-name/admin` is for all admin-specific functionality
`plugin-name/public` is for all public-facing functionality

At this point, I will go through some of the more important classes and its functions in the project:

##### Moosend_For_Wp

This class is responsible for orchestrating the [actions](https://developer.wordpress.org/plugins/hooks/actions/) and [filters](https://developer.wordpress.org/plugins/hooks/filters/) of the core plugin. 
In there we define internationalization functionality for the plugin as well.

##### Moosend_Form_WP_Admin

Contains every single function that is going to be used in the admin panel, including service calls and rendering methods
Important methods explained: 

`enqueue_styles`: Register in here any styles that will be used in the admin panel.
`enqueue_scripts`: Register in here any scripts that will be used in the admin panel.
`add_plugin_admin_menu`: This function is responsible for registering the menu and submenus of the plugin in the admin panel.
`add_theme_url`: By using less css it assignes the id #preview alongside with each theme style. This way we can achive to use the user's theme styling. In order to render a real time preview of the form.

Note: callback functions are used to cooperate with javascript methods asynchronously.

##### Moosend_Form_WP_Public

Contains every single function that is going to be used in the public section of the plugin (server side functionality), including service calls and rendering methods

Important methods explained: 

`enqueue_styles`: Register in here any styles that will be used in the public section.
`enqueue_scripts`: Register in here any scripts that will be used in the public section.

Note: callback functions are used to cooperate with javascript methods asynchronously.

### Deployment

When you deploy you need to have 4 main directories

`assets`: Screenshots, headers and icons go in there
`trunk `: this is the directory where you’ll put the plugin files
`branches`: Divergent branches of code go in there
`tags`: All the plugin releases will be stored there

This is informative, you don't need to create them manually

Firstly you fetch the code, using any [svn manager](https://tortoisesvn.net/downloads.html) from your wordpress repository.
For the subscription forms plugin perfmorm a chechout using https://plugins.svn.wordpress.org/moosend/
Make sure to get username and password for Moosend's wordpress account from your team leader.

After you have fetched the code, you can make any changes required in the trunk folder where your plugin files exist.
Then you need to change the plugin version in `moosend-for-wp.php` and `readme.txt`
Then you have to create a new version in the tags folder. Name that folder with the version number

In order to release your new version you follow this process
- Use SVN to add the code
- Commit the code using a message (ex. "Release 1.0.93")

If everything worked smoothly you should now see the new version deployed in https://wordpress.org/plugins/moosend/