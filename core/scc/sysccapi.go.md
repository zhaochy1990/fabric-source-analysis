这个文件定义了SystemChaincode这个类，提供了一些通用方法

```golang
// SystemChaincode defines the metadata needed to initialize system chaincode
// when the fabric comes up. SystemChaincodes are installed by adding an
// entry in importsysccs.go
type SystemChaincode struct {
	//Unique name of the system chaincode
	Name string

	//Path to the system chaincode; currently not used
	Path string

	//InitArgs initialization arguments to startup the system chaincode
	InitArgs [][]byte

	// Chaincode is the actual chaincode object
	Chaincode shim.Chaincode

	// InvokableExternal keeps track of whether
	// this system chaincode can be invoked
	// through a proposal sent to this peer
	InvokableExternal bool

	// InvokableCC2CC keeps track of whether
	// this system chaincode can be invoked
	// by way of a chaincode-to-chaincode
	// invocation
	InvokableCC2CC bool

	// Enabled a convenient switch to enable/disable system chaincode without
	// having to remove entry from importsysccs.go
	Enabled bool
}
```

SystemChaincode有如下方法
```golang
// 注册System Chaincode
// 调用inproccontroller的Register方法
func registerSysCC(syscc *SystemChaincode) (bool, error)
```
