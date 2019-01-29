load('//:buckaroo_macros.bzl', 'buckaroo_deps')
load('//:subdir_glob.bzl', 'subdir_glob')

posix_srcs = glob([
  'src/posix/**/*.cpp',
])

windows_srcs = glob([
  'src/windows/**/*.cpp',
])

avx2_srcs = [
  'src/dump_avx2.cpp',
]

sse3_srcs = [
  'src/dump_ssse3.cpp',
]

cxx_library(
  name = 'log',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', '**/*.hpp'),
  ]),
  headers = subdir_glob([
    ('src', '**/*.hpp'),
  ]),
  srcs = glob([
    'src/setup/**/*.cpp',
    'src/*.cpp',
  ], exclude = avx2_srcs + sse3_srcs),
  platform_srcs = [
    ('linux.*', posix_srcs),
    ('macos.*', posix_srcs),
    ('windows.*', windows_srcs),
  ],
  deps = buckaroo_deps(),
  visibility = [
    'PUBLIC',
  ],
)
