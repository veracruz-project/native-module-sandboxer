# A program using Google's Sandboxed API to run Veracruz native modules in a
# sandboxed environment.
#
# AUTHORS
#
# The Veracruz Development Team.
#
# COPYRIGHT AND LICENSING
#
# See the `LICENSE_MIT.markdown` file in the root directory for copyright and
# licensing information.
# Based on Google's Sandboxed API, Apache-2.0 license https://github.com/google/sandboxed-api/blob/main/LICENSE

project(NativeModuleSandboxer C CXX ASM)

add_subdirectory(sandboxed-api)

add_executable(native-module-sandboxer
  native-module-sandboxer.cc
)
set_target_properties(native-module-sandboxer PROPERTIES OUTPUT_NAME native-module-sandboxer)
add_executable(native-module-sandboxer)
target_link_libraries(native-module-sandboxer PRIVATE
  absl::flags
  absl::flags_parse
  absl::flags_usage
  absl::log
  absl::log_globals
  absl::log_initialize
  absl::strings
  absl::time
  sandbox2::bpf_helper
  sandbox2::sandbox2
  sandbox2::util
  sapi::base
)
