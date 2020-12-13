




In /Users/jinhuan/code/rules_gitops/skylib/k8s.bzl

the kustomize step include kustomize + resolver

```bash

#!/bin/bash
set -euo pipefail

bazel-out/host/bin/external/kustomize_bin/kustomize build --load_restrictor none --reorder legacy bazel-out/darwin-fastbuild/bin/helloworld/mynamespace | \

bazel-out/host/bin/external/com_adobe_rules_gitops/templating/fast_template_engine_/fast_template_engine --stamp_info_file=bazel-out/darwin-fastbuild/bin/external/com_adobe_rules_gitops/skylib/more_stable_status.txt --variable=CLUSTER=ethos51devva6 --start_tag={{ --end_tag=}}     | \

bazel-out/host/bin/external/com_adobe_rules_gitops/resolver/resolver_/resolver  --image //helloworld:image=docker-adcloud-release.dr-uw2.adobeitc.com/$(cat bazel-out/darwin-fastbuild/bin/external/com_adobe_rules_gitops/skylib/build_user_value.txt)/helloworld/image@$(cat bazel-out/darwin-fastbuild/bin/helloworld/image.digest) --image helloworld-image=docker-adcloud-release.dr-uw2.adobeitc.com/$(cat bazel-out/darwin-fastbuild/bin/external/com_adobe_rules_gitops/skylib/build_user_value.txt)/helloworld/image@$(cat bazel-out/darwin-fastbuild/bin/helloworld/image.digest) \

>bazel-out/darwin-fastbuild/bin/helloworld/mynamespace.yaml
```

# manual
1. create the transformer file and test this

2. remove resolver