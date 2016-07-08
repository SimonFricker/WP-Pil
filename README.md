# WP-Pil


          function html5_insert_image($html, $id, $caption, $title, $align, $url) {
          	$image_attributes = wp_get_attachment_image_src(  $id, $size = 'large', $icon = false  ); // returns an array
          	$url_large = $image_attributes[0];
          	$image_attributes_thumb = wp_get_attachment_image_src(  $id, $size = 'preload-thumb', $icon = false  ); // returns an array
          	$url_thumb = $image_attributes_thumb[0];
          
          	$metadata = wp_get_attachment_metadata ($id);
          	$width = $metadata['width'];
          	$height = $metadata['height'];
          
            $html5 = "<figure id='post-$id media-$id' class='pil img-responsive align-$align'>";
            $html5 .= "<a class='fluidlightbox' href='$url_large'><img src='$url_large' alt='$title' data-pil-thumb-url='$url_thumb' data-full-width='$width' data-full-height='$height' /></a>";
            $html5 .= "</figure>";
            return $html5;
          }
          add_filter( 'image_send_to_editor', 'html5_insert_image', 10, 9 );


