---
layout: post
title: "Permisos en la Libreria Multimedia de WP"
date: "2011-10-12"
categories: dev
---

# Gestión de permisos en la Liberia Multimedia de WP

 

Esta sección de WP no tiene permisos , con lo que podemos ver todos los recursos multimedia  subidos a un blog , sea o no multiusuario. Mediante un script encontrado en los foros de wordpres.org , un usuario que lo modifico y posteo en su blog y una chica muy simpática que dejo un comentario ,en dicho blog ,de  como modificar lo para la venta emergente de la librería.

Fuente de la versión 0.1 :  [Restricting Users to View Only their own Media Library Items](https://wordpress.org/support/topic/restricting-users-to-view-only-their-own-media-library-items?replies=7) la respuesta numero uno de **bruha**

?php
/\*
Plugin Name: Manage Your Media Only
Version: 0.1
\*/

//Manage Your Media Only
function mymo\_parse\_query\_useronly( $wp\_query ) {
    if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/upload.php' ) !== false ) {
        if ( !current\_user\_can( 'level\_5' ) ) {
            global $current\_user;
            $wp\_query->set( 'author', $current\_user->id );
        }
    }
}

add\_filter('parse\_query', 'mymo\_parse\_query\_useronly' );
?>

Fuente de la versión 0.2: [How to restrict users to view only their own media library items in wordpress](https://junvo.com/blog/2011/restrict-users-to-view-only-their-own-media-library-items-in-wordpress.html "How to restrict users to view only their own media library items in wordpress") Es un añadido para contar solo los elementos que son de nuestra propiedad y así aparezcan correctamente los contadores superiores.Tien como pega que hay que modificar los ficheros

- /wp-includes/post.php
- /wp-admin/includes/class-wp-media-table.php

Cosa que no he hecho , la dejo aquí por si un día me hace falta. Es un presentimiento

/wp-includes/post.php modify function wp\_count\_attachments:

function wp\_count\_attachments( $mime\_type = '' ) { global $wpdb; $and = wp\_post\_mime\_type\_where( $mime\_type ); $count = $wpdb->get\_results( "SELECT post\_mime\_type, COUNT( \* ) AS num\_posts FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' $and GROUP BY post\_mime\_type", ARRAY\_A ); $stats = array( ); foreach( (array) $count as $row ) { $stats\[$row\['post\_mime\_type'\]\] = $row\['num\_posts'\]; } $stats\['trash'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status = 'trash' $and"); $stats\['orphans'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_parent < 1 $and"); return apply\_filters( 'count\_attachments', (object) $stats, $mime\_type ); }

In /wp-admin/includes/class-wp-media-table.php in function get\_views replace

$\_total\_posts = array\_sum($\_num\_posts) - $\_num\_posts\['trash'\]; if ( !isset( $total\_orphans ) ) $total\_orphans = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_parent < 1" );

with

 $\_total\_posts = array\_sum($\_num\_posts) - $\_num\_posts\['trash'\] - $\_num\_posts\['orphans'\]; if ( !isset( $total\_orphans ) ) $total\_orphans = $\_num\_posts\['orphans'\];

?php /\* Plugin Name: Manage Your Media Only Version: 0.2 \*/ //Manage Your Media Only function mymo\_parse\_query\_useronly( $wp\_query ) {     if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/upload.php' ) !== false ) {         if ( !current\_user\_can( 'level\_5' ) ) {             global $current\_user;             $wp\_query->set( 'author', $current\_user->id );
        }
    }
}

add\_filter('parse\_query', 'mymo\_parse\_query\_useronly' );

/\*
 \* Count only allowed media library items
 \* Added by Vladimir Shugaev
 \*/

add\_filter('count\_attachments','count\_own\_attachments');
function count\_own\_attachments( $default, $mime\_type ) {
	global $wpdb, $current\_user, $pagenow;

    if( !is\_a( $current\_user, 'WP\_User') )
        return $default;

    if( 'upload.php' != $pagenow )
        return $default;

    if( !current\_user\_can('delete\_pages') ){
        $and = wp\_post\_mime\_type\_where( $mime\_type );
		$count = $wpdb->get\_results( "SELECT post\_mime\_type, COUNT( \* ) AS num\_posts FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_author= '$current\_user->id' $and GROUP BY post\_mime\_type", ARRAY\_A );

		$stats = array( );
		foreach( (array) $count as $row ) {
			$stats\[$row\['post\_mime\_type'\]\] = $row\['num\_posts'\];
		}
		$stats\['trash'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status = 'trash' AND post\_author= '$current\_user->id' $and");
		$stats\['orphans'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_parent < 1 AND post\_author= '$current\_user->id' $and");
		return (object)$stats;
	}
    return $default;
}

Fuente de la versión 0.3: [How to restrict users to view only their own media library items in wordpress](https://junvo.com/blog/2011/restrict-users-to-view-only-their-own-media-library-items-in-wordpress.html "How to restrict users to view only their own media library items in wordpress") ultimo comentario de Stefania el 04 de Octubre de 2011 at 10:42 AM

< ?php /\* Plugin Name: Manage Your Media Only Version: 0.3 \*/ //Manage Your Media Only function mymo\_parse\_query\_useronly( $wp\_query ) {     if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/upload.php' ) !== false ) {         if ( !current\_user\_can( 'level\_5' ) ) {             global $current\_user;             $wp\_query->set( 'author', $current\_user->id );
        }
    }
    if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/media-upload.php' ) !== false ) {
        if ( !current\_user\_can( 'level\_5' ) ) {
            global $current\_user;
            $wp\_query->set( 'author', $current\_user->id );
        }
/\*
 \* Management the window "media-upload.php" for the add new images to galery
 \* Added by Stafania
 \*/
        } else if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/media-upload.php' ) !== false ) {
        if ( !current\_user\_can( 'level\_5' ) ) {
            global $current\_user;
            $wp\_query->set( 'author', $current\_user->id );
        }
    }
}

