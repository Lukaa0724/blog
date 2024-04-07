# VSCode中Compilot报错Extension activation failed: "connect ETIMEDOUT 20.205.243.168:443"

[参考](https://github.com/orgs/community/discussions/64334)，其中指出需要修改本地的host文件，添加
```shell
140.82.112.25 alive.github.com
140.82.114.6 api.github.com
185.199.110.153 assets-cdn.github.com
140.82.113.22 central.github.com
185.199.108.133 cloud.githubusercontent.com
140.82.113.9 codeload.github.com
140.82.112.22 collector.github.com
140.82.112.4 gist.github.com
52.216.146.155 github-cloud.s3.amazonaws.com
52.217.204.137 github-com.s3.amazonaws.com
54.231.163.81 github-production-release-asset-2e65be.s3.amazonaws.com
52.217.44.156 github-production-repository-file-5c1aeb.s3.amazonaws.com
52.216.54.145 github-production-user-asset-6210df.s3.amazonaws.com
192.0.66.2 github.blog
140.82.112.4 github.com
140.82.114.17 github.community
185.199.109.154 github.githubassets.com
151.101.65.194 github.global.ssl.fastly.net
185.199.110.153 github.io
185.199.110.153 githubstatus.com
140.82.112.25 live.github.com
13.107.43.16 pipelines.actions.githubusercontent.com
13.107.238.40 vscode.dev
```

通过win+R快捷键，输入`C:\Windows\System32\drivers\etc`，添加到hosts文件中即可