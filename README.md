Usage example on arm64 host:

sudo modprobe loop
docker run --privileged  -v $(pwd):/work --rm -it linaro/arm64-fai  /bin/bash
cd /work
git clone http://git.linaro.org/ci/fai.git
fai-diskimage -v --cspace $(pwd)/fai  --hostname linaro-test -S 3G --class BUSTER,DEBIAN,DEVELOPER,LINARO,QCOM,DB410C,RAW linaro.raw 2>&1|tee fai.log

Gotchas:
- loop devices need to exist before starting docker
- order of classes matter - latter classes override variables from earlier ones
- missing packages in packages from package\_lists and errors while installing packages will not error the build out
  - grep the log for warnings and erros before proceeding
