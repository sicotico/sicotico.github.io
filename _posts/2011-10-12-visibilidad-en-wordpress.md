---
layout: single
title: "Visibilidad en Wordpress"
date: "2011-10-12"
categories: dev
---

En wp-admin/includes está el fichero meta-boxes.php , la definición de visibilidad de los post esta ligada a la variable $visibility  , siendo el caso base para comprobar dicha variable. En la linea 123 podemos encontrar esta definición:

113 if ( 'private' == $post->post\_status ) {
114         $post->post\_password = '';
115         $visibility = 'private';
116         $visibility\_trans = \_\_('Private');
117 } elseif ( !empty( $post->post\_password ) ) {
118         $visibility = 'password';
119         $visibility\_trans = \_\_('Password protected');
120 } elseif ( $post\_type == 'post' && is\_sticky( $post->ID ) ) {
121         $visibility = 'public';
122         $visibility\_trans = \_\_('Public, Sticky');
123 } else {
124         $visibility = 'public';
125         $visibility\_trans = \_\_('Public');
126 }

Debemos dejarlo de esta manera:

113 if ( 'private' == $post->post\_status ) {
114         $post->post\_password = '';
115         $visibility = 'private';
116         $visibility\_trans = \_\_('Private');
117 } elseif ( !empty( $post->post\_password ) ) {
118         $visibility = 'password';
119         $visibility\_trans = \_\_('Password protected');
120 } elseif ( $post\_type == 'post' && is\_sticky( $post->ID ) ) {
121         $visibility = 'public';
122         $visibility\_trans = \_\_('Public, Sticky');
123 } else {
124         $visibility = 'private';
125         $visibility\_trans = \_\_('Private');
126 }

Así conseguimos que el caso base sea privado. Si queremos seguir interaccionando con esta variable desde la interfaz de wordpress no tendremos ningún problema.

Fuente:

## \[resolved\] How to set new posts visibility to private by default ? (14 posts)

