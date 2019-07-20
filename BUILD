
cc_library(
    name = "skia_h",
    visibility = ["//visibility:public"],
    
    includes = [ "." ],
    hdrs = glob(["**/*.h"]),
)

cc_import(
    name = "skia_bin",
    visibility = ["//visibility:public"],

    static_library = select({
        "@bazel_tools//src/conditions:windows": "skia_static.lib",
        "@bazel_tools//src/conditions:darwin_x86_64": "macos/libskia.a",
        "//conditions:default": "libskia.a",
    }),
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
        "@bazel_tools//src/conditions:darwin_x86_64": [
            "-framework CoreText",
            "-framework CoreServices",
            "-framework CoreGraphics"
        ],
        "//conditions:default": [
            "-lGL",
            "-lz",
            "-lpng",
            "-ljpeg",
            "-lwebp",
            "-lwebpmux",
            "-lwebpdemux",
            "-lfreetype",
            "-lfontconfig",
        ],
    }),
)