add\_filter('parse\_query', 'mymo\_parse\_query\_useronly' );

/\*
 \* Count only allowed media library items
 \* Added by Vladimir Shugaev
 \*/

add\_filter('count\_attachments','count\_own\_attachments');
function count\_own\_attachments( $default, $mime\_type ) {
	global $wpdb, $current\_user, $pagenow;

    if( !is\_a( $current\_user, 'WP\_User') )
        return $default;

    if( 'upload.php' != $pagenow )
        return $default;

    if( !current\_user\_can('delete\_pages') ){
        $and = wp\_post\_mime\_type\_where( $mime\_type );
		$count = $wpdb->get\_results( "SELECT post\_mime\_type, COUNT( \* ) AS num\_posts FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_author= '$current\_user->id' $and GROUP BY post\_mime\_type", ARRAY\_A );

		$stats = array( );
		foreach( (array) $count as $row ) {
			$stats\[$row\['post\_mime\_type'\]\] = $row\['num\_posts'\];
		}
		$stats\['trash'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status = 'trash' AND post\_author= '$current\_user->id' $and");
		$stats\['orphans'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_parent < 1 AND post\_author= '$current\_user->id' $and");
		return (object)$stats;
	}
    return $default;
}

?>

Las bases están creadas , cada recursos posee datos identificativos suficientes como para poder establecer reglas de visualización. Desde el punto de vista de un programador necesitamos un filtro que actúe en el momento de ejecutar el `upload.php` y el `media-upload.php`

< ?php
/\*
Plugin Name: Manage Your Media Only
Version: 0.4
\*/

//Manage Your Media Only
function mymo\_parse\_query\_useronly( $wp\_query ) {
    if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/upload.php' ) !== false ) {
        if ( !current\_user\_can( 'level\_5' ) ) {
            global $current\_user;
            $wp\_query->set( 'author', $current\_user->id );
        }
    }

/\*
 \* Management the window "media-upload.php" for the add new images to galery
 \* Added by Luis Puente
 \*/
    if ( strpos( $\_SERVER\[ 'REQUEST\_URI' \], '/wp-admin/media-upload.php' ) !== false ) {
        if ( !current\_user\_can( 'level\_5' ) ) {
            global $current\_user;
            $wp\_query->set( 'author', $current\_user->id );
        }
    }
}

add\_filter('parse\_query', 'mymo\_parse\_query\_useronly' );

/\*
 \* Count only allowed media library items
 \* Added by Vladimir Shugaev
 \*/

add\_filter('count\_attachments','count\_own\_attachments');
function count\_own\_attachments( $default, $mime\_type ) {
	global $wpdb, $current\_user, $pagenow;

    if( !is\_a( $current\_user, 'WP\_User') )
        return $default;

    if( 'upload.php' != $pagenow )
        return $default;

    if( !current\_user\_can('delete\_pages') ){
        $and = wp\_post\_mime\_type\_where( $mime\_type );
		$count = $wpdb->get\_results( "SELECT post\_mime\_type, COUNT( \* ) AS num\_posts FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_author= '$current\_user->id' $and GROUP BY post\_mime\_type", ARRAY\_A );

		$stats = array( );
		foreach( (array) $count as $row ) {
			$stats\[$row\['post\_mime\_type'\]\] = $row\['num\_posts'\];
		}
		$stats\['trash'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status = 'trash' AND post\_author= '$current\_user->id' $and");
		$stats\['orphans'\] = $wpdb->get\_var( "SELECT COUNT( \* ) FROM $wpdb->posts WHERE post\_type = 'attachment' AND post\_status != 'trash' AND post\_parent < 1 AND post\_author= '$current\_user->id' $and");
		return (object)$stats;
	}
    return $default;
}

?>

Dichas reglas las utilizamos desde un fichero php subido como plugin.Este proceso consiste en crear una carpeta introducir este fichero php , comprimirla en zip. Así ya lo podemos cargar en nuestro wordpress
