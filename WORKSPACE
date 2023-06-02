workspace(name = "proxydetox")

load("@//bazel:http.bzl", "versioned_http_archive")

# https://github.com/bazelbuild/rules_apple/releases
versioned_http_archive(
    name = "build_bazel_rules_apple",
    sha256 = "a6141240657093fa7ccc7ca1ee5a62408dd9996d1bf47bc2369b8b9faefb2698",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_apple/releases/download/{version}/rules_apple.{version}.tar.gz",
        "https://github.com/bazelbuild/rules_apple/releases/download/{version}/rules_apple.{version}.tar.gz",
    ],
    version = "2.3.0",
)

load(
    "@build_bazel_rules_apple//apple:repositories.bzl",
    "apple_rules_dependencies",
)

apple_rules_dependencies()

load(
    "@build_bazel_rules_swift//swift:repositories.bzl",
    "swift_rules_dependencies",
)

swift_rules_dependencies()

load(
    "@build_bazel_rules_swift//swift:extras.bzl",
    "swift_rules_extra_dependencies",
)

swift_rules_extra_dependencies()

load(
    "@build_bazel_apple_support//lib:repositories.bzl",
    "apple_support_dependencies",
)

apple_support_dependencies()

# https://github.com/bazelbuild/rules_rust/releases
versioned_http_archive(
    name = "rules_rust",
    sha256 = "50272c39f20a3a3507cb56dcb5c3b348bda697a7d868708449e2fa6fb893444c",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_rust/releases/download/{version}/rules_rust-v{version}.tar.gz",
        "https://github.com/bazelbuild/rules_rust/releases/download/{version}/rules_rust-v{version}.tar.gz",
    ],
    version = "0.22.0",
)

load("@rules_rust//rust:repositories.bzl", "rust_repositories")

rust_repositories(
    edition = "2021",
    # version = "1.67.0",
)

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")

crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")

crates_repository(
    name = "crate_index",
    cargo_config = "//:.cargo/config.toml",
    cargo_lockfile = "//:Cargo.lock",
    # Generate with:
    # CARGO_BAZEL_REPIN=1 bazel sync --only=crate_index
    lockfile = "//:Cargo.Bazel.lock",
    manifests = [
        "//:Cargo.toml",
        "//detox_net:Cargo.toml",
        "//dnsdetox:Cargo.toml",
        "//paceval:Cargo.toml",
        "//paclib:Cargo.toml",
        "//proxy_client:Cargo.toml",
        "//proxydetox:Cargo.toml",
        "//proxydetoxlib:Cargo.toml",
    ],
)

load("@crate_index//:defs.bzl", "crate_repositories")

crate_repositories()

load("@rules_rust//bindgen:repositories.bzl", "rust_bindgen_repositories")

rust_bindgen_repositories()

# https://github.com/bazelbuild/rules_pkg/releases
versioned_http_archive(
    name = "rules_pkg",
    sha256 = "8f9ee2dc10c1ae514ee599a8b42ed99fa262b757058f65ad3c384289ff70c4b8",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/{version}/rules_pkg-{version}.tar.gz",
        "https://github.com/bazelbuild/rules_pkg/releases/download/{version}/rules_pkg-{version}.tar.gz",
    ],
    version = "0.9.1",
)

load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")

rules_pkg_dependencies()
