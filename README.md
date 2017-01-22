# WP Term Media #

WP drop-in to add media attachments to terms, using the `WP_Term_Meta_UI` class by @stuttter

## Description ##

> This WordPress drop-in requires at least [WordPress](https://wordpress.org) 4.7.

Adding attachments to terms through the Media Library is simplified through this drop-in class. Use this in your plugin or theme to add media selection in your term creation/publishing workflow. 

## Usage ##

To include this drop-in in your project, do the following:

1. Put the drop-in class file and `assets` folder in your project
2. Require the `WP_Term_Meta_UI` class by @stuttter, for example from their [WP Term Colors plugin](https://github.com/stuttter/wp-term-colors/blob/master/includes/class-wp-term-meta-ui.php).
3. Require the `class-wp-term-media.php` class file in your main project file
4. Register a term media item with `new WP_Term_Media()`, generally at the 'init' action
5. You're done!

```php
// 2/3. In your main project file
require( $path_to_file . 'class-wp-term-meta-ui.php' );
require( $path_to_file . 'class-wp-term-media.php' );

// 4. When hooking in 'init'
new WP_Term_Media(
	__FILE__, // Location where the assets folder was placed
	array(
		'meta_key'   => 'meta-key',      // Term meta key
		'mime_type'  => 'image',         // Mime type of selectable attachments. Can be 'image', 'video', 'audio', or any mime type in wp_get_mime_types(). Defaults to 'image'.
		'image_size' => array( 50, 50 ), // For images, the size to add when it does not exist yet. Can be image size name or array with dimensions.
		'labels'     => array(           // Labels for the Media Library
			'setTermMedia'    => __( 'Set Term Attachment',    'your-textdomain' ),
			'termMediaTitle'  => __( 'Term Attachment',        'your-textdomain' ),
			'removeTermMedia' => __( 'Remove Term Attachment', 'your-textdomain' ),
		),
	)
);
```

## Contributing ##

You can contribute to the development of this drop-in by [opening a new issue](https://github.com/lmoffereins/wp-term-media/issues/) to report a bug or request a feature in the drop-in's GitHub repository.

## Related ##

See also the `WP_Post_Media` and `WP_Setting_Media` drop-ins, to select media attachments for posts and settings respectively.
