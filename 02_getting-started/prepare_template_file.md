*Getting Started*

##Prepare the WordPress template

This guide is based on a Twentyfifteen child theme.  
Ares were added to the 'page' post type, so the file to alter in that case is the template part content-page.php.

If you are using a different theme, use the corresponding theme file for pages.

There are basically two ways of rendering areas: by area id, or all areas of a single context.

If you followed the guide you have two areas in the `normal` context, makes sense to render all areas at once

####do_action('kb_context', $context, $post_id, $args)

This hook will render all areas of the given context in the order they appear on the edit screen.  
`do_action` makes sure that no errors appear if the plugin is inactive.

**Alternative functions:**
- `kb_render_context( $context, $post_id, $additionalArgs )`
- `\Kontentblocks\renderContext( $context, $post_id, $additionalArgs );`

###The changed content-page.php

```html
<?php
/**
 * The template used for displaying page content
 *
 * @package WordPress
 * @subpackage Twenty_Fifteen
 * @since Twenty Fifteen 1.0
 */
?>

<article id="post-<?php the_ID(); ?>" <?php post_class(); ?>>
	<?php
		// Post thumbnail.
		twentyfifteen_post_thumbnail();
	?>

	<header class="entry-header">
		<?php the_title( '<h1 class="entry-title">', '</h1>' ); ?>
	</header><!-- .entry-header -->

	<div class="entry-content">
		<?php the_content(); ?>
		<?php
		    // add area output after the regular content 
		    do_action('kb_context', 'normal');
	    ?>
		<?php
			wp_link_pages( array(
				'before'      => '<div class="page-links"><span class="page-links-title">' . __( 'Pages:', 'twentyfifteen' ) . '</span>',
				'after'       => '</div>',
				'link_before' => '<span>',
				'link_after'  => '</span>',
				'pagelink'    => '<span class="screen-reader-text">' . __( 'Page', 'twentyfifteen' ) . ' </span>%',
				'separator'   => '<span class="screen-reader-text">, </span>',
			) );
		?>
	</div><!-- .entry-content -->



	<?php edit_post_link( __( 'Edit', 'twentyfifteen' ), '<footer class="entry-footer"><span class="edit-link">', '</span></footer><!-- .entry-footer -->' ); ?>

</article><!-- #post-## -->
```

`do_action('kb_context', 'normal');` added after `the_content`.  
`$post_id`, if not set, will be the same as the return value of `get_the_ID()`.  
More `$args` could have been set to change the behavior of the area render engine, but are optional. 

####do_action('kb_area', $area_id, $post_id, $args)

Works the same way as the `kb_context` hook, but takes an specific `$area_id` instead.


**Alternative functions:**  
- `kb_render_area( $area_id, $post_id, $additionalArgs )`
- `\Kontentblocks\renderSingleArea( $area_id, $post_id, $additionalArgs );`

Next step: create the module front-end template