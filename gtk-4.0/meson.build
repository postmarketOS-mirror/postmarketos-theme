scss_files = files([
  '_colors-public.scss',
  '_colors.scss',
  '_common.scss',
  '_drawing.scss',
])

foreach variant: theme_variants
  variant_target = custom_target('postmarketOS theme variant: ' + variant,
    input: 'postmarketOS-@0@.scss'.format(variant),
    output: 'postmarketOS-@0@.css'.format(variant),
    command: [
      sassc, sassc_opts, '@INPUT@', '@OUTPUT@',
    ],
    build_by_default: true,
    depend_files: scss_files,
  )
  dest_theme_dir = get_option('datadir') / 'themes' / 'postmarketos-'+variant

  meson.add_install_script (install_exec,
      variant_target.full_path(),
      dest_theme_dir / 'gtk-4.0' / 'gtk.css'
      )
  install_subdir('assets',
    install_dir: dest_theme_dir / 'gtk-4.0')
endforeach
