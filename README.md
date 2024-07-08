Bazel silently refuses to copy over folders starting with `bazel-` into the sandbox and it will fail at runtime despite the analysis phase going fine 

```
➜  bazel-repro git:(main) ✗ bazel build bazel-lol
INFO: Analyzed target //bazel-lol:bazel-lol (0 packages loaded, 0 targets configured).
ERROR: /home/andrzej.gluszak/code/jetbrains/bazel-repro/bazel-lol/BUILD:1:13: Building bazel-lol/libbazel-lol.jar (1 source file) failed: (Exit 1): java failed: error executing Javac command (from target //bazel-lol:bazel-lol) external/rules_java~~toolchains~remotejdk21_linux/bin/java '--add-exports=jdk.compiler/com.sun.tools.javac.api=ALL-UNNAMED' '--add-exports=jdk.compiler/com.sun.tools.javac.main=ALL-UNNAMED' ... (remaining 19 arguments skipped)
warning: [options] source value 8 is obsolete and will be removed in a future release
warning: [options] target value 8 is obsolete and will be removed in a future release
warning: [options] To suppress warnings about obsolete options, use -Xlint:-options.
error: error reading bazel-lol/Lol.java; /home/andrzej.gluszak/.cache/bazel/_bazel_andrzej.gluszak/2d69bae751473fd5c42ccfa8d7541a9d/execroot/_main/bazel-lol/Lol.java
Target //bazel-lol:bazel-lol failed to build
Use --verbose_failures to see the command lines of failed build steps.
INFO: Elapsed time: 0.263s, Critical Path: 0.03s
INFO: 2 processes: 2 internal.
ERROR: Build did NOT complete successfully
```
