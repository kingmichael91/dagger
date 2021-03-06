# Copyright (C) 2019 The Dagger Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Description:
#   Internal code for implementing Hilt processors.

package(default_visibility = ["//:src"])

java_library(
    name = "base_processor",
    srcs = [
        "BaseProcessor.java",
        "ProcessorErrorHandler.java",
    ],
    deps = [
        ":processor_errors",
        ":processors",
        "//java/dagger/internal/guava:base",
        "//java/dagger/internal/guava:collect",
        "@google_bazel_common//third_party/java/auto:common",
        "@google_bazel_common//third_party/java/auto:value",
        "@google_bazel_common//third_party/java/javapoet",
    ],
)

java_library(
    name = "processor_errors",
    srcs = [
        "BadInputException.java",
        "ErrorTypeException.java",
        "ProcessorErrors.java",
    ],
    deps = [
        "//java/dagger/internal/guava:base",
        "//java/dagger/internal/guava:collect",
        "@google_bazel_common//third_party/java/auto:common",
        "@google_bazel_common//third_party/java/error_prone:annotations",
        "@google_bazel_common//third_party/java/jsr305_annotations",
    ],
)

java_library(
    name = "processors",
    srcs = [
        "AnnotationValues.java",
        "KotlinMetadata.java",
        "Processors.java",
    ],
    deps = [
        ":classnames",
        ":processor_errors",
        "//java/dagger/internal/codegen/extension",
        "//java/dagger/internal/guava:base",
        "//java/dagger/internal/guava:collect",
        "@google_bazel_common//third_party/java/auto:common",
        "@google_bazel_common//third_party/java/javapoet",
        "@maven//:org_jetbrains_kotlin_kotlin_stdlib",
        "@maven//:org_jetbrains_kotlinx_kotlinx_metadata_jvm",
    ],
)

java_library(
    name = "classnames",
    srcs = [
        "ClassNames.java",
    ],
    deps = [
        "@google_bazel_common//third_party/java/javapoet",
    ],
)

java_library(
    name = "component_names",
    srcs = [
        "ComponentNames.java",
    ],
    deps = [
        ":processors",
        "//java/dagger/internal/guava:annotations",
        "@google_bazel_common//third_party/java/javapoet",
    ],
)

java_library(
    name = "component_descriptor",
    srcs = [
        "ComponentDescriptor.java",
        "ComponentGenerator.java",
        "ComponentTree.java",
    ],
    deps = [
        ":classnames",
        ":processors",
        "//java/dagger/internal/codegen/extension",
        "//java/dagger/internal/guava:base",
        "//java/dagger/internal/guava:collect",
        "//java/dagger/internal/guava:graph",
        "@google_bazel_common//third_party/java/auto:value",
        "@google_bazel_common//third_party/java/javapoet",
    ],
)

java_library(
    name = "components",
    srcs = [
        "Components.java",
    ],
    deps = [
        ":classnames",
        ":component_descriptor",
        ":processor_errors",
        ":processors",
        "//java/dagger/hilt/processor/internal/definecomponent:define_components",
        "//java/dagger/internal/codegen/extension",
        "//java/dagger/internal/guava:base",
        "//java/dagger/internal/guava:collect",
        "@google_bazel_common//third_party/java/javapoet",
    ],
)
