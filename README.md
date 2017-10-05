Usage example:

apt update; apt install --no-install-recommends fai-server
fai-setup-storage qemu-utils procps img2simg
git clone http://git.linaro.org/ci/fai.git
fai-diskimage -v --cspace $PATH/fai  --hostname test -S 3G --class SID,DEBIAN,LINARO,DEVELOPER,QCOM,DB410C,RAW linaro.raw 2>&1|tee fai.log
img2simg linaro.raw linaro.img

Gotchas:
- order of classes matter - latter classes override variables from earlier ones
- missing packages in packages from package\_lists and errors while installing packages will not error the build out
