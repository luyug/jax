load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Force a sufficiently new copy of @platforms, see https://github.com/bazelbuild/bazel/issues/15175 and
# https://github.com/google/jax/issues/10132. When our transitive dependencies aren't pulling in an
# old version, we can remove this (the current hypothesis is that the cause is in TFRT).
http_archive(
    name = "platforms",
    sha256 = "379113459b0feaf6bfbb584a91874c065078aa673222846ac765f86661c27407",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/platforms/releases/download/0.0.5/platforms-0.0.5.tar.gz",
        "https://github.com/bazelbuild/platforms/releases/download/0.0.5/platforms-0.0.5.tar.gz",
    ],
)

# To update TensorFlow to a new revision,
# a) update URL and strip_prefix to the new git commit hash
# b) get the sha256 hash of the commit by running:
#    curl -L https://github.com/tensorflow/tensorflow/archive/<git hash>.tar.gz | sha256sum
#    and update the sha256 with the result.
http_archive(
    name = "org_tensorflow",
    sha256 = "bcd62c1cace55c9892c2c3580355b0c24243bcb6ffd40ec7944126685959bcca",
    strip_prefix = "tensorflow-0dfdb8509be9384a10b71814f429f6e0d10c8a76",
    urls = [
        "https://github.com/tensorflow/tensorflow/archive/0dfdb8509be9384a10b71814f429f6e0d10c8a76.tar.gz",
    ],
)

# For development, one can use a local TF repository instead.
# local_repository(
#    name = "org_tensorflow",
#    path = "tensorflow",
# )

load("//third_party/pocketfft:workspace.bzl", pocketfft = "repo")
pocketfft()

# Initialize TensorFlow's external dependencies.
load("@org_tensorflow//tensorflow:workspace3.bzl", "tf_workspace3")
tf_workspace3()

load("@org_tensorflow//tensorflow:workspace2.bzl", "tf_workspace2")
tf_workspace2()

load("@org_tensorflow//tensorflow:workspace1.bzl", "tf_workspace1")
tf_workspace1()

load("@org_tensorflow//tensorflow:workspace0.bzl", "tf_workspace0")
tf_workspace0()
