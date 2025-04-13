

## Trivy:

`Trivy` is an open-source vulnerability scanner developed by Aqua Security. It helps scan containers, Kubernetes, filesystems, and repositories for security vulnerabilities, misconfigurations, and exposed secrets.

The most famous vulnerability ID is CVE (Common Vulnerability and Exposure). 

The two types of vulnerabilities are known and unknown. In detail, Known Vulnerabilities are the ones that are already found out and assigned CVE ID. Whereas the Unknown Vulnerability is where it is not disclosed yet.

Hence there are two types of scanners, a scanner identifying components with known vulnerabilities. For example `Trivy`, `Clair`, `Aqua`. In addition to that, we also have an unknown vulnerability scanner like `OWASP` `ZAP`, `OSS-Fuzz`.



#### Features of Trivy Scanner:
- Easy installation – `apt`, `yum`, `apk`, `Bundler`, `Composer`, `pipenv`, `Poetry` etc.
- Highly Accurate
- Detect comprehensive vulnerabilities
- Simple – Specify only an image name or artefact name
- Quick – The first scan will finish within 10 seconds (depending on your network). As the consequent scans will finish in single seconds
- DevSecOps – Appropriate for CI such as Jenkins, Travis CI, GitLab CI, etc
- Support multiple formats – Including container image, local filesystem, remote git repository



### RHEL/CentOS:


```
rpm -ivh https://github.com/aquasecurity/trivy/releases/download/v0.20.2/trivy_0.20.2_Linux-64bit.rpm

rpm -ivh https://github.com/aquasecurity/trivy/releases/download/v0.61.0/trivy_0.61.0_Linux-64bit.rpm
```


Or,

```
vim /etc/yum.repos.d/trivy.repo

[trivy]
name=Trivy repository
baseurl=https://aquasecurity.github.io/trivy-repo/rpm/releases/$releasever/$basearch/
gpgcheck=0
enabled=1
```


```
yum -y install trivy
```





### Debian/Ubuntu:


```
sudo apt install -y wget apt-transport-https gnupg lsb-release
```



```
wget https://github.com/aquasecurity/trivy/releases/download/v0.20.2/trivy_0.20.2_Linux-64bit.deb

wget https://github.com/aquasecurity/trivy/releases/download/v0.61.0/trivy_0.61.0_Linux-64bit.deb

dpkg -i trivy_0.20.2_Linux-64bit.deb
```



Or,


```
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
```


```
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
```


```
sudo apt-get update
sudo apt-get install trivy
```


```
trivy -v
```



### Scan vulnerabilities:


#### Scan a Container Image:


_OPTIONS:_

- `--format value`, `-f` value        : format (table, json, template) (default: "table") [$TRIVY_FORMAT]
- `--input` value, `-i` value         : input file path instead of image name [$TRIVY_INPUT]
- `--output` value, `-o` value        : output file name [$TRIVY_OUTPUT]
- `--severity` value, `-s` value      : severities of vulnerabilities to be displayed (comma separated) (default: "UNKNOWN,LOW,MEDIUM,HIGH,CRITICAL") [$TRIVY_SEVERITY]
- `--skip-db-update`, `--skip-update` : skip updating vulnerability database (default: false) [$TRIVY_SKIP_UPDATE, $TRIVY_SKIP_DB_UPDATE]
- `--list-all-pkgs`                   : enabling the option will output all packages regardless of vulnerability (default: false) [$TRIVY_LIST_ALL_PKGS]
- `--skip-files` value                : specify the file paths to skip traversal [$TRIVY_SKIP_FILES]
- `--skip-dirs` value                 : specify the directories where the traversal is skipped [$TRIVY_SKIP_DIRS]
- `--reset`                             : remove all caches and database (default: false) [$TRIVY_RESET]


```
docker pull php:5.6
docker pull nginx:latest
```


_Syntax:_
```
trivy image [options] [IMAGE_NAME]
```


```
trivy image php:5.6
```


_Filter vulnerabilities by severity (LOW, MEDIUM, HIGH, CRITICAL):_

```
trivy image --severity HIGH,CRITICAL php:5.6
trivy image --severity HIGH,CRITICAL php:5.6 | less
```


_Skips updating the vulnerability database before scanning:_

```
trivy image --skip-update nginx:latest
```



_List all installed OS and application packages in an image:_

```
trivy image --list-all-pkgs nginx:latest
```




```
trivy image --format table --output report.txt nginx:latest
trivy image --format json --output report.json nginx:latest
```





#### Scan a Local Filesystem:

- WARN: `--security-checks` is deprecated. Use `--scanners` instead.


```
git clone https://github.com/Saurabh-pec/Calculator-javaProject.git
```



```
trivy fs [OPTIONS] /path/to/directory
```


```
trivy fs javaProject
```


_Scan with High & Critical Vulnerabilities Only:_

```
trivy fs --severity HIGH,CRITICAL javaProject
```



_Scan and Ignore Unfixed Vulnerabilities:_
```
trivy fs --ignore-unfixed javaProject
```


```
trivy fs --security-checks config javaProject
```



```
trivy fs --scanners secret javaProject
```


```
trivy fs --scanners vuln,config,secret javaProject
```



#### Scan a Git Repository:

```
trivy repo https://github.com/Saurabh-pec/Calculator-javaProject.git
```





#### Scan a Kubernetes Cluster:

```
trivy k8s cluster
```




### Links:
- [Trivy Installation](https://aquasecurity.github.io/trivy/v0.20.2/getting-started/installation/)
- [Trivy | github.com](https://github.com/aquasecurity/trivy)
- [Trivy | trivy.dev](https://trivy.dev/latest/getting-started/installation/)
- [Docs | trivy.dev](https://trivy.dev/latest/docs/)



Trivy is a powerful, fast, and easy-to-use security scanner for containers, Kubernetes, and code repositories. Since it supports multiple scan types (vulnerabilities, misconfigurations, and secrets), it's a great choice for DevOps and security teams.


