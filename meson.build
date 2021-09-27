project('removegrain', 'cpp',
  version : '1',
  default_options : ['warning_level=3'])

add_project_arguments('-ffast-math', language : 'cpp')

sources = [
     'src/clense.cpp',
     'src/removegrainvs.cpp',
     'src/repairvs.cpp',
     'src/shared.cpp',
     'src/shared.h',
     'src/verticalcleaner.cpp'
]

vapoursynth_dep = dependency('vapoursynth', version: '>=55').partial_dependency(compile_args : true, includes : true)

if host_machine.cpu_family().startswith('x86')
  add_project_arguments('-DVS_TARGET_CPU_X86', '-mfpmath=sse', '-msse2', language: 'cpp')
endif

if host_machine.system() == 'windows'
  add_project_link_arguments('-static', language: 'cpp')
endif

deps = [vapoursynth_dep]

shared_module('removegrain', sources,
  dependencies : deps,
  install : true,
  install_dir : join_paths(vapoursynth_dep.get_pkgconfig_variable('libdir'), 'vapoursynth'),
  gnu_symbol_visibility : 'hidden'
)
