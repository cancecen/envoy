load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_extension",
    "envoy_cc_library",
    "envoy_extension_package",
)

licenses(["notice"])  # Apache 2

envoy_extension_package()

envoy_cc_library(
    name = "thrift_to_metadata_lib",
    srcs = ["filter.cc"],
    hdrs = ["filter.h"],
    deps = [
        "//envoy/server:filter_config_interface",
        "//source/common/http:header_utility_lib",
        "//source/extensions/filters/http/common:pass_through_filter_lib",
        "//source/extensions/filters/network/thrift_proxy:auto_protocol_lib",
        "//source/extensions/filters/network/thrift_proxy:auto_transport_lib",
        "//source/extensions/filters/network/thrift_proxy:decoder_lib",
        "//source/extensions/filters/network/thrift_proxy:passthrough_decoder_event_handler_lib",
        "//source/extensions/filters/network/thrift_proxy:thrift_lib",
        "@envoy_api//envoy/extensions/filters/http/thrift_to_metadata/v3:pkg_cc_proto",
    ],
)

envoy_cc_extension(
    name = "config",
    srcs = ["config.cc"],
    hdrs = ["config.h"],
    deps = [
        ":thrift_to_metadata_lib",
        "//envoy/registry",
        "//source/extensions/filters/http/common:factory_base_lib",
        "@envoy_api//envoy/extensions/filters/http/thrift_to_metadata/v3:pkg_cc_proto",
    ],
)
