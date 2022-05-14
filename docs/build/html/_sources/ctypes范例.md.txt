# ctypes 范例:

使用本模块需如下步骤:

1) 加载动态链接库 [shared_atomic.loaddll()](./原子字节数组API.md),

    `atomic = shared_atomic.loaddll()`

2) 定义多进程共离的变量，请使用multiprocessing模块，使用原子操作可以不用Rlock/lock, 使用参数lock=False

    `v = multiprocessing.Value(ctypes.c_long, 100, lock=False)`
    
    `a = multiprocessing.Array(ctypes.c_long, 100, lock=False)`
    
    如果只需要单进程多线程，请使用ctypes
    
    `a = ctypes.c_long(100)`
    
3) 利用 [ctypes.byref](https://docs.python.org/3/library/ctypes.html?highlight=ctypes.byref#ctypes.byref)获取指针。
    
    `aref = ctypes.byref(a, 0)`

4) 将指针传递给原子函数并启动多线程或多进程
    
    `atomic.long_get_and_set(aref,ctypes.c_long(100))`
    
    `processlist = []`
    
    `for i in range(10000):`
    
    `    processlist.append(Process(target=atomic.long_get_and_set, args=(aref,ctypes.c_long(100))))`

    `for i in range(10000):`
    
    `    processlist[i].start()`

    `for i in range(10000):`
    
    `    processlist[i].join()`