load("@rules_pkg//pkg:zip.bzl", "pkg_zip")
load("@rules_pkg//pkg:mappings.bzl", "pkg_files")

pkg_files(
    name = "bin",
    srcs = ["//proxydetox"],
    prefix = "proxydetox/bin",
)

pkg_files(
    name = "install_script",
    srcs = [
        ":install.bat",
    ],
    prefix = "proxydetox",
)

pkg_zip(
    name = "windows",
    srcs = [
        ":bin",
        ":install_script",
    ],
    out = "proxydetox.zip",
    visibility = ["//visibility:public"],
)
