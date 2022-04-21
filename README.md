# 模板获取和原理
- 获取全部模板文件到指定文件夹
`goctl template init -home {dir}`
- 获取指定模板到指定目录,粒度为文件夹级别
`goctl template update -c {category}  -home {dir}`
- 基本原理:
通过变量替换,来生成文件

# 模板修改
  本仓库主要是对go-zero的模板进行了定制了,具体改动如下:
- 对handler文件的返回值进行了修改
- 在types文件中增加了Response的类型定义
```go
type Response struct {
	RetCode    int         `json:"ret_code"`
	RetMsg     string      `json:"ret_msg"`
	RetContent interface{} `json:"ret_content"`
}

type Errno struct {
	Code    int
	Message string
}

// 错误码定义
var (
	Succeed       = &Errno{Code: 0, Message: "success"}
)
```
- 对logic文件的返回值进行了修改