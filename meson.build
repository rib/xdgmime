project('xdgmime', 'c', license: 'MIT')

deps = []

clib_sp = subproject('clib')
deps += clib_sp.get_variable('clib_dep')

deps += dependency('libuv', fallback: [ 'libuv', 'libuv_dep' ])

inc = include_directories('.')

defines = [
    '-D_ALL_SOURCE=1',
    '-D_GNU_SOURCE=1',
]

src = [
    'glob.c',
    'glob.h',
    'magic.c',
    'magic.h',
    'xdgmime-query.c',
    'xdgmime.c',
    'xdgmime.h',
]

xdgmime_lib = library('xdgmime', src,
                      c_args: defines,
                      dependencies: deps)
xdgmime_dep = declare_dependency(link_with: xdgmime_lib, include_directories: inc)

xdgmime_query = executable('xdgmime-query', [ 'xdgmime-query.c' ],
                           c_args: defines,
                           dependencies: deps + [ xdgmime_dep ],
                           native: true)

