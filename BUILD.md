# Build

See ./Build.sh

```bash
AL_TAG=2
DOCKER_BUILD_FLAGS=--no-cache
FLB_VERSION=1.9.10
FLB_REPOSITORY=https://github.com/udhos/upstream-to-fluent-bit.git
FLB_VERSION=1.9.10_log_group_class

docker build $(DOCKER_BUILD_FLAGS) --build-arg AL_TAG=${AL_TAG} --build-arg FLB_VERSION=${FLB_VERSION} --build-arg FLB_REPOSITORY=${FLB_REPOSITORY} -t amazon/aws-for-fluent-bit:build-common-al${AL_TAG} -f ./dockerfiles/Dockerfile.build-common .

docker build $(DOCKER_BUILD_FLAGS) --build-arg BUILD_IMAGE=amazon/aws-for-fluent-bit:build-common-al${AL_TAG} -t amazon/aws-for-fluent-bit:compile-al${AL_TAG} -f ./dockerfiles/Dockerfile.compile .
```

Get fluent-bit binary

```bash
$ docker run -v $PWD:/pwd --rm -ti docker.io/amazon/aws-for-fluent-bit:compile-al2 sh
sh-4.2# cp /fluent-bit/bin/fluent-bit /pwd
sh-4.2# 
sh-4.2# 
sh-4.2# exit
exit
$ 
$ gzip fluent-bit
```
