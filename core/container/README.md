#### Container
容器相关操作，目前仅仅支持Docker。
对于system chaincode，使用系统容器运行。
```golang
//supported containers
const (
	DOCKER = "Docker"
	SYSTEM = "System"
)
```

容器操作
- start with build
- start
- stop
