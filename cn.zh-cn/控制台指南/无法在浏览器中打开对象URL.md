# 无法在浏览器中打开对象URL<a name="zh-cn_topic_0045828990"></a>

## 问题<a name="section24512769"></a>

为什么无法在浏览器中打开对象URL？

## 回答<a name="section18890413175456"></a>

若在“桶策略”规则中配置了限制用户访问该对象的权限，或者在该对象的ACL权限中，没有开启“匿名用户”的“读取权限”权限，用户均不能在浏览器中打开该对象的URL。其中，“桶策略”权限优先级高于对象的ACL权限，即当该对象有“匿名用户”的“读取权限”权限的同时，在“桶策略”规则中也配置了限制用户访问该对象的权限，用户还是无法在浏览器中打开对象URL。

因此，可以尝试使用以下两种方式归避此问题。（以下[1](#aobs_get_started_0063_mmccppss_s3)到[6](#aobs_get_started_0063_mmccppss_s4)是设置该对象“匿名用户”的“读取权限”权限。[7](#s5)到[9](#aobs_get_started_0063_mmccppss_s1)是检查是否在“桶策略”规则中配置了限制用户访问该对象的权限。）

1.  <a name="aobs_get_started_0063_mmccppss_s3"></a>登录OBS管理控制台。
2.  在桶列表中单击待操作的桶，进入“概览”页面。
3.  在左侧导航栏，单击“权限”，进入权限管理页面。
4.  在“桶ACL”中，单击匿名用户后的“编辑”。
5.  勾选“匿名用户”后的“读取权限”。
6.  <a name="aobs_get_started_0063_mmccppss_s4"></a>单击“保存”后重试。
7.  <a name="s5"></a>登录OBS管理控制台。
8.  在桶列表中单击待操作的桶，进入“概览”页面。
9.  <a name="aobs_get_started_0063_mmccppss_s1"></a>在左侧导航栏，单击“权限 \> 桶策略\>高级设置”，检查是否在“桶策略”规则中配置了限制用户访问该对象的权限，是，则删除该“桶策略”规则后重试。

