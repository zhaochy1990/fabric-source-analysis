系统容器的一些方法
inproccontroller: in process controller
### package inproccontroller
inproccontroller.go在加载的时候定义了一些变量
```golang
typeRegistry        = make(map[string]*inprocContainer)
instRegistry        = make(map[string]*inprocContainer)
```
和一些方法
```golang
func Register(path string, cc shim.Chaincode) error
```
Register在typeRegistry中查找path对应的cc，如果有，说明这个cc已经注册过了，如果没有，则新建一个inprocContainer，并将该path与对应的inprocContainer存在typeRegistry中


```golang
// inprocContainer
type inprocContainer struct {
	chaincode shim.Chaincode
	running   bool
	args      []string
	env       []string
	stopChan  chan struct{}
}
```


