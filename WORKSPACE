load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

http_archive(
    name = "rules_proto",
    sha256 = "602e7161d9195e50246177e7c55b2f39950a9cf7366f74ed5f22fd45750cd208",
    strip_prefix = "rules_proto-97d8af4dc474595af3900dd85cb3a29ad28cc313",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/97d8af4dc474595af3900dd85cb3a29ad28cc313.tar.gz",
        "https://github.com/bazelbuild/rules_proto/archive/97d8af4dc474595af3900dd85cb3a29ad28cc313.tar.gz",
    ],
)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

RULES_JVM_EXTERNAL_TAG = "3.3"

RULES_JVM_EXTERNAL_SHA = "d85951a92c0908c80bd8551002d66cb23c3434409c814179c0ff026b53544dab"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "org.http4k:http4k-core:3.278.0",
        "org.http4k:http4k-client-okhttp:3.278.0",
        "org.http4k:http4k-cloudnative:3.278.0",
        "org.http4k:http4k-contract:3.278.0",
        "org.http4k:http4k-format-jackson:3.278.0",
        "org.http4k:http4k-security-oauth:3.278.0",
        "org.http4k:http4k-server-undertow:3.278.0",
        "org.http4k:http4k-template-handlebars:3.278.0",
        "org.junit.jupiter:junit-jupiter-api:5.7.0",
        "org.junit.jupiter:junit-jupiter-engine:5.7.0",
        "org.http4k:http4k-testing-hamkrest:3.278.0",
        "org.http4k:http4k-testing-chaos:3.278.0",
        "org.http4k:http4k-testing-approval:3.278.0",
        "org.http4k:http4k-testing-webdriver:3.278.0",
    ],
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

git_repository(
    name = "io_bazel_rules_kotlin",
    commit = "69159daf2b49746706e2497e2fd272afe8a9afee",
    remote = "https://github.com/bazelbuild/rules_kotlin.git",
)

load("@io_bazel_rules_kotlin//kotlin:dependencies.bzl", "kt_download_local_dev_dependencies")

kt_download_local_dev_dependencies()

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories")

KOTLIN_VERSION = "1.4.20"

KOTLINC_RELEASE_SHA = "11db93a4d6789e3406c7f60b9f267eba26d6483dcd771eff9f85bb7e9837011f"

KOTLINC_RELEASE = {
    "urls": [
        "https://github.com/JetBrains/kotlin/releases/download/v{v}/kotlin-compiler-{v}.zip".format(v = KOTLIN_VERSION),
    ],
    "sha256": KOTLINC_RELEASE_SHA,
}

kt_download_local_dev_dependencies()

kotlin_repositories(compiler_release = KOTLINC_RELEASE)

register_toolchains("//:kotlin_toolchain")
