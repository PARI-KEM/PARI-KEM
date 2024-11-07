
## $$\sf HEY !! \space $$
## $$\frak{Welcome \space to \space my \space profile \space }$$

if b"ICC_PROFILE\0" == &app2_marker_data[0..12] {
   let icc = &app2_marker_data[14..]; // Lazy assumption that the profile is smaller than 64KB
   let profile = Profile::new_icc(icc)?;
   let t = Transform::new(&profile, PixelFormat::RGB_8,
       &Profile::new_srgb(), PixelFormat::RGB_8, Intent::Perceptual);
   t.transform_in_place(&mut rgb);
}

