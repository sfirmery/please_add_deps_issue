def _add_exported_deps(name, output):
    for line in output:
        add_exported_dep(name, line)

def _add_deps(name, output):
    for line in output:
        add_dep(name, line)


build_rule(
    name = "add_deps",
    cmd = "for i in {1..10}; do echo \"//third_party/dep_${i}:dep_${i}\"; done",
    srcs = ["deps"],
    # post_build = _add_deps
    post_build = _add_exported_deps
)

build_rule(
    name = "use_exported_deps",
    outs = ["all_deps"],
    deps = [":add_deps"],
    cmd = "find . -mindepth 2 | sort -n >> $OUTS",
)
