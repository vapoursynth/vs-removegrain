project('removegrain', 'c', 'cpp',
  version : '1',
  default_options : ['warning_level=3'])

add_project_arguments('-ffast-math', language : 'c')

sources = [
     'src/clense.cpp',
     'src/removegrainvs.cpp',
     'src/repairvs.cpp',
     'src/shared.cpp',
     'src/shared.h',
     'src/verticalcleaner.cpp'
]

vapoursynth_dep = dependency('vapoursynth', version: '>=55').partial_dependency(compile_args : true, includes : true)

deps = [vapoursynth_dep]

shared_module('removegrain', sources,
  dependencies : deps,
  install : true,
  install_dir : join_paths(vapoursynth_dep.get_pkgconfig_variable('libdir'), 'vapoursynth'),
  gnu_symbol_visibility : 'hidden'
)
