# Theme integration

To test our views we'll create in the section, we should make sure that we actually see the modules output.

I will use the `page.php` and `sidebar-content.php` file of Twentyfourteen to demonstrate the integration, but every other theme will work as well.

For brevity, I completly replace the inner content of the `<div id="content"...</div>` with:
```

    <div id="page-content" class="site-content" role="main">
    <?php
        do_action('area', 'demo-content', null, array('context' => 'page', 'subcontext' => 'page-content'));
    ?>
    </div><!-- #content -->
```

**Important**: the plugin does not care of the 'loop'. I've removed it because we are not using 'post_content' in this example. If you use Kontentblocks areas alongside native concepts, you simply do things like you always do. No problemo.

We are using a standard WordPress hook, because it fails gracefully if the callback doesn't exist (plugin deactivated...).

The callback function looks like this, which is a little more descriptive:

    global $post;
    $postId = ( null === $id ) ? $post->ID : $id;
    $AreaRender = new AreaRenderer( $postId, $area, $additionalArgs );
    $AreaRender->render( true );


In `sidebar-content.php`, agian for brevity, I've replaced everything with:

```
<div id="content-sidebar" class="content-sidebar widget-area" role="complementary">
	<?php dynamic_sidebar( 'sidebar-2' ); ?>
    <?php do_action('sidebar_areas', null, array('context' => 'page', 'subcontext' => 'sidebar')); ?>
</div><!-- #content-sidebar -->```


Please note that we use a different hook here: `sidebar_areas`  
We could have used:  
`do_action('area', 'demo-sidebar', null, array('context' => 'page', 'subcontext' => 'page-content'));`

as well, and it would work as expected.  
Areas in the context of 'side' a kind of an exception resp. are part of another concept which we didn't touch yet.  
It's similar to the way WordPress sidebars work, because many users are familiar with the idea of sidebars in WordPress. That's the reason why Kontentblocks tries to mimic that concept.  
So it's possible to let users generate custom (side) areas through the backend and activate them on a per-post basis.  
That said, it's worth a own chapter.

Let's go ahead with creating some real stuff: HTML aka. Views