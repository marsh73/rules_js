workspace(
    name = "cra-workspace",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "aspect_rules_js",
    sha256 = "b9fde0f20de6324ad443500ae738bda00facbd73900a12b417ce794856e01407",
    strip_prefix = "rules_js-1.5.0",
    url = "https://github.com/aspect-build/rules_js/archive/refs/tags/v1.5.0.tar.gz",
)

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@rules_nodejs//nodejs:repositories.bzl", "DEFAULT_NODE_VERSION", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = DEFAULT_NODE_VERSION,
)

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//cra:pnpm-lock.yaml",
    public_hoist_packages = {
        "jest-watch-typeahead": [""],
        "eslint": [""],
    },
    verify_node_modules_ignored = "//cra:.bazelignore",
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()
