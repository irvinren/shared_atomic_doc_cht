# 原子API範例（多線程多進程混合）:

使用本模塊需如下步驟:

1) 創建子進程所需要的函數, 子進程當中可以創建多線程.

   `def process_run(a):`

   `     def subthread_run(a):`
   
   `         a.array_sub_and_fetch(b'\x0F')`

   `     threadlist = []`
   
   `     for t in range(5000):`
   
   `         threadlist.append(Thread(target=subthread_run, args=(a,)))`

   `     for t in range(5000):`
   
   `         threadlist[t].start()`

   `     for t in range(5000):`
   
   `         threadlist[t].join()`

2) 創建共享字節數組

    `    a = atomic_bytearray(b'ab', length=7, paddingdirection='r', paddingbytes=b'012', mode='m')`

3) 啓動這些進程與線程並利用共享字節數組

    `    processlist = []`
    
    `    for p in range(2):`
    
    `        processlist.append(Process(target=process_run, args=(a,)))`

    `    for p in range(2):`
    
    `        processlist[p].start()`

    `    for p in range(2):`
    
    `        processlist[p].join()`

    `    assert a.value == int.to_bytes(27411031864108609,length=8,byteorder='big')`
