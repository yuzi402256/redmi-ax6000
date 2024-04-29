<!DOCTYPE html>
<!-- saved from url=(0031)https://www.1993.cm/ax6000.html -->
<html><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
 <link rel="stylesheet" href="https://qust.me/styles/main.css">       
    <title>红米AX6000解锁</title>
    <style>
        body {
            background-color: #333;
            font-family: Arial, sans-serif;
            text-align: center;
            color: #fff;
        }

        h1 {
            font-size: 24px;
            margin-top: 20px;
        }

        .container {
            background-color: #444;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            padding: 20px;
            width: 80%;
            margin: 0 auto;
            max-width: 700px;
        }

        p {
            font-size: 16px;
            margin-bottom: 10px;
        }

        input[type="text"] {
            padding: 10px;
            width: 100%;
            border: none;
            border-radius: 5px;
            margin-bottom: 10px;
            background-color: #555;
            color: #fff;
        }

        .button-container {
            display: flex;
            justify-content: space-between; /* 按钮之间的空间均匀分布 */
            flex-wrap: wrap; /* 如果按钮太多，自动换行 */
        }

        button {
            background-color: #007BFF;
            color: #fff;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            transition: background-color 0.3s;
            margin-bottom: 10px; /* 为按钮之间添加一些垂直间距 */
        }

        button:hover {
            background-color: #0056b3;
        }

        .code-box {
            border: 1px solid #ccc;
            padding: 5px;
            margin-top: 5px;
            max-width: 700px;
            background-color: #fff;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
            white-space: pre-wrap;
            overflow-x: auto;
            color: #ff0000;
			text-align: left;
        }

        code {
            font-size: 16px;
            text-align: left;
        }
    </style>
</head>
<body>
    <h1>Yu.zi修改.提供此步骤</h1>

    <!-- 链接1输入框和按钮 -->
    <div class="container">
        <p>开启开发/调试模式：</p>
        <input type="text" id="keywordInput1" placeholder="输入当前浏览器地址栏中的stok">
        <button onclick="openLink(1)">执行</button>
    </div>

    <!-- 链接2输入框和按钮 -->
    <div class="container">
        <p>重启路由：</p>
        <input type="text" id="keywordInput2" placeholder="输入当前浏览器地址栏中的stok">
        <button onclick="openLink(2)">重启</button>
    </div>

    <!-- 链接3输入框和按钮 -->
    <div class="container">
        <p>设置Bdata永久开启telnet：</p>
        <input type="text" id="keywordInput3" placeholder="输入当前浏览器地址栏中的stok">
        <button onclick="openLink(3)">开始设置</button>
    </div>

    <!-- 链接4输入框和按钮 -->
    <div class="container">
        <p>重启保存设置：</p>
        <input type="text" id="keywordInput4" placeholder="输入当前浏览器地址栏中的stok">
        <button onclick="openLink(4)">执行重启保存</button>
    </div>

    <!-- 代码复制部分 -->
    <div class="container">
        <h2>点击按钮复制代码 全部执行完后开启 ssh</h2>
        <div class="button-container">
            <button onclick="copyCode(1)">复制修改root密码为admin代码 1</button>
            <button onclick="copyCode(2)">复制固化SSH代码 2</button>
            <button onclick="copyCode(3)">复制永久开启SSH（重启不会关闭）代码 3</button>
            <button onclick="copyCode(4)">复制修改时区设置代码 4</button>
            <button onclick="copyCode(5)">复制关闭开发/调试模式代码 5</button>
            <button onclick="copyCode(6)">复制重启代码 6</button>
        </div>

        <div class="code-box">
            <code id="code">已复制: uci set system.@system[0].timezone='CST-8'
uci set system.@system[0].webtimezone='CST-8'
uci set system.@system[0].timezoneindex='2.84'
uci commit</code>
        </div>
    </div>
	
    <div class="container">
	  <h3>先用ssh的方式登录到路由器。开始刷openwrt 教程</h3>
<p> <font style="color: red;">第一步.</font>刷入过渡固件</p>
        <div class="button-container">
            <button onclick="copyCode(7)">复制刷入过渡固件代码</button>
        </div>
 <div class="code-box">
<code id="code">cat /proc/cmdline
</code></div>
<p> <font style="color: red;">第二步.</font>需要路由器是正常联网的，首先 ssh 连接上红米 ax6000 </p>
<p>执行上面的命令，查看返回的 firmware 等于 0 还是 1。</p> 
<p style="color: red;">如果是 0 执行</p>
 <div class="code-box">
<code id="code">
nvram set boot_wait=on
nvram set uart_en=1
nvram set flag_boot_rootfs=1
nvram set flag_last_success=1
nvram set flag_boot_success=1
nvram set flag_try_sys1_failed=0
nvram set flag_try_sys2_failed=0
nvram commit
cd /tmp
curl -L https://share.qust.me/d/%E8%B7%AF%E7%94%B1%E5%99%A8/redmi-ax6000/initramfs-factory.ubi -o initramfs-factory.ubi
ubiformat /dev/mtd9 -y -f /tmp/initramfs-factory.ubi
reboot -f
</code></div>
<p style="color: red;">如果是 1 执行</p>
 <div class="code-box">
