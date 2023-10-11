# Copyright 2019 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

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
# Based on Google's Sandboxed API, Apache-2.0 license (https://github.com/google/sandboxed-api/blob/main/LICENSE)

project(NativeModuleSandboxer C CXX ASM)

cmake_minimum_required(VERSION 3.16)

if(COMMAND cmake_policy)
  cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

add_subdirectory(sandboxed-api)

add_executable(native-module-sandboxer
  native-module-sandboxer.cc
)
set_target_properties(native-module-sandboxer PROPERTIES OUTPUT_NAME native-module-sandboxer)
target_link_libraries(native-module-sandboxer PRIVATE
  absl::flags_parse
  absl::flags_usage
  absl::log_initialize
  sandbox2::sandbox2
)
