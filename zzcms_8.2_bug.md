# zzcms
zzcms_8.2_bug


> [Suggested description]
> zzcms 8.2 allows remote attackers to discover the full path via
> a direct request to
> 3/qq_connect2.0/API/class/ErrorCase.class.php or
> 3/ucenter_api/code/friend.php.
>
> ------------------------------------------
>
> [Additional Information]
> The vulnerability was discovered by downloading the program's source code to local and online deployment tests.
>
> Location :
> domain/3/qq_connect2.0/API/class/ErrorCase.class.php
>
> Code :
> require_once(CLASS_PATH."Recorder.class.php");
>
> Rows : 8
>
> Return error :
> Notice: Use of undefined constant CLASS_PATH - assumed 'CLASS_PATH' in /www/3/qq_connect2.0/API/class/ErrorCase.class.php on line 8
> Warning: require_once(CLASS_PATHRecorder.class.php): failed to open stream: No such file or directory in /www/3/qq_connect2.0/API/class/ErrorCase.class.php on line 8
> Fatal error: require_once(): Failed opening required 'CLASS_PATHRecorder.class.php' (include_path='.;C:\php\pear') in /www/3/qq_connect2.0/API/class/ErrorCase.class.php on line 8
>
> Harm:
> Web Site physical path leakage .
>
> Conditions for Execution :
> Normal access can
>
> Edition :
> zzcms 8.2
>
> Cause the cause :
> require_once(): Failed opening required 'CLASS_PATHRecorder.class.php' (include_path='.;C:\php\pear') in /www/3/qq_connect2.0/API/class/ErrorCase.class.php, cause path leakage.
>
> POC :
> http://127.0.0.1/3/qq_connect2.0/API/class/ErrorCase.class.php
>
>
>
>
> Location :
> domain/3/ucenter_api/code/friend.php
>
> Code :
>  $num = uc_friend_totalnum($Example_uid);
>
> Rows : 14
>
> Return error :
> Fatal error: Call to undefined function uc_friend_totalnum() in /www/3/ucenter_api/code/friend.php on line 14
>
> Harm :
> Web Site physical path leakage .
>
> Conditions for Execution :
> Normal access can
>
> Edition :
> zzcms 8.2
>
> Cause the cause :
> Call to undefined function uc_friend_totalnum() in /www/3/ucenter_api/code/friend.php, cause path leakage.
>
> POC :
> http://127.0.0.1/3/ucenter_api/code/friend.php
>
>
> fix suggestions :
> Modify the application source code to avoid information leakage.
>
> ------------------------------------------
>
> [VulnerabilityType Other]
> Physical path leaked
>
> ------------------------------------------
>
> [Vendor of Product]
> ZZCMS
>
> ------------------------------------------
>
> [Affected Product Code Base]
> zzcms - 8.2
>
> ------------------------------------------
>
> [Affected Component]
> ErrorCase.class.php , Use of undefined constant CLASS_PATH - assumed 'CLASS_PATH' , require_once(): Failed opening required 'CLASS_PATHRecorder.class.php'
>
> ------------------------------------------
>
> [Attack Type]
> Remote
>
> ------------------------------------------
>
> [Impact Information Disclosure]
> true
>
> ------------------------------------------
>
> [Attack Vectors]
> The vulnerability is triggered by accessing the following URL :
> http://127.0.0.1/3/qq_connect2.0/API/class/ErrorCase.class.php
> http://127.0.0.1/3/ucenter_api/code/friend.php
>
> ------------------------------------------
>
> [Discoverer]
> kongxin