<code id="code">
nvram set boot_wait=on
nvram set uart_en=1
nvram set flag_boot_rootfs=0
nvram set flag_last_success=0
nvram set flag_boot_success=1
nvram set flag_try_sys1_failed=0
nvram set flag_try_sys2_failed=0
nvram commit
cd /tmp
curl -L https://share.qust.me/d/%E8%B7%AF%E7%94%B1%E5%99%A8/redmi-ax6000/initramfs-factory.ubi -o initramfs-factory.ubi
ubiformat /dev/mtd8 -y -f /tmp/initramfs-factory.ubi
reboot -f
</code></div>
<p>执行完毕后，路由器被自动刷入一个过渡固件。复制执行完就会重启进入过渡固件，过渡固件的</p>
<p></p>
<p>如没有自动分配IP地址，我手动设置电脑的IP为：192.168.15.2就可以成功连上。如果没有链接上，默认网关要改为192.168.15.1</p>

<p>进入过渡系统之后，我们需要打开服务里的终端选项，管理ip：192.168.15.1 用户名和密码：root/admin<</p>
<p> <font style="color: red;">第三步.</font>再终端里或者 进入ssh 粘贴运行以下代码：</p>

 <div class="code-box">
<code id="code">
fw_setenv boot_wait on
fw_setenv uart_en 1
fw_setenv flag_boot_rootfs 0
fw_setenv flag_last_success 1
fw_setenv flag_boot_success 1
fw_setenv flag_try_sys1_failed 8
fw_setenv flag_try_sys2_failed 8
</code></div>


<p>接下来我们可以选择一个官方分区版openwrt固件刷入。</p>
<p>打开系统＞备份＞升级，选择最后一项：刷写新的固件。然后选择准备好固件点击上传。</p>
<p>默认选择：immortalwrt-mediatek-mt7986-xiaomi_redmi-router-ax6000-stock-squashfs-sysupgrade.bin</p>
<p>上传完之后.<font style="color: red;">记得取消“保留当前配置”.勾选强制刷机</font>再点击继续。</p>

<p>等待刷写完毕并自动重启后，就进入正式版的openWRT系统了。
正式版的openWRT系统后台地址是 192.168.6.1 用户名和密码依然是 root 和 password，默认的网口 1 是 wan 口，剩下的都是 lan 口。</p>




	        </div>

		
	

    <script>
        function openLink(linkNumber) {
            // 获取相应链接输入框中的关键字
            var keywordInputId = "keywordInput" + linkNumber;
            var keyword = document.getElementById(keywordInputId).value;

            // 固定的前后链接
            var prefixes = [
                "http://192.168.31.1/cgi-bin/luci/;stok=",
                "http://192.168.31.1/cgi-bin/luci/;stok=",
                "http://192.168.31.1/cgi-bin/luci/;stok=",
                "http://192.168.31.1/cgi-bin/luci/;stok="
            ];

            var suffixes = [
                "/api/misystem/set_sys_time?timezone=%20%27%20%3B%20zz%3D%24%28dd%20if%3D%2Fdev%2Fzero%20bs%3D1%20count%3D2%202%3E%2Fdev%2Fnull%29%20%3B%20printf%20%27%A5%5A%25c%25c%27%20%24zz%20%24zz%20%7C%20mtd%20write%20-%20crash%20%3B%20",
                "/api/misystem/set_sys_time?timezone=%20%27%20%3b%20reboot%20%3b%20",
                "/api/misystem/set_sys_time?timezone=%20%27%20%3B%20bdata%20set%20telnet_en%3D1%20%3B%20bdata%20set%20ssh_en%3D1%20%3B%20bdata%20set%20uart_en%3D1%20%3B%20bdata%20commit%20%3B%20",
                "/api/misystem/set_sys_time?timezone=%20%27%20%3b%20reboot%20%3b%20"
            ];

            // 将关键字与前后链接组合成完整的网址
            var fullUrl = prefixes[linkNumber - 1] + keyword + suffixes[linkNumber - 1];

            // 打开新窗口或标签页以访问完整网址
            window.open(fullUrl, "_blank");
        }

        function copyCode(codeNumber) {
            let codeText;
            
            switch (codeNumber) {
                case 1:
                    codeText = `echo -e 'admin\\nadmin' | passwd root`;
                    break;
                case 2:
                    codeText = `nvram set ssh_en=1\nnvram set telnet_en=1\nnvram set uart_en=1\nnvram set boot_wait=on\nnvram commit`;
                    break;
                case 3:
                    codeText = `mkdir /data/auto_ssh && cd /data/auto_ssh\ncurl -O https://fastly.jsdelivr.net/gh/lemoeo/AX6S@main/auto_ssh.sh\nchmod +x auto_ssh.sh\nuci set firewall.auto_ssh=include\nuci set firewall.auto_ssh.type='script'\nuci set firewall.auto_ssh.path='/data/auto_ssh/auto_ssh.sh'\nuci set firewall.auto_ssh.enabled='1'\nuci commit firewall`;
                    break;
                case 4:
                    codeText = `uci set system.@system[0].timezone='CST-8'\nuci set system.@system[0].webtimezone='CST-8'\nuci set system.@system[0].timezoneindex='2.84'\nuci commit`;
                    break;
                case 5:
                    codeText = `mtd erase crash`;
                    break;
                case 6:
                    codeText = `reboot`;
                    break;
                case 7:
                    codeText = `cat /proc/cmdline`;
                    break;
                default:
                    codeText = "无效的代码片段";
            }

            const codeElement = document.getElementById("code");
            const textarea = document.createElement("textarea");
            textarea.value = codeText;
            document.body.appendChild(textarea);
            textarea.select();
            document.execCommand("copy");
            document.body.removeChild(textarea);

            codeElement.textContent = `已复制: ${codeText}`;
        }
    </script>


</body></html>
