# 创建IAM委托<a name="obs_03_0037"></a>

OBS需使用IAM委托执行对象的跨区域复制。跨区域复制IAM委托创建如下：

1.  在“创建跨区域复制规则”对话框，单击“创建委托”，进入“统一身份认证服务”管理控制台“委托”页面。
2.  单击“创建委托”，进行委托创建。
3.  输入“委托名称”。
4.  “委托类型”选择“云服务。
5.  “云服务”选择“OBS”。
6.  选择“持续时间”。
7.  在“权限选择”项，单击“全局服务\>对象存储服务”行的“修改”，系统弹出“修改策略”对话框。
8.  选择“基本\>Tenant Administrator”，单击“确定”。
9.  （可选）如跨域复制规则勾选了“复制使用KMS加密的对象”，源桶和目标桶所在区域需配置KMS Administrator权限集。
    1.  单击源桶/目标桶所在区域行的“修改”，系统弹出“修改策略”对话框。
    2.  搜索KMS，并选择KMS Administrator权限集。
    3.  单击“确定”。

10. 单击“确定”，完成委托创建。

