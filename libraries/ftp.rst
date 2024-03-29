============
FTP管理类
============


+-------------+----------+
|属性         |值        |
+=============+==========+
|命名空间     |fize\\net |
+-------------+----------+
|类名         |Ftp       |
+-------------+----------+


:方法:


+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|方法名           |说明                                                                                                                                                                                                           |
+=================+===============================================================================================================================================================================================================+
|`__construct()`_ |构造函数                                                                                                                                                                                                       |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`__destruct()`_  |析构函数                                                                                                                                                                                                       |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`alloc()`_       |为要上传的文件预分配空间                                                                                                                                                                                       |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`cdup()`_        |切换到当前目录的父目录,即切换到上级目录
经测试，windows环境下有出现返回false并出现警告，但实际切换成功的情况                                                                                                   |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`chdir()`_       |改变当前目录                                                                                                                                                                                                   |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`chmod()`_       |设置 FTP 服务器上的文件权限
经测试，在windows环境下该方法无效，windows并没有针对FTP的权限之说                                                                                                                  |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`close()`_       |关闭当前FTP连接                                                                                                                                                                                                |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`connect()`_     |建立一个新的FTP连接                                                                                                                                                                                            |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`delete()`_      |删除 FTP 服务器上的一个文件                                                                                                                                                                                    |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`exec()`_        |请求运行一条 FTP 命令                                                                                                                                                                                          |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`fget()`_        |从 FTP 服务器上下载一个文件并保存到本地一个已经打开的文件中                                                                                                                                                    |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`fput()`_        |上传一个已经打开的文件到 FTP 服务器                                                                                                                                                                            |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`getOption()`_   |返回当前 FTP 连接的各种不同的选项设置                                                                                                                                                                          |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`get()`_         |从 FTP 服务器上下载一个文件                                                                                                                                                                                    |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`login()`_       |登录 FTP 服务器                                                                                                                                                                                                |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`mdtm()`_        |返回指定文件的最后修改时间戳                                                                                                                                                                                   |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`mkdir()`_       |建立新目录                                                                                                                                                                                                     |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`nbContinue()`_  |返回当前非阻塞的传输状态                                                                                                                                                                                       |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`nlist()`_       |返回给定目录的文件及文件夹名称列表                                                                                                                                                                             |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`pasv()`_        |是否打开被动模式                                                                                                                                                                                               |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`put()`_         |上传文件到 FTP 服务器                                                                                                                                                                                          |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`pwd()`_         |返回当前目录名                                                                                                                                                                                                 |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`quit()`_        |close的别名                                                                                                                                                                                                    |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`raw()`_         |向 FTP 服务器发送命令
将服务器的响应以字符串数组的形式返回。 对于响应内容既不做解析处理， 也不检测命令是否执行成功。                                                                                           |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`rawlist()`_     |返回指定目录下文件的详细列表                                                                                                                                                                                   |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`rename()`_      |更改 FTP 服务器上的文件或目录名
使用此方法可以移动文件或者文件夹                                                                                                                                               |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`rmdir()`_       |删除 FTP 服务器上的一个目录                                                                                                                                                                                    |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`setOption()`_   |设置各种 FTP 运行时选项                                                                                                                                                                                        |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`site()`_        |向服务器发送 SITE 命令                                                                                                                                                                                         |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`size()`_        |返回指定文件的大小                                                                                                                                                                                             |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`sslConnect()`_  |打开一个到 host 的安全 FTP 连接（SSL-FTP）。
注意：本函数有可能不存在，只有 PHP 构建时同时包含了 ftp 模块 和 OpenSSL 模块时， ftp_ssl_connect()  函数才可用。                                                  |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|`systype()`_     |返回远程 FTP 服务器的操作系统类型
非可靠判断，windows有可能返回UNIX                                                                                                                                            |
+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


方法
======
__construct()
-------------
构造函数

.. code-block:: php

  public function __construct (
      string $host,
      string $username = null,
      string $password = null,
      int $port = 21,
      int $timeout = 90,
      bool $ssl = false
  )


:参数:
  +---------+-----------------------------+
  |名称     |说明                         |
  +=========+=============================+
  |host     |要连接的服务器               |
  +---------+-----------------------------+
  |username |登录用户名                   |
  +---------+-----------------------------+
  |password |登录密码                     |
  +---------+-----------------------------+
  |port     |端口号，默认21               |
  +---------+-----------------------------+
  |timeout  |超时时间，默认90(秒)         |
  +---------+-----------------------------+
  |ssl      |是否为SSL-FTP连接            |
  +---------+-----------------------------+
  
  


__destruct()
------------
析构函数

.. code-block:: php

  public function __destruct ()



alloc()
-------
为要上传的文件预分配空间

