# Selenium Grid

使用 **"--nodeconfig"** 服务器参数，你可以在本地 selenium grid 里注册你的 appium 服务器。

```bash
> node . -V --nodeconfig /path/to/nodeconfig.json
```

在 node 的配置文件里，你需要定义 **"browserName"**，**"version"** 和 **"platform"**。
基于这些参数，selenium grid 会将你的测试定向到正确的设备上去。你还需要配置你的 **host** 详细信息和
**selenium grid** 的详细信息。你可以在 <a href="http://code.google.com/p/selenium/source/browse/java/server/src/org/openqa/grid/common/defaults/GridParameters.properties">这里</a> 找到详细的参数列表和描述信息。

一旦你启动了 appium 服务器并且在 grid 里注册了信息，你会在 grid 控制台发现你的设备：

"http://**\<grid-ip-adress\>**:**\<grid-port\>**/grid/console"

## Grid 配置文件例子

```xml
{
  "capabilities":
      [
        {
          "browserName": "<e.g._iPhone5_or_iPad4>",
          "version":"<version_of_iOS_e.g._6.1>",
          "maxInstances": 1,
          "platform":"<platform_e.g._MAC_or_ANDROID>"
        }
      ],
  "configuration":
  {
    "cleanUpCycle":2000,
    "timeout":30000,
    "proxy": "org.openqa.grid.selenium.proxy.DefaultRemoteProxy",
    "url":"http://<host_name_appium_server_or_ip-address_appium_server>:<appium_port>/wd/hub",
    "maxSession": 1,
    "register": true,
    "registerCycle": 5000,
    "hubPort": <grid_port>,
    "hubHost": "<Grid_host_name_or_grid_ip-address>"
  }
}
```

可以在 <a href="http://selenium.googlecode.com/git/docs/api/java/org/openqa/selenium/Platform.html">这里</a>查看有效的 platform 参数。
