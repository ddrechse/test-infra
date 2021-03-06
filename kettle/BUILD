py_test(
    name = "make_db_test",
    srcs = [
        "make_db.py",
        "make_db_test.py",
        "model.py",
    ],
    # Remove when these are fixed.
    # https://github.com/bazelbuild/bazel/issues/1973
    # https://github.com/bazelbuild/bazel/issues/2056
    local = True,
    deps = [
        "@requests//:requests",
        "@yaml//:yaml",
    ],
)

py_binary(
    name = "make_db",
    srcs = [
        "make_db.py",
        "model.py",
    ],
)

py_test(
    name = "model_test",
    srcs = [
        "model.py",
        "model_test.py",
        ":package-srcs",
    ],
)

py_test(
    name = "stream_test",
    srcs = [
        "stream.py",
        "stream_test.py",
        ":package-srcs",
    ],
    data = ["schema.json"],
    deps = [
        "@requests//:requests",
    ],
)

py_test(
    name = "make_json_test",
    srcs = [
        "make_json.py",
        "make_json_test.py",
        "model.py",
        ":package-srcs",
    ],
    data = ["//:buckets"],
    # idem
    local = True,
    deps = ["@yaml//:yaml"],
)

filegroup(
    name = "package-srcs",
    srcs = glob(
        ["**"],
        exclude = [
            "*.db",
            "*.gz",
        ],
    ),
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
    visibility = ["//visibility:public"],
)
