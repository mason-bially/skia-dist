
cc_library(
    name = "skia_h",
    visibility = ["//visibility:public"],
    
    includes = [ "." ],
    hdrs = glob(["*.h"]),
)

cc_import(
    name = "skia_bin",
    visibility = ["//visibility:public"],

    static_library = "skia_static.lib",
    interface_library = "skia.lib",
    shared_library = "skia.dll",
)

cc_library(
    name = "skia",
    visibility = ["//visibility:public"],

    deps = [
        ":skia_bin",
        ":skia_h",
    ],

    linkopts = [ ] + select({
        "@bazel_tools//src/conditions:windows": [
            "-DEFAULTLIB:Opengl32.lib"
        ],
        "//conditions:default": [],
    }),
)