
#  take note of <b>Advanced tutorial: How to write reusable apps</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/reusable-apps/

## 心得
- 先安裝 <b>setuptools</b>
- 教程要求將之前做的 polls <b>移出</b>到要打包的目錄
  - 這是故意的，實務上我們一般是<b>複製</b>
- 按規定定打包後，在回到 mysite 去安裝回來
  - 發現使用預設數據庫的好處，數據都在。
  - 遇到打包的檔案名稱和範例指令不一樣。
- TODO https://readthedocs.org 
  



## failed to run ez_setup.py


```
Microsoft Windows [版本 10.0.10586]
(c) 2015 Microsoft Corporation。保留所有权利。

C:\WINDOWS\system32>cd \

C:\>cd 2016-djangoproject

C:\2016-djangoproject>dir
 驱动器 C 中的卷是 OS
 卷的序列号是 54D4-5F1D

 C:\2016-djangoproject 的目录

2016/07/26  16:38    <DIR>          .
2016/07/26  16:38    <DIR>          ..
2016/07/26  16:37            12,402 ez_setup.py
2016/07/26  15:51    <DIR>          mysite
               1 个文件         12,402 字节
               3 个目录 102,270,791,680 可用字节

C:\2016-djangoproject>ez_setup.py
Downloading https://pypi.io/packages/source/s/setuptools/setuptools-25.1.0.zip
test
使用“2”个参数调用“DownloadFile”时发生异常:“操作超时”
所在位置 行:1 字符: 106
+ ... redentials; (new-object System.Net.WebClient).DownloadFile("https://p ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], MethodInvocationException
    + FullyQualifiedErrorId : WebException

Traceback (most recent call last):
  File "C:\2016-djangoproject\ez_setup.py", line 426, in <module>
    sys.exit(main())
  File "C:\2016-djangoproject\ez_setup.py", line 422, in main
    archive = download_setuptools(**_download_args(options))
  File "C:\2016-djangoproject\ez_setup.py", line 346, in download_setuptools
    downloader(url, saveto)
  File "C:\2016-djangoproject\ez_setup.py", line 246, in download_file_powershel
l
    _clean_check(cmd, target)
  File "C:\2016-djangoproject\ez_setup.py", line 220, in _clean_check
    subprocess.check_call(cmd)
  File "D:\Python\Python35-32\lib\subprocess.py", line 581, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['powershell', '-Command', '[System.Net.
WebRequest]::DefaultWebProxy.Credentials = [System.Net.CredentialCache]::Default
Credentials; (new-object System.Net.WebClient).DownloadFile("https://pypi.io/pac
kages/source/s/setuptools/setuptools-25.1.0.zip", "C:\\2016-djangoproject\\setup
tools-25.1.0.zip")']' returned non-zero exit status 1

C:\2016-djangoproject>
```

