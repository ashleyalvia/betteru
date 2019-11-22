# betteru
better urself, be a better u


et_header();

$default         = hestia_get_blog_layout_default();
$sidebar_layout  = apply_filters( 'hestia_sidebar_layout', get_theme_mod( 'hestia_blog_sidebar_layout', $default ) );
$wrapper_classes = apply_filters( 'hestia_filter_archive_content_classes', 'col-md-8 archive-post-wrap' );

do_action( 'hestia_before_archive_content' );

?>

<div class="<?php echo hestia_layout(); ?>">
	<div class="hestia-blogs" data-layout="<?php echo esc_attr( $sidebar_layout ); ?>">
		<div class="container">
			<div class="row">
				<?php
				if ( $sidebar_layout === 'sidebar-left' ) {
					get_sidebar();
				}
				?>
				<div class="<?php echo esc_attr( $wrapper_classes ); ?>">
					<?php
					if ( have_posts() ) :
						while ( have_posts() ) :
							the_post();
							get_template_part( 'template-parts/content' );
						endwhile;
						the_posts_pagination();
						else :
							get_template_part( 'template-parts/content', 'none' );
					endif;
						?>
				</div>
				<?php

				if ( $sidebar_layout === 'sidebar-right' ) {
					get_sidebar();
				}
				?>
			</div>
		</div>
	</div>
	<?php
	get_footer(); ?>
