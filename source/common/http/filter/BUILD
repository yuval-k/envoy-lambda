licenses(["notice"])  # Apache 2

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_library",
    "envoy_cc_test",
    "envoy_package",
)

envoy_package()

load("@envoy_api//bazel:api_build_system.bzl", "api_proto_library")

envoy_cc_library(
    name = "aws_authenticator_lib",
    srcs = ["aws_authenticator.cc"],
    hdrs = ["aws_authenticator.h"],
    repository = "@envoy",
    deps = [
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_library(
    name = "lambda_filter_config",
    hdrs = [
        "lambda_filter_config.h",
    ],
    repository = "@envoy",
    deps = [
        "//:lambda_filter_proto_cc",
        "//source/common/config:lambda_well_known_names_lib",
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_library(
    name = "function_retriever_lib",
    srcs = [
        "function.cc",
        "metadata_function_retriever.cc",
    ],
    hdrs = [
        "function.h",
        "function_retriever.h",
        "metadata_function_retriever.h",
    ],
    repository = "@envoy",
    deps = [
        "//source/common/config:lambda_well_known_names_lib",
        "@solo_envoy_common//include/envoy/http:metadata_accessor_interface",
        "@solo_envoy_common//source/common/http:solo_filter_utility_lib",
    ],
)

envoy_cc_library(
    name = "lambda_filter_lib",
    srcs = [
        "lambda_filter.cc",
    ],
    hdrs = [
        "lambda_filter.h",
    ],
    repository = "@envoy",
    deps = [
        "//source/common/http/filter:aws_authenticator_lib",
        "//source/common/http/filter:function_retriever_lib",
        "//source/common/http/filter:lambda_filter_config",
        "@envoy//source/exe:envoy_common_lib",
        "@solo_envoy_common//include/envoy/http:metadata_accessor_interface",
        "@solo_envoy_common//source/common/http:solo_filter_utility_lib",
    ],
)
