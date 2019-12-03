# Description:
#   Build rule for Python and Numpy.
#   This rule works for Debian and Ubuntu. Other platforms might keep the
#   headers in different places, cf. 'How to build DeepMind Lab' in build.md.

cc_library(
    name = "python",
    hdrs = select(
        {
            "@bazel_tools//tools/python:PY2": glob(["local/lib/python2.7/dist-packages/numpy/core/include/**/*.h"]),
            "@bazel_tools//tools/python:PY3": glob(["include/python3.6/dist-packages/numpy/core/include/**/*.h"]),
        },
        no_match_error = "Internal error, Python version should be one of PY2 or PY3",
    ),
    includes = select(
        {
            "@bazel_tools//tools/python:PY2": ["local/lib/python2.7/dist-packages/numpy/core/include"],
            "@bazel_tools//tools/python:PY3": ["include/python3.6/dist-packages/numpy/core/include"],
        },
        no_match_error = "Internal error, Python version should be one of PY2 or PY3",
    ),
    visibility = ["//visibility:public"],
)

alias(
    name = "python_headers",
    actual = ":python",
    visibility = ["//visibility:public"],
)
