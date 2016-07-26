
#  take note of <b>Advanced tutorial: How to write reusable apps</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/reusable-apps/

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
