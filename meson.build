project('postmarketos-theme', version: '0.1.0')

theme_variants = [
  'light',
  'dark',
  'oled',
]

sassc = find_program('sassc', required: true)
sassc_opts = ['-a', '-M', '-t', 'compact']

install_exec = meson.current_source_dir() / 'meson' / 'install-to-dir.py'

foreach variant: theme_variants
  conf = configuration_data()
  conf.set('variant', variant)
  cf = configure_file(
    input: 'index.theme.in',
    output: 'pmos-@0@.theme'.format(variant),
    configuration: conf
  )
  dest_theme_dir = get_option('datadir') / 'themes' / 'postmarketos-'+variant

  install_data(cf,
    install_dir: dest_theme_dir,
    rename: 'index.theme',
  )
endforeach


subdir('gtk-4.0')
subdir('gtk-3.0')