## setuptools exists
```
Windows PowerShell
版权所有 (C) 2015 Microsoft Corporation。保留所有权利。

PS C:\Users\MARK> (Invoke-WebRequest https://bootstrap.pypa.io/ez_setup.py).Content | python -
Invoke-WebRequest : 无法连接到远程服务器
所在位置 行:1 字符: 2
+ (Invoke-WebRequest https://bootstrap.pypa.io/ez_setup.py).Content | p ...
+  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (System.Net.HttpWebRequest:HttpWebRequest) [Invoke-WebRequest]，WebExce
    ption
    + FullyQualifiedErrorId : WebCmdletWebResponseException,Microsoft.PowerShell.Commands.InvokeWebRequestCommand

PS C:\Users\MARK> easy_install --version
setuptools 25.1.0 from d:\python\python35-32\lib\site-packages\setuptools-25.1.0-py3.5.egg (Python 3.5)
PS C:\Users\MARK>
```
## README.rst
這檔案裡有中文的話，打包出現編碼問題，應該用純英文，最起碼在這個階段。
```
Microsoft Windows [版本 10.0.10586]
(c) 2015 Microsoft Corporation。保留所有权利。

C:\Users\MARK>ping www.baidu.com

正在 Ping www.a.shifen.com [180.97.33.107] 具有 32 字节的数据:
请求超时。

180.97.33.107 的 Ping 统计信息:
    数据包: 已发送 = 1，已接收 = 0，丢失 = 1 (100% 丢失)，
Control-C
^C
C:\Users\MARK>ping www.baidu.com

正在 Ping www.a.shifen.com [180.97.33.107] 具有 32 字节的数据:
来自 180.97.33.107 的回复: 字节=32 时间=1968ms TTL=56
来自 180.97.33.107 的回复: 字节=32 时间=360ms TTL=56
来自 180.97.33.107 的回复: 字节=32 时间=932ms TTL=56
请求超时。

180.97.33.107 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 3，丢失 = 1 (25% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 360ms，最长 = 1968ms，平均 = 1086ms

C:\Users\MARK>ping www.baidu.com

正在 Ping www.a.shifen.com [180.97.33.107] 具有 32 字节的数据:
来自 180.97.33.107 的回复: 字节=32 时间=13ms TTL=56
来自 180.97.33.107 的回复: 字节=32 时间=10ms TTL=56
来自 180.97.33.107 的回复: 字节=32 时间=10ms TTL=56
来自 180.97.33.107 的回复: 字节=32 时间=9ms TTL=56

180.97.33.107 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 9ms，最长 = 13ms，平均 = 10ms

C:\Users\MARK>cd \

C:\>cd 2016-djangoproject

C:\2016-djangoproject>dir
 驱动器 C 中的卷是 OS
 卷的序列号是 54D4-5F1D

 C:\2016-djangoproject 的目录

2016/07/27  09:08    <DIR>          .
2016/07/27  09:08    <DIR>          ..
2016/07/27  09:11    <DIR>          django-polls
2016/07/26  16:37            12,402 ez_setup.py
2016/07/26  15:51    <DIR>          mysite
               1 个文件         12,402 字节
               4 个目录 97,797,980,160 可用字节

C:\2016-djangoproject>atom .

C:\2016-djangoproject>dir
 驱动器 C 中的卷是 OS
 卷的序列号是 54D4-5F1D

 C:\2016-djangoproject 的目录

2016/07/27  09:08    <DIR>          .
2016/07/27  09:08    <DIR>          ..
2016/07/27  09:27    <DIR>          django-polls
2016/07/26  16:37            12,402 ez_setup.py
2016/07/26  15:51    <DIR>          mysite
               1 个文件         12,402 字节
               4 个目录 97,794,678,784 可用字节

C:\2016-djangoproject>cd django-polls

C:\2016-djangoproject\django-polls>dir
 驱动器 C 中的卷是 OS
 卷的序列号是 54D4-5F1D

C:\2016-djangoproject\django-polls>python setup.py sdist
Traceback (most recent call last):
  File "setup.py", line 7, in <module>
    README = readme.read()
UnicodeDecodeError: 'gbk' codec can't decode byte 0xbf in position 2: illegal mu
ltibyte sequence

C:\2016-djangoproject\django-polls>python setup.py sdist
Traceback (most recent call last):
  File "setup.py", line 7, in <module>
    README = readme.read()
UnicodeDecodeError: 'gbk' codec can't decode byte 0xbf in position 2: illegal mu
ltibyte sequence

C:\2016-djangoproject\django-polls>python setup.py sdist
Traceback (most recent call last):
  File "setup.py", line 7, in <module>
    README = readme.read()
UnicodeDecodeError: 'gbk' codec can't decode byte 0xbf in position 2: illegal mu
ltibyte sequence

C:\2016-djangoproject\django-polls>python setup.py sdist
Traceback (most recent call last):
  File "setup.py", line 7, in <module>
    README = readme.read()
UnicodeDecodeError: 'gbk' codec can't decode byte 0xbf in position 2: illegal mu
ltibyte sequence

C:\2016-djangoproject\django-polls>python setup.py sdist
Traceback (most recent call last):
  File "setup.py", line 6, in <module>
    with open(os.path.join(os.path.dirname(__file__), 'README.rst')) as readme:
FileNotFoundError: [Errno 2] No such file or directory: 'README.rst'

C:\2016-djangoproject\django-polls>python setup.py sdist
running sdist
running egg_info
creating django_polls.egg-info
writing top-level names to django_polls.egg-info\top_level.txt
writing django_polls.egg-info\PKG-INFO
writing dependency_links to django_polls.egg-info\dependency_links.txt
writing manifest file 'django_polls.egg-info\SOURCES.txt'
reading manifest file 'django_polls.egg-info\SOURCES.txt'
reading manifest template 'MANIFEST.in'
warning: no files found matching '*' under directory 'polls\docs'
writing manifest file 'django_polls.egg-info\SOURCES.txt'
running check
creating django-polls-0.1
creating django-polls-0.1\django_polls.egg-info
creating django-polls-0.1\polls
creating django-polls-0.1\polls\migrations
creating django-polls-0.1\polls\static
creating django-polls-0.1\polls\static\polls
creating django-polls-0.1\polls\static\polls\images
creating django-polls-0.1\polls\templates
creating django-polls-0.1\polls\templates\polls
making hard links in django-polls-0.1...
hard linking LICENSE -> django-polls-0.1
hard linking MANIFEST.in -> django-polls-0.1
hard linking README.rst -> django-polls-0.1
hard linking setup.py -> django-polls-0.1
hard linking django_polls.egg-info\PKG-INFO -> django-polls-0.1\django_polls.egg
-info
hard linking django_polls.egg-info\SOURCES.txt -> django-polls-0.1\django_polls.
egg-info
hard linking django_polls.egg-info\dependency_links.txt -> django-polls-0.1\djan
go_polls.egg-info
hard linking django_polls.egg-info\top_level.txt -> django-polls-0.1\django_poll
s.egg-info
hard linking polls\__init__.py -> django-polls-0.1\polls
hard linking polls\admin.py -> django-polls-0.1\polls
hard linking polls\apps.py -> django-polls-0.1\polls
hard linking polls\models.py -> django-polls-0.1\polls
hard linking polls\tests.py -> django-polls-0.1\polls
hard linking polls\urls.py -> django-polls-0.1\polls
hard linking polls\views.py -> django-polls-0.1\polls
hard linking polls\migrations\0001_initial.py -> django-polls-0.1\polls\migratio
ns
hard linking polls\migrations\__init__.py -> django-polls-0.1\polls\migrations
hard linking polls\static\polls\style.css -> django-polls-0.1\polls\static\polls

hard linking polls\static\polls\images\background.jpg -> django-polls-0.1\polls\
static\polls\images
hard linking polls\templates\polls\detail-tutorial03.html -> django-polls-0.1\po
lls\templates\polls
hard linking polls\templates\polls\detail.html -> django-polls-0.1\polls\templat
es\polls
hard linking polls\templates\polls\index---draft.html -> django-polls-0.1\polls\
templates\polls
hard linking polls\templates\polls\index.html -> django-polls-0.1\polls\template
s\polls
hard linking polls\templates\polls\results.html -> django-polls-0.1\polls\templa
tes\polls
Writing django-polls-0.1\setup.cfg
creating dist
creating 'dist\django-polls-0.1.zip' and adding 'django-polls-0.1' to it
adding 'django-polls-0.1\LICENSE'
adding 'django-polls-0.1\MANIFEST.in'
adding 'django-polls-0.1\PKG-INFO'
adding 'django-polls-0.1\README.rst'
adding 'django-polls-0.1\setup.cfg'
adding 'django-polls-0.1\setup.py'
adding 'django-polls-0.1\django_polls.egg-info\dependency_links.txt'
adding 'django-polls-0.1\django_polls.egg-info\PKG-INFO'
adding 'django-polls-0.1\django_polls.egg-info\SOURCES.txt'
adding 'django-polls-0.1\django_polls.egg-info\top_level.txt'
adding 'django-polls-0.1\polls\admin.py'
adding 'django-polls-0.1\polls\apps.py'
adding 'django-polls-0.1\polls\models.py'
adding 'django-polls-0.1\polls\tests.py'
adding 'django-polls-0.1\polls\urls.py'
adding 'django-polls-0.1\polls\views.py'
adding 'django-polls-0.1\polls\__init__.py'
adding 'django-polls-0.1\polls\migrations\0001_initial.py'
adding 'django-polls-0.1\polls\migrations\__init__.py'
adding 'django-polls-0.1\polls\static\polls\style.css'
adding 'django-polls-0.1\polls\static\polls\images\background.jpg'
adding 'django-polls-0.1\polls\templates\polls\detail-tutorial03.html'
adding 'django-polls-0.1\polls\templates\polls\detail.html'
adding 'django-polls-0.1\polls\templates\polls\index---draft.html'
adding 'django-polls-0.1\polls\templates\polls\index.html'
adding 'django-polls-0.1\polls\templates\polls\results.html'
removing 'django-polls-0.1' (and everything under it)

C:\2016-djangoproject\django-polls>
```
## 有點波折，終於成功安裝回來
```


C:\2016-djangoproject\mysite>pip install --user django-polls-0.1.tar.gz
Requirement 'django-polls-0.1.tar.gz' looks like a filename, but the file does n
ot exist
Processing c:\2016-djangoproject\mysite\django-polls-0.1.tar.gz
Exception:
Traceback (most recent call last):
  File "d:\python\python35-32\lib\site-packages\pip\basecommand.py", line 215, i
n main
    status = self.run(options, args)
  File "d:\python\python35-32\lib\site-packages\pip\commands\install.py", line 2
99, in run
    requirement_set.prepare_files(finder)
  File "d:\python\python35-32\lib\site-packages\pip\req\req_set.py", line 370, i
n prepare_files
    ignore_dependencies=self.ignore_dependencies))
  File "d:\python\python35-32\lib\site-packages\pip\req\req_set.py", line 587, i
n _prepare_file
    session=self.session, hashes=hashes)
  File "d:\python\python35-32\lib\site-packages\pip\download.py", line 798, in u
npack_url
    unpack_file_url(link, location, download_dir, hashes=hashes)
  File "d:\python\python35-32\lib\site-packages\pip\download.py", line 705, in u
npack_file_url
    unpack_file(from_path, location, content_type, link)
  File "d:\python\python35-32\lib\site-packages\pip\utils\__init__.py", line 602
, in unpack_file
    tarfile.is_tarfile(filename) or
  File "d:\python\python35-32\lib\tarfile.py", line 2448, in is_tarfile
    t = open(name)
  File "d:\python\python35-32\lib\tarfile.py", line 1557, in open
    return func(name, "r", fileobj, **kwargs)
  File "d:\python\python35-32\lib\tarfile.py", line 1622, in gzopen
    fileobj = gzip.GzipFile(name, mode + "b", compresslevel, fileobj)
  File "d:\python\python35-32\lib\gzip.py", line 163, in __init__
    fileobj = self.myfileobj = builtins.open(filename, mode or 'rb')
FileNotFoundError: [Errno 2] No such file or directory: 'C:\\2016-djangoproject\
\mysite\\django-polls-0.1.tar.gz'

C:\2016-djangoproject\mysite>dir
 驱动器 C 中的卷是 OS
 卷的序列号是 54D4-5F1D

 C:\2016-djangoproject\mysite 的目录

2016/07/27  09:53    <DIR>          .
2016/07/27  09:53    <DIR>          ..
2016/07/26  15:15            43,008 db.sqlite3
2016/07/27  09:40           116,046 django-polls-0.1.zip
2016/07/25  13:54               249 manage.py
2016/07/25  13:58    <DIR>          mysite
2016/07/26  11:56                96 result.txt
2016/07/26  15:53    <DIR>          templates
               4 个文件        159,399 字节
               4 个目录 97,788,833,792 可用字节

C:\2016-djangoproject\mysite>pip install --user django-polls-0.1.zip
Processing c:\2016-djangoproject\mysite\django-polls-0.1.zip
Installing collected packages: django-polls
  Running setup.py install for django-polls ... done
Successfully installed django-polls

C:\2016-djangoproject\mysite>python manage.py runserver
Performing system checks...

System check identified no issues (0 silenced).
July 27, 2016 - 10:11:38
Django version 1.9.7, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