1. ![](https://www.gravatar.com/avatar/c8cf87bffb092e30838b920fde631dfe?s=48&d=monsterid&r=g)**StoarceCreierul**
    
    [Member](https://wordpress.org/support/profile/stoarcecreierul)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1502511)
    
    The scenario is registered users posting for other registered users only, using custom simple forms.
    
    Is there a plugin or way to hack the default visibility settings for new posts to private ?
    
2. ![](https://www.gravatar.com/avatar/75d5503e3b8135d7b93b0c5696922ee2?s=48&d=monsterid&r=g)**sagar\_mehta**
    
    [Member](https://wordpress.org/support/profile/sagar_mehta)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1508121)
    
    I am looking for a solution to this myself.
    
    I'd love to learn how this can be done.
    
    Sagar
    
3. ![](https://www.gravatar.com/avatar/75d5503e3b8135d7b93b0c5696922ee2?s=48&d=monsterid&r=g)**sagar\_mehta**
    
    [Member](https://wordpress.org/support/profile/sagar_mehta)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1508678)
    
    Just discovered how to do this:
    
    For this, you need to edit the file 'meta-boxes.php' located in wp-admin/includes/ folder.
    
    Open that file in NotePad and find the following code:
    
    ```
    $visibility = 'public'; $visibility_trans = __('Public');
    ```
    
    Now, all you need to do is change it do the following:
    
    ```
    $visibility = 'private'; $visibility_trans = __('Private');
    ```
    
    Done.
    
    You can even hide the Visibility option so that users can't change it. To do that, find the following code in the same file:
    
    ```
    <a href="#visibility"><?php _e('Edit'); ?></a> <div id="post-visibility-select"> <input type="hidden" name="hidden_post_password" id="hidden-post-password" value="<?php echo esc_attr($post->post_password); ?>" /> <?php if ($post_type == 'post'): ?> <input type="checkbox" style="display:none" name="hidden_post_sticky" id="hidden-post-sticky" value="sticky" <?php checked(is_sticky($post->ID)); ?> /> <?php endif; ?> <input type="hidden" name="hidden_post_visibility" id="hidden-post-visibility" value="<?php echo esc_attr( $visibility ); ?>" /> <input type="radio" name="visibility" id="visibility-radio-public" value="public" <?php checked( $visibility, 'public' ); ?> /> <label for="visibility-radio-public"><?php _e('Public'); ?></label><br /> <?php if ($post_type == 'post'): ?> <span id="sticky-span"><input id="sticky" name="sticky" type="checkbox" value="sticky" <?php checked(is_sticky($post->ID)); ?> tabindex="4" /> <label for="sticky"><?php _e('Stick this post to the front page') ?></label><br /></span> <?php endif; ?> <input type="radio" name="visibility" id="visibility-radio-password" value="password" <?php checked( $visibility, 'password' ); ?> /> <label for="visibility-radio-password"><?php _e('Password protected'); ?></label><br /> <span id="password-span"><label for="post_password"><?php _e('Password:'); ?></label> <input type="text" name="post_password" id="post_password" value="<?php echo esc_attr($post->post_password); ?>" /><br /></span> <input type="radio" name="visibility" id="visibility-radio-private" value="private" <?php checked( $visibility, 'private' ); ?> /> <label for="visibility-radio-private"><?php _e('Private'); ?></label><br /> <p> <a href="#visibility"><?php _e('OK'); ?></a> <a href="#visibility"><?php _e('Cancel'); ?></a> </p> </div>
    ```
    
    Replace that with the following:
    
    ```
    <!-- <a href="#visibility"><?php _e('Edit'); ?></a> <div id="post-visibility-select"> <input type="hidden" name="hidden_post_password" id="hidden-post-password" value="<?php echo esc_attr($post->post_password); ?>" /> <?php if ($post_type == 'post'): ?> <input type="checkbox" style="display:none" name="hidden_post_sticky" id="hidden-post-sticky" value="sticky" <?php checked(is_sticky($post->ID)); ?> /> <?php endif; ?> <input type="hidden" name="hidden_post_visibility" id="hidden-post-visibility" value="<?php echo esc_attr( $visibility ); ?>" /> <input type="radio" name="visibility" id="visibility-radio-public" value="public" <?php checked( $visibility, 'public' ); ?> /> <label for="visibility-radio-public"><?php _e('Public'); ?></label><br /> <?php if ($post_type == 'post'): ?> <span id="sticky-span"><input id="sticky" name="sticky" type="checkbox" value="sticky" <?php checked(is_sticky($post->ID)); ?> tabindex="4" /> <label for="sticky"><?php _e('Stick this post to the front page') ?></label><br /></span> <?php endif; ?> <input type="radio" name="visibility" id="visibility-radio-password" value="password" <?php checked( $visibility, 'password' ); ?> /> <label for="visibility-radio-password"><?php _e('Password protected'); ?></label><br /> <span id="password-span"><label for="post_password"><?php _e('Password:'); ?></label> <input type="text" name="post_password" id="post_password" value="<?php echo esc_attr($post->post_password); ?>" /><br /></span> <input type="radio" name="visibility" id="visibility-radio-private" value="private" <?php checked( $visibility, 'private' ); ?> /> <label for="visibility-radio-private"><?php _e('Private'); ?></label><br /> <p> <a href="#visibility"><?php _e('OK'); ?></a> <a href="#visibility"><?php _e('Cancel'); ?></a> </p> </div> -->
    ```
    
    Basically, just commenting out the part by using <!-- and -->. A plugin for this would be awesome.
    
    **WARNING:** Commenting out the form will mean that NO ONE can make a public or password protected post. And all your pages will be Private by default without an option to change them back to public.
    
    The work around is that after you create a page or write a post you want to be public, just go to the 'Edit Posts' or 'Edit Pages' screen and uncheck the 'Private Post' / 'Private Page' checkbox under Quick Edit.
    
    Regards,
    
    Sagar
    
4. ![](https://www.gravatar.com/avatar/c8cf87bffb092e30838b920fde631dfe?s=48&d=monsterid&r=g)**StoarceCreierul**
    
    [Member](https://wordpress.org/support/profile/stoarcecreierul)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1508858)
    
    This is it, thank you Sagar !
    
    Now how do we get rid of the "Private:" text at the beginning of the title ?
    
5. ![](https://www.gravatar.com/avatar/75d5503e3b8135d7b93b0c5696922ee2?s=48&d=monsterid&r=g)**sagar\_mehta**
    
    [Member](https://wordpress.org/support/profile/sagar_mehta)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1513103)
    
    To hide the Visiblity: Private part that shows up, find the following code in the same file:
    
    ```
    <?php _e('Visibility:'); ?> <span id="post-visibility-display"><?php if ( 'private' == $post->post_status ) { $post->post_password = ''; $visibility = 'private'; $visibility_trans = __('Private'); } elseif ( !empty( $post->post_password ) ) { $visibility = 'password'; $visibility_trans = __('Password protected'); } elseif ( $post_type == 'post' && is_sticky( $post->ID ) ) { $visibility = 'public'; $visibility_trans = __('Public, Sticky'); } else { $visibility = 'Private'; $visibility_trans = __('Private'); } echo esc_html( $visibility_trans ); ?>
    ```
    
    And replace it with the following:
    
    ```
    <!-- <?php _e('Visibility:'); ?> <span id="post-visibility-display"><?php if ( 'private' == $post->post_status ) { $post->post_password = ''; $visibility = 'private'; $visibility_trans = __('Private'); } elseif ( !empty( $post->post_password ) ) { $visibility = 'password'; $visibility_trans = __('Password protected'); } elseif ( $post_type == 'post' && is_sticky( $post->ID ) ) { $visibility = 'public'; $visibility_trans = __('Public, Sticky'); } else { $visibility = 'Private'; $visibility_trans = __('Private'); } echo esc_html( $visibility_trans ); ?> -->
    ```
    
    Again, simply commenting out the section :)
    
    Hope this helps :)
    
    Regards,
    
    Sagar
    
6. ![](https://www.gravatar.com/avatar/c8cf87bffb092e30838b920fde631dfe?s=48&d=monsterid&r=g)**StoarceCreierul**
    
    [Member](https://wordpress.org/support/profile/stoarcecreierul)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1521111)
    
    I commented out the section but the private post still shows up with that text at the beginning:
    
    `Private: Hello World!`
    
    We should change something in /wp-includes/post-template.php on line 116.
    
    Here's the complete Retrieve post title function:
    
    ```
    function get_the_title( $id = 0 ) { $post = &get_post($id); $title = $post->post_title; if ( !is_admin() ) { if ( !empty($post->post_password) ) { $protected_title_format = apply_filters('protected_title_format', __('Protected: %s')); $title = sprintf($protected_title_format, $title); } else if ( isset($post->post_status) && 'private' == $post->post_status ) { $private_title_format = apply_filters('private_title_format', __('Private: %s')); $title = sprintf($private_title_format, $title); } } return apply_filters( 'the_title', $title, $post->ID ); }
    ```
    
7. ![](https://www.gravatar.com/avatar/75d5503e3b8135d7b93b0c5696922ee2?s=48&d=monsterid&r=g)**sagar\_mehta**
    
    [Member](https://wordpress.org/support/profile/sagar_mehta)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1526284)
    
    Oh ok, I thought you were talking about the 'Visibility: Private' section that shows up on the right hand side on the 'Write Post' page.
    
    To remove the "Private: " part from the title of the post, change the following line of code in your code above:
    
    `$private_title_format = apply_filters('private_title_format', __('Private: %s'));`
    
    To this:
    
    `$private_title_format = apply_filters('private_title_format', __('%s'));`
    
    That should do it :)
    
    Sagar
    
8. ![](https://www.gravatar.com/avatar/c8cf87bffb092e30838b920fde631dfe?s=48&d=monsterid&r=g)**StoarceCreierul**
    
    [Member](https://wordpress.org/support/profile/stoarcecreierul)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1528752)
    
    Thank you !
    
9. ![](https://www.gravatar.com/avatar/09b4f585089248a6984effb6c2d35033?s=48&d=monsterid&r=g)**mattloak**
    
    [Member](https://wordpress.org/support/profile/mattloak)
    
    Posted 1 year ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1709617)
    
    Is there any way to make the post default to Private without editing core files? Can this be done with filters in the functions.php file?
    
10. ![](https://www.gravatar.com/avatar/d4d25d9271f32496b80bbdb4ac49916b?s=48&d=monsterid&r=g)**gewone**
    
    [Member](https://wordpress.org/support/profile/gewone)
    
    Posted 11 months ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1759634)
    
    Big thanks for this. Perfect solution for your private life journal. Hopefully there will be a designer setting in the actual GUI somewhere soon (WP v3.1 perhaps?). I love the blogging engine anyways. ♥
    
11. ![](https://www.gravatar.com/avatar/cd5d24f11b5b66ea658e94c0ec025d39?s=48&d=monsterid&r=g)**fireghost**
    
    [Member](https://wordpress.org/support/profile/fireghost)
    
    Posted 10 months ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1814589)
    
    after set it as private, i can't search it's content even after I log in, what can i do? thanks!!
    
12. ![](https://www.gravatar.com/avatar/960965e56eaa66e6797bb855953f6030?s=48&d=monsterid&r=g)**jorve**
    
    [Member](https://wordpress.org/support/profile/jorve)
    
    Posted 7 months ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1957575)
    
    my problem with this workaround is that, once the post is made public, the page still defaults to private setting, so that if the page is updated, it becomes "privately published" once again.
    
    Trying to figure out a way to change this....
    
13. ![](https://www.gravatar.com/avatar/960965e56eaa66e6797bb855953f6030?s=48&d=monsterid&r=g)**jorve**
    
    [Member](https://wordpress.org/support/profile/jorve)
    
    Posted 7 months ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-1957651)
    
    nvm, I figured it out..... if (in the meta-boxes.php file) you replace:
    
    ```
    if ( 'private' == $post->post_status ) { $post->post_password = ''; $visibility = 'private'; $visibility_trans = __('Private'); } elseif ( !empty( $post->post_password ) ) { $visibility = 'password'; $visibility_trans = __('Password protected'); } elseif ( $post_type == 'post' && is_sticky( $post->ID ) ) { $visibility = 'public'; $visibility_trans = __('Public, Sticky'); } else { $visibility = 'public'; $visibility_trans = __('Public'); }
    ```
    
    with:
    
    ```
    if ( 'publish' == $post->post_status ) { $post->post_password = ''; $visibility = 'public'; $visibility_trans = __('Public'); } elseif ( !empty( $post->post_password ) ) { $visibility = 'password'; $visibility_trans = __('Password protected'); } elseif ( $post_type == 'post' && is_sticky( $post->ID ) ) { $visibility = 'public'; $visibility_trans = __('Public, Sticky'); } else { $visibility = 'private'; $visibility_trans = __('Private'); }
    ```
    
    then your posts will default to Private, but once they have been published publicly, they will remain public.
    
14. ![](https://www.gravatar.com/avatar/0c1e2e1d07b4bf856d79c2ddfc218b8f?s=48&d=monsterid&r=g)**pat.heard**
    
    [Member](https://wordpress.org/support/profile/patheard)
    
    Posted 5 months ago [#](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14#post-2074408)
    
    If you want to do it without editing the core files, you can hook into the **post\_submitbox\_misc\_actions** action and add some jQuery that will fire onload:
    
    ```
    function default_post_visibility(){ global $post; if ( 'publish' == $post->post_status ) { $visibility = 'public'; $visibility_trans = __('Public'); } elseif ( !empty( $post->post_password ) ) { $visibility = 'password'; $visibility_trans = __('Password protected'); } elseif ( $post_type == 'post' && is_sticky( $post->ID ) ) { $visibility = 'public'; $visibility_trans = __('Public, Sticky'); } else { $post->post_password = ''; $visibility = 'private'; $visibility_trans = __('Private'); } ?> <script type="text/javascript"> (function($){ try { $('#post-visibility-display').text('<?php echo $visibility_trans; ?>'); $('#hidden-post-visibility').val('<?php echo $visibility; ?>'); $('#visibility-radio-<?php echo $visibility; ?>').attr('checked', true); } catch(err){} }) (jQuery); </script> <?php } add_action( 'post_submitbox_misc_actions' , 'default_post_visibility' );
    ```
    

Fuente: [Wordpress.org Foro](https://wordpress.org/support/topic/how-to-set-new-post-visibility-to-private-by-default?replies=14 "Visibility default wordpress")