.. code-block:: php

  public function alloc (
      int $filesize,
      string &$result = null
  ) : bool


:参数:
  +---------+-------------------------------------------------------------------------------------------+
  |名称     |说明                                                                                       |
  +=========+===========================================================================================+
  |filesize |要分配的空间，以字节为单位。                                                               |
  +---------+-------------------------------------------------------------------------------------------+
  |result   |如果提供此参数，那么服务器的响应 会以文本方式设置到 result 中。                            |
  +---------+-------------------------------------------------------------------------------------------+
  
  


cdup()
------
切换到当前目录的父目录,即切换到上级目录
经测试，windows环境下有出现返回false并出现警告，但实际切换成功的情况

.. code-block:: php

  public function cdup () : bool



chdir()
-------
改变当前目录

.. code-block:: php

  public function chdir (
      string $directory
  ) : bool


:参数:
  +----------+----------------+
  |名称      |说明            |
  +==========+================+
  |directory |目标目录。      |
  +----------+----------------+
  
  


chmod()
-------
设置 FTP 服务器上的文件权限
经测试，在windows环境下该方法无效，windows并没有针对FTP的权限之说

.. code-block:: php

  public function chmod (
      int $mode,
      string $filename
  ) : int


:参数:
  +---------+----------------------------------------+
  |名称     |说明                                    |
  +=========+========================================+
  |mode     |要设置的权限值，八进制值。              |
  +---------+----------------------------------------+
  |filename |远程文件名称。                          |
  +---------+----------------------------------------+
  
  

:返回值:
  操作成功返回文件新的权限，操作失败返回 FALSE。


close()
-------
关闭当前FTP连接

.. code-block:: php

  public function close () : bool



connect()
---------
建立一个新的FTP连接

.. code-block:: php

  public function connect (
      string $host,
      int $port = 21,
      int $timeout = 90
  )


:参数:
  +--------+-----------------------------+
  |名称    |说明                         |
  +========+=============================+
  |host    |要连接的服务器               |
  +--------+-----------------------------+
  |port    |端口号，默认21               |
  +--------+-----------------------------+
  |timeout |超时时间，默认90(秒)         |
  +--------+-----------------------------+
  
  


delete()
--------
删除 FTP 服务器上的一个文件

.. code-block:: php

  public function delete (
      string $path
  ) : bool


:参数:
  +-------+-------------------------------------------------------------------------------+
  |名称   |说明                                                                           |
  +=======+===============================================================================+
  |path   |要删除的文件路径，可以是相对路径，也可以是绝对路径。                           |
  +-------+-------------------------------------------------------------------------------+
  
  


exec()
------
请求运行一条 FTP 命令

.. code-block:: php

  public function exec (
      string $command
  ) : bool


:参数:
  +--------+-----------+
  |名称    |说明       |
  +========+===========+
  |command |FTP 命令   |
  +--------+-----------+
  
  


fget()
------
从 FTP 服务器上下载一个文件并保存到本地一个已经打开的文件中

.. code-block:: php

  public function fget (
      resource $handle,
      string $remote_file,
      int $mode,
      int $resumepos = 0,
      bool $nb = false
  ) : mixed


:参数:
  +------------+------------------------------------------------------------------------------------------------------------+
  |名称        |说明                                                                                                        |
  +============+============================================================================================================+
  |handle      |本地已经打开的文件的句柄。                                                                                  |
  +------------+------------------------------------------------------------------------------------------------------------+
  |remote_file |远程文件的路径。                                                                                            |
  +------------+------------------------------------------------------------------------------------------------------------+
  |mode        |传送模式参数， 必须是 (文本模式) FTP_ASCII  或 (二进制模式) FTP_BINARY  中的一个。                          |
  +------------+------------------------------------------------------------------------------------------------------------+
  |resumepos   |远程文件开始下载的位置。                                                                                    |
  +------------+------------------------------------------------------------------------------------------------------------+
  |nb          |是否以非阻塞方式                                                                                            |
  +------------+------------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  如果非阻塞则返回FTP_FAILED  或 FTP_FINISHED  或 FTP_MOREDATA，否则返回下载结果


fput()
------
上传一个已经打开的文件到 FTP 服务器

.. code-block:: php

  public function fput (
      string $remote_file,
      resource $handle,
      int $mode,
      int $startpos = 0,
      bool $nb = false
  ) : mixed


