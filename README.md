# KINE

Fix the vgo error for [github.com/ibuildthecloud/kine](https://github.com/ibuildthecloud/kine) at [PR#5](https://github.com/ibuildthecloud/kine/pull/5):

```bash
build command-line-arguments: cannot load github.com/rancher/kine/pkg/tls: git ls-remote -q https://github.com/rancher/kine exit status 128:
	remote: Repository not found.
	fatal: repository 'https://github.com/rancher/kine/' not found
```

> Note: It's imported as github.com/rancher/kine, but this repository is removed.

## Usage

**Step 1:** Write code imported `github.com/rancher/kine`

```go
package main

import "github.com/rancher/kine/pkg/tls"

func main() {
	_ = &tls.Config{}
}
```

**Step 2:** Init with Go Modules

```bash
go mod init private.me
```

> Remark: Please use your package URL.

**Step 3:** Replace by `github.com/winlinvip/kine`

```bash
go mod edit -replace=github.com/rancher/kine=github.com/winlinvip/kine@v0.2.0
```

**Step 4:** Run or test it

```bash
go test ./...
```
