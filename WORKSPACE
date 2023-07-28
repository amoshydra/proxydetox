workspace(name = "proxydetox")

load("@//bazel:http.bzl", "versioned_http_archive")

versioned_http_archive(
    name = "platforms",
    sha256 = "5308fc1d8865406a49427ba24a9ab53087f17f5266a7aabbfc28823f3916e1ca",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/platforms/releases/download/{version}/platforms-{version}.tar.gz",
        "https://github.com/bazelbuild/platforms/releases/download/{version}/platforms-{version}.tar.gz",
    ],
    version = "0.0.6",
)

versioned_http_archive(
    name = "build_bazel_rules_apple",
    sha256 = "8ac4c7997d863f3c4347ba996e831b5ec8f7af885ee8d4fe36f1c3c8f0092b2c",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_apple/releases/download/{version}/rules_apple.{version}.tar.gz",
        "https://github.com/bazelbuild/rules_apple/releases/download/{version}/rules_apple.{version}.tar.gz",
    ],
    version = "2.5.0",
)

versioned_http_archive(
    name = "build_bazel_apple_support",
    sha256 = "34bab0182c33ef595015eb0e66518ef09b367a7841cdba997c6c01843b62f753",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/apple_support/releases/download/{version}/apple_support.{version}.tar.gz",
        "https://github.com/bazelbuild/apple_support/releases/download/{version}/apple_support.{version}.tar.gz",
    ],
    version = "1.8.0",
)

versioned_http_archive(
    name = "build_bazel_rules_swift",
    sha256 = "b3b6c5c9f2a589150f71e79dec1e1ed0eb974dbd49e9317df4e09e08ff6e83df",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_swift/releases/download/{version}/rules_swift.{version}.tar.gz",
        "https://github.com/bazelbuild/rules_swift/releases/download/{version}/rules_swift.{version}.tar.gz",
    ],
    version = "1.9.1",
)

load(
    "@build_bazel_apple_support//lib:repositories.bzl",
    "apple_support_dependencies",
)

apple_support_dependencies()

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

versioned_http_archive(
    name = "rules_rust",
    sha256 = "4a9cb4fda6ccd5b5ec393b2e944822a62e050c7c06f1ea41607f14c4fdec57a2",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_rust/releases/download/{version}/rules_rust-v{version}.tar.gz",
        "https://github.com/bazelbuild/rules_rust/releases/download/{version}/rules_rust-v{version}.tar.gz",
    ],
    version = "0.25.1",
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    extra_target_triples = [
        "aarch64-apple-darwin",
        "x86_64-apple-darwin",
    ],
)

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")

crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crate", "crates_repository")

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
        "//spnego:Cargo.toml",
    ],
)

load("@crate_index//:defs.bzl", "crate_repositories")

crate_repositories()

crates_repository(
    name = "crate_index_tools",
    cargo_lockfile = "//:Cargo.tools.lock",
    # Generate with:
    # CARGO_BAZEL_REPIN=1 bazel sync --only=crate_index_tools
    lockfile = "//:Cargo.Bazel.tools.lock",
    packages = {"toml": crate.spec(version = "0.7.6")},
)

load("@crate_index_tools//:defs.bzl", crate_repositories_tools = "crate_repositories")

crate_repositories_tools()

load("@rules_rust//bindgen:repositories.bzl", "rust_bindgen_dependencies", "rust_bindgen_register_toolchains")

rust_bindgen_dependencies()

rust_bindgen_register_toolchains()

load("@rules_rust//bindgen:transitive_repositories.bzl", "rust_bindgen_transitive_dependencies")

rust_bindgen_transitive_dependencies()

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
