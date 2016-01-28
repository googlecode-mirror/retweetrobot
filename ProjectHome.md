<img src='http://rtbot.laobubu.net/logo.png' align='right' width='128' height='128'>
RetweetRobot是开源的twitter锐推机器人，它可以自动收集RT信息并且转发。<br>
<br>
<br>
目前此程序已经运行于twitter上，请follow <a href='https://twitter.com/RTKcn'>@RTKcn</a>

<h2>Why RetweetRobot</h2>
<ul><li>开源，任何人都可以随意搭建<br>
</li><li>广泛，支持大多数的服务器＊<br>
</li><li>灵活，修改之后即可成为自己的特色工具</li></ul>

<i>＊推荐在Linux服务器下使用Cron Jobs，另外服务器必须不屏蔽twitter</i>
<hr />
<h2>注意一下，否则无法正常运行↓</h2>
<b>必须使用oAuth方式来发推！</b>

<h2>以下是过时的通知</h2>
因为1.5开始使用in reply to来链接原始数据，因此如果你使用<a href='http://laobubu.net/blog/162'>oAuth发推者</a>完成更新twitter，请修改update_tweet.php文件的代码为<br>
<pre><code>&lt;?php<br>
require_once('twitteroauth.php');<br>
require_once('config.php');<br>
<br>
if (ACCESS_TOKEN_SECRET === '' || ACCESS_TOKEN === '') {<br>
    header('Location: connect.php');<br>
}<br>
$connection = new TwitterOAuth(CONSUMER_KEY, CONSUMER_SECRET, ACCESS_TOKEN, ACCESS_TOKEN_SECRET);<br>
<br>
function post($msg,$reply=0) {<br>
	global $connection;<br>
	$arg = array('status' =&gt; $msg);<br>
	if ($reply&gt;0) $arg['in_reply_to_status_id']=$reply;<br>
	$connection-&gt;post('statuses/update', $arg);<br>
}<br>
</code></pre>
不知道update_tweet.php是怎么回事？看看 HowToEdit 页的“自定义via”部分先！<br>
<hr />
<h3>请参阅</h3>
<ul><li>如何安装 HowToInstall<br>
</li><li>如何个性化机器人 HowToEdit<br>
<hr />
<h3>Change Log</h3>
</li></ul><ol><li>更新到v1.2.0 在 2010年7月28日<br>
<ul><li>翻阅三页实时RT记录（扩大信息量）<br>
</li><li>尝试获取原始推（增强真实性）<br>
</li><li>更新热词记录文件记录方式（更容易欣赏）<br>
</li></ul></li><li>更新到v1.4.0 在 2010年9月12日<br>
<ul><li>每页RT数量达到100（扩大信息量）<br>
</li><li>修正和DirectAdmin计划任务的兼容性问题（增强兼容性）<br>
</li><li>更新日文屏蔽方法（内容更准确）<br>
</li></ul></li><li>更新到v1.5.0 在 2010年9月19日<br>
<ul><li>使用mobile.twitter.com页面作为部分API代理（增强稳定性）<br>
</li><li>添加in reply to以确保原推（保证准确性）<br>
</li><li>添加d方式进行调试（使用方法：访问时在地址后面加上d参数即可，例如<code>work.php?d</code>）