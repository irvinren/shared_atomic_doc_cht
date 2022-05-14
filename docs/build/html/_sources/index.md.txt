歡迎光臨共享原子性的文檔!
=========================================

<big> 這個模塊可以為python程序提供多線程與多進程程序當中所需要的可共享變量的原子操作。

內部提供的類:
- - [atomic_int/原子有符號整數](./原子有符號整數API.md)
- - [atomic_uint/原子無符號整數](./原子無符號整數API.md)
- - [atomic_float/原子浮點數](./原子布爾型浮點型API.md)
- - [atomic_bool/原子布爾型](./原子布爾型浮點型API.md)
- - [atomic_bytearray/原子字節數組](./原子字節數組API.md)
- - [atomic_string/原子字符串](./原子字符串API.md)
- - [atomic_set/原子集合](./原子集合API.md), 需要安裝 [bitarray>=2.4.0](https://pypi.org/project/bitarray/).
- - [atomic_list/原子列表](./原子列表API.md), 需要安裝 [bitarray>=2.4.0](https://pypi.org/project/bitarray/).

從舊版本繼承的CTYPES API可以一直沿用。

系統需求:
- Linux/MacOSX, 
- - 支持 CPython 3.0-3.11, Pypy 3.0-3.9, 
- - 需要 cffi >= 1.0.0, <= 1.1.15, 
- Windows, 
- - 只支持 CPython 3.0-3.11, 不支持 Pypy. 
- - 需要 cppyy >=1.5.0, <=2.3.1, 它使用 [cling](https://github.com/vgvassilev/cling/tree/master/tools/packaging) 作為C++解釋器.
- - 多進程模式不支持, 只支持單進程多線程模式.

使用範例, 請瀏覽 [原子API範例](./原子API範例.md)，[ctypes_API使用範例](./CTYPES範例.md)。

ctypes API 的使用參考, 請瀏覽 [ctypes API](./CTYPES_API.md).</big>

##

```{eval-rst}
.. toctree::

   原子API範例.md
   CTYPES範例.md
   原子有符號整數API.md
   原子無符號整數API.md
   原子布爾型浮點型API.md
   原子字節數組API.md
   原子列表API.md
   原子集合API.md
   原子字符串API.md
   CTYPES_API.md

 ```
 
 ![Python Logo](https://www.python.org/static/community_logos/python-logo.png)
