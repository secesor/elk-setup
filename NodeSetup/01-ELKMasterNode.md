# First steps
- Update your system:
  ```
  sudo yum update
  ```

# Docker installation
For OracleLinux7 follow [this guide](https://blogs.oracle.com/virtualization/post/install-docker-on-oracle-linux-7).

For OracleLinux8 follow [this guide](https://www.how2shout.com/linux/how-to-install-docker-ce-on-oracle-linux-8-7/).

## Steps for OracleLinux8
Install yum-utils, which provides yum-config-manager tool:
```
sudo yum install -y yum-utils
```

Add official Docker repository:
```
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Run system update:
```
sudo yum update
```

Install docker and containerd:
```
sudo yum install docker-ce docker-ce-cli containerd.io
```

Check docker installation:
```
docker --version
```
Sample output:
```
Docker version 20.10.17, build 100c701
```

Start docker daemon:
```
sudo systemctl start docker
```

Check docker status:
```
sudo systemctl status docker
```

Configure docker daemon to startup on system boot:
```
sudo systemctl enable docker
```

In order to execute docker commands without `sudo` you should add your user to docker group:
```
sudo usermod -aG docker
```

## Troubleshooting

### Kernel does not support ...
I started docker daemon and when I checked daemon status I noticed the following warning:
> warning msg="Your kernel does not support cgroup blkio weight_device"

After googling it for a while, conclusion is that I should not worry unless it's a production environment, which is not my case.

It seems, anyway, that cgroup feature was [deprecated from Linux Kernel](https://github.com/docker/cli/pull/2908).
Running `uname -a` on my system would yield:
> Linux instance-20220224-0144 5.4.17-2136.302.7.2.1.el8uek.aarch64 #2 SMP Tue Jan 18 12:11:39 PST 2022 aarch64 aarch64 aarch64 GNU/Linux

### Not using native diff for overlay2

I started docker daemon and when I checked daemon status I noticed the following warning:
> warning msg="Not using native diff for overlay2, this may cause degraded performance for building images"

I was able to make the warning go away following the instructions in [this guide](https://mikeshade.com/posts/docker-native-overlay-diff/):
```
sudo systemctl stop docker
sudo modprobe -r overlay
sudo modprobe overlay
sudo systemctl start docker
```