:参数:
  +------------+-----------------------------------------------------------------------------------------------------+
  |名称        |说明                                                                                                 |
  +============+=====================================================================================================+
  |remote_file |远程文件路径。                                                                                       |
  +------------+-----------------------------------------------------------------------------------------------------+
  |handle      |打开的本地文件句柄，读取到文件末尾。                                                                 |
  +------------+-----------------------------------------------------------------------------------------------------+
  |mode        |传输模式只能为 (文本模式) FTP_ASCII  或 (二进制模式) FTP_BINARY  其中的一个。                        |
  +------------+-----------------------------------------------------------------------------------------------------+
  |startpos    |远程文件上传的开始位置。                                                                             |
  +------------+-----------------------------------------------------------------------------------------------------+
  |nb          |是否以非阻塞方式                                                                                     |
  +------------+-----------------------------------------------------------------------------------------------------+
  
  

:返回值:
  如果非阻塞则返回FTP_FAILED  或 FTP_FINISHED  或 FTP_MOREDATA，否则返回上传结果


getOption()
-----------
返回当前 FTP 连接的各种不同的选项设置

.. code-block:: php

  public function getOption (
      int $option
  ) : mixed


:参数:
  +-------+---------------------+
  |名称   |说明                 |
  +=======+=====================+
  |option |参数 option 选项     |
  +-------+---------------------+
  
  


get()
-----
从 FTP 服务器上下载一个文件

.. code-block:: php

  public function get (
      string $local_file,
      string $remote_file,
      int $mode,
      int $resumepos = 0,
      bool $nb = false
  ) : mixed


:参数:
  +------------+-----------------------------------------------------------------------------------------------------------+
  |名称        |说明                                                                                                       |
  +============+===========================================================================================================+
  |local_file  |文件本地的路径（如果文件已经存在，则会被覆盖）。                                                           |
  +------------+-----------------------------------------------------------------------------------------------------------+
  |remote_file |文件的远程路径。                                                                                           |
  +------------+-----------------------------------------------------------------------------------------------------------+
  |mode        |传送模式。只能为 (文本模式) FTP_ASCII  或 (二进制模式) FTP_BINARY  中的其中一个。                          |
  +------------+-----------------------------------------------------------------------------------------------------------+
  |resumepos   |从远程文件的这个位置继续下载。                                                                             |
  +------------+-----------------------------------------------------------------------------------------------------------+
  |nb          |是否以非阻塞方式                                                                                           |
  +------------+-----------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  如果非阻塞则返回FTP_FAILED  或 FTP_FINISHED  或 FTP_MOREDATA，否则返回下载结果


login()
-------
登录 FTP 服务器

.. code-block:: php

  public function login (
      string $username,
      string $password
  ) : bool


:参数:
  +---------+----------+
  |名称     |说明      |
  +=========+==========+
  |username |用户名    |
  +---------+----------+
  |password |密码      |
  +---------+----------+
  
  


mdtm()
------
返回指定文件的最后修改时间戳

.. code-block:: php

  public function mdtm (
      string $remote_file
  ) : int


:参数:
  +------------+-------------+
  |名称        |说明         |
  +============+=============+
  |remote_file |文件路径     |
  +------------+-------------+
  
  


mkdir()
-------
建立新目录

.. code-block:: php

  public function mkdir (
      string $directory
  ) : mixed


:参数:
  +----------+----------+
  |名称      |说明      |
  +==========+==========+
  |directory |新目录    |
  +----------+----------+
  
  

:返回值:
  如果成功返回新建的目录名，否则返回 FALSE。


nbContinue()
------------
返回当前非阻塞的传输状态

.. code-block:: php

  public function nbContinue () : int


:返回值:
  返回常量 FTP_FAILED  或 FTP_FINISHED  或 FTP_MOREDATA。


nlist()
-------
返回给定目录的文件及文件夹名称列表

.. code-block:: php

  public function nlist (
      string $directory = null
  ) : array


:参数:
  +----------+-------------------------------------------------------------------+
  |名称      |说明                                                               |
  +==========+===================================================================+
  |directory |指定要列表的目录，如果不指定则默认为当前目录                       |
  +----------+-------------------------------------------------------------------+
  
  


pasv()
------
是否打开被动模式

.. code-block:: php

  public function pasv (
      bool $pasv
  ) : bool


:参数:
  +-------+-------------------------+
  |名称   |说明                     |
  +=======+=========================+
  |pasv   |是否打开被动模式         |
  +-------+-------------------------+
  
  

:返回值:
  成功时返回 TRUE ， 或者在失败时返回 FALSE。


put()
-----
上传文件到 FTP 服务器

.. code-block:: php

  public function put (
      string $remote_file,
      string $local_file,
      int $mode = 2,
      int $startpos = 0,
      bool $nb = false
  ) : mixed


:参数:
  +------------+----------------------------------------------------------------------------------------------------------------+
  |名称        |说明                                                                                                            |
  +============+================================================================================================================+
  |remote_file |远程文件路径。                                                                                                  |
  +------------+----------------------------------------------------------------------------------------------------------------+
  |local_file  |本地文件路径。                                                                                                  |
  +------------+----------------------------------------------------------------------------------------------------------------+
  |mode        |传送模式，只能为 FTP_ASCII （文本模式）或 FTP_BINARY （二进制模式）,默认为二进制。                              |
  +------------+----------------------------------------------------------------------------------------------------------------+
  |startpos    |远程文件上传的开始位置。                                                                                        |
  +------------+----------------------------------------------------------------------------------------------------------------+
  |nb          |是否以非阻塞方式                                                                                                |
  +------------+----------------------------------------------------------------------------------------------------------------+
  
  

:返回值:
  如果非阻塞则返回FTP_FAILED  或 FTP_FINISHED  或 FTP_MOREDATA，否则返回上传结果


pwd()
-----
返回当前目录名

.. code-block:: php

  public function pwd () : string



quit()
------
close的别名

.. code-block:: php

  public function quit () : bool



raw()
-----
向 FTP 服务器发送命令
将服务器的响应以字符串数组的形式返回。 对于响应内容既不做解析处理， 也不检测命令是否执行成功。

.. code-block:: php

  public function raw (
      string $command
  ) : array


:参数:
  +--------+----------------------+
  |名称    |说明                  |
  +========+======================+
  |command |要执行的命令。        |
  +--------+----------------------+
  
  


rawlist()
---------
返回指定目录下文件的详细列表

.. code-block:: php

  public function rawlist (
      string $directory,
      bool $recursive = false
  ) : array


:参数:
  +----------+---------------------------------------------------------------------+
  |名称      |说明                                                                 |
  +==========+=====================================================================+
  |directory |目录路径。                                                           |
  +----------+---------------------------------------------------------------------+
  |recursive |如果此参数为 TRUE ，实际执行的命令将会为 LIST -R。                   |
  +----------+---------------------------------------------------------------------+
  
  


rename()
--------
更改 FTP 服务器上的文件或目录名
使用此方法可以移动文件或者文件夹

.. code-block:: php

  public function rename (
      string $oldname,
      string $newname
  ) : bool


:参数:
  +--------+-------------------------------+
  |名称    |说明                           |
  +========+===============================+
  |oldname |原来的文件／目录名。           |
  +--------+-------------------------------+
  |newname |新名字。                       |
  +--------+-------------------------------+
  
  


rmdir()
-------
删除 FTP 服务器上的一个目录

.. code-block:: php

  public function rmdir (
      string $directory,
      bool $force = false
  ) : bool


:参数:
  +----------+----------------------------------------------+
  |名称      |说明                                          |
  +==========+==============================================+
  |directory |要删除的目录                                  |
  +----------+----------------------------------------------+
  |force     |如果该目录不为空，是否强制删除                |
  +----------+----------------------------------------------+
  
  


setOption()
-----------
设置各种 FTP 运行时选项

.. code-block:: php

  public function setOption (
      int $option,
      mixed $value
  ) : bool


:参数:
  +-------+--------------------------------------------+
  |名称   |说明                                        |
  +=======+============================================+
  |option |选项标识                                    |
  +-------+--------------------------------------------+
  |value  |本参数取决于要修改哪个 option。             |
  +-------+--------------------------------------------+
  
  


site()
------
向服务器发送 SITE 命令

.. code-block:: php

  public function site (
      string $command
  ) : bool


:参数:
  +--------+------------+
  |名称    |说明        |
  +========+============+
  |command |SITE 命令   |
  +--------+------------+
  
  


size()
------
返回指定文件的大小

.. code-block:: php

  public function size (
      string $remote_file
  ) : int


:参数:
  +------------+----------------------+
  |名称        |说明                  |
  +============+======================+
  |remote_file |远程文件路径。        |
  +------------+----------------------+
  
  


sslConnect()
------------
打开一个到 host 的安全 FTP 连接（SSL-FTP）。
注意：本函数有可能不存在，只有 PHP 构建时同时包含了 ftp 模块 和 OpenSSL 模块时， ftp_ssl_connect()  函数才可用。

.. code-block:: php

  public function sslConnect (
      string $host,
      int $port = 21,
      int $timeout = 90
  )


:参数:
  +--------+-----------------------------+
  |名称    |说明                         |
  +========+=============================+
  |host    |要连接的服务器               |
  +--------+-----------------------------+
  |port    |端口号，默认21               |
  +--------+-----------------------------+
  |timeout |超时时间，默认90(秒)         |
  +--------+-----------------------------+
  
  


systype()
---------
返回远程 FTP 服务器的操作系统类型
非可靠判断，windows有可能返回UNIX

.. code-block:: php

  public function systype () : string



