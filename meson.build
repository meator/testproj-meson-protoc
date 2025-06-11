project(
  'testproj',
  'cpp',
  default_options: [
    'warning_level=3',
    'cpp_std=gnu++20',
  ],
)

sources = files('test.cc')

# Pull in wrap.
dependency('protobuf')
protoc = find_program('protoc')

proto_outputs = custom_target(
  # TODO
  command: [protoc, '--cpp_out', '@OUTDIR@', '-I', '@CURRENT_SOURCE_DIR@', '@INPUT@'],
  input: 'key_type.proto',
  output: ['key_type.pb.cc', 'key_type.pb.h'],
)
sources += proto_outputs

static_library(
  'mylib',
  sources,
)
