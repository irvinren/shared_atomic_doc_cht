# ctypes 範例:

使用本模塊需如下步驟:

1) 加載動態鏈接庫 [shared_atomic.loaddll()](./原子字節數組API.md),

    `atomic = shared_atomic.loaddll()`

2) 定義多進程共離的變量，請使用multiprocessing模塊，使用原子操作可以不用Rlock/lock, 使用參數lock=False

    `v = multiprocessing.Value(ctypes.c_long, 100, lock=False)`
    
    `a = multiprocessing.Array(ctypes.c_long, 100, lock=False)`
    
    如果只需要單進程多線程，請使用ctypes
    
    `a = ctypes.c_long(100)`
    
3) 利用 [ctypes.byref](https://docs.python.org/3/library/ctypes.html?highlight=ctypes.byref#ctypes.byref)獲取指針。
    
    `aref = ctypes.byref(a, 0)`

4) 將指針傳遞給原子函數並啓動多線程或多進程
    
    `atomic.long_get_and_set(aref,ctypes.c_long(100))`
    
    `processlist = []`
    
    `for i in range(10000):`
    
    `    processlist.append(Process(target=atomic.long_get_and_set, args=(aref,ctypes.c_long(100))))`

    `for i in range(10000):`
    
    `    processlist[i].start()`

    `for i in range(10000):`
    
    `    processlist[i].join()`
