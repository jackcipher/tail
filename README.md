[![Build Status](https://travis-ci.org/hpcloud/tail.svg)](https://travis-ci.org/hpcloud/tail)
[![Build status](https://ci.appveyor.com/api/projects/status/vrl3paf9md0a7bgk/branch/master?svg=true)](https://ci.appveyor.com/project/Nino-K/tail/branch/master)

# tail-ing文件的Go包

Forked From [https://github.com/hpcloud/tail](https://github.com/hpcloud/tail)

底层实现
- inotify
  
内核2.6以上版本可使用

- poll
  
通过轮询实现


```Go
filename := "/Users/jack/tail.log"

tails, err := tail.TailFile(filename, tail.Config{
ReOpen: true,
Follow: true,
Location:  &tail.SeekInfo{
Offset: 0,
Whence: io.SeekEnd, // 文件尾部
},
MustExist: false,
Poll:      false,
})
```

See [API documentation](http://godoc.org/github.com/hpcloud/tail).

## 日志分割

支持文件分割/移动检测
可以很好地配合日志分割程序使用


## 安装

    go get github.com/jackcipher/tail


## Fork修改内容

检测到iNode节点变更后，重新打开文件，并将游标设置为文件尾部