#linux #container


I am currently using nerdctl as drop-in replacement of docker. nerdctl comes as zip in github releases in two flavors: minimal and full. Minimal let you only image pull and push. Full contains containerd, runc, CNI, buildkit etc.

### Installation

`nerdctl` can be installed by extracting the tar file from its github release page.

### Common Issues

1. To build multi-platform images, we need to install emulators. There is a nice image `tonistiigi/binfmt` which install all platforms using:
```shell
docker run --privileged --rm tonistiigi/binfmt --install all
```
2.  To build images, `buildkitd` needs to be running. To run it:

```shell
buildkitd &
```

