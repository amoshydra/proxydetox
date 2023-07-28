load("@rules_pkg//pkg:zip.bzl", "pkg_zip")
load("@rules_pkg//pkg:mappings.bzl", "pkg_files")

pkg_files(
    name = "bin",
    srcs = ["//proxydetox"],
    prefix = "proxydetox/bin",
)

pkg_zip(
    name = "zip",
    srcs = [
        ":bin",
    ],
    out = "proxydetox.zip",
    visibility = ["//visibility:public"],
)
