# Parquet benchmark data

This repository contains Parquet benchmark data. Such data is useful to help
optimize Parquet implementations but also advance the Parquet format itself.

At this point the community requests donation of Parquet footers and especially
footers that are large and slow to parse/process. Typically these are footers of
wide schemata: either coming from lots of individual columns and/or deeply nested
structs.

To donate Parquet footers we have built a binary `parquet-dump-footer` as part
of parquet tools. This utility extracts footers from parquet, scrubs binary data
for privacy reasons and allows to pretty print (`--debug`) the result for
inspection before submission.

When you are ready to donate a footer please open a PR against this repository
and add your footer under `footer/<name>.footer`.

Use `parquet-dump-footer --help` for explantion of all the options.

## alternate parquet-dump-footer binary

You can binaries in this repo for different architectures. The binaries are built
using the following cmake configuration.

```sh
cmake .. -DCMAKE_BUILD_TYPE=Release -DARROW_ACERO=OFF -DARROW_BUILD_UTILITIES=OFF -DARROW_COMPUTE=OFF -DARROW_CSV=OFF -DARROW_DATASET=OFF -DARROW_FILESYSTEM=ON -DARROW_AZURE=ON -DARROW_HDFS=OFF -DARROW_GCS=ON -DARROW_IPC=OFF -DARROW_PARQUET=ON -DARROW_S3=ON -DARROW_JSON=OFF -DARROW_MIMALLOC=OFF -DARROW_JEMALLOC=OFF -DARROW_SUBSTRAIT=OFF -DARROW_DEPENDENCY_SOURCE=BUNDLED -DARROW_DEPENDENCY_USE_SHARED=OFF -DARROW_BUILD_STATIC=ON -DARROW_BUILD_SHARED=OFF -DPARQUET_BUILD_EXECUTABLES=ON
```
