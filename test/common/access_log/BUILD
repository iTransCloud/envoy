licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_library",
    "envoy_cc_test",
    "envoy_package",
)

envoy_package()

envoy_cc_library(
    name = "test_util",
    hdrs = ["test_util.h"],
    deps = [],
)

envoy_cc_test(
    name = "access_log_formatter_test",
    srcs = ["access_log_formatter_test.cc"],
    deps = [
        "//source/common/access_log:access_log_formatter_lib",
        "//source/common/common:utility_lib",
        "//source/common/http:header_map_lib",
        "//test/mocks/http:http_mocks",
        "//test/mocks/request_info:request_info_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "access_log_impl_test",
    srcs = ["access_log_impl_test.cc"],
    deps = [
        ":test_util",
        "//source/common/access_log:access_log_lib",
        "//source/common/config:filter_json_lib",
        "//source/extensions/access_loggers/file:config",
        "//test/common/upstream:utility_lib",
        "//test/mocks/access_log:access_log_mocks",
        "//test/mocks/event:event_mocks",
        "//test/mocks/filesystem:filesystem_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/server:server_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "access_log_manager_impl_test",
    srcs = ["access_log_manager_impl_test.cc"],
    deps = [
        "//source/common/access_log:access_log_manager_lib",
        "//source/common/stats:stats_lib",
        "//test/mocks/access_log:access_log_mocks",
        "//test/mocks/api:api_mocks",
        "//test/mocks/event:event_mocks",
        "//test/mocks/filesystem:filesystem_mocks",
    ],
)

envoy_cc_binary(
    name = "access_log_formatter_speed_test",
    testonly = 1,
    srcs = ["access_log_formatter_speed_test.cc"],
    external_deps = [
        "benchmark",
    ],
    deps = [
        ":test_util",
        "//source/common/access_log:access_log_formatter_lib",
        "//source/common/http:header_map_lib",
        "//source/common/network:address_lib",
        "//test/mocks/http:http_mocks",
        "//test/mocks/request_info:request_info_mocks",
        "//test/test_common:printers_lib",
    ],
)
