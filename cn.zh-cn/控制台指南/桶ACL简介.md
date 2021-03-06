# 桶ACL简介<a name="zh-cn_topic_0045829069"></a>

## 桶ACL简介<a name="section1314334415429"></a>

访问控制列表（Access Control List，ACL）是一个指定被授权者和所授予权限的授权列表。桶ACL是基于账号或用户组的桶级访问控制。桶的拥有者可以通过桶ACL授予其他账号或用户组访问权限。

OBS支持通过桶ACL对[表1](#table177445813209)所示用户或用户组授予桶的访问权限。

**表 1**  OBS支持的被授权用户

<a name="table177445813209"></a>
<table><thead align="left"><tr id="row5236185882019"><th class="cellrowborder" valign="top" width="27%" id="mcps1.2.3.1.1"><p id="p4236185812209"><a name="p4236185812209"></a><a name="p4236185812209"></a>被授权用户</p>
</th>
<th class="cellrowborder" valign="top" width="73%" id="mcps1.2.3.1.2"><p id="p0236185811200"><a name="p0236185811200"></a><a name="p0236185811200"></a>描述</p>
</th>
</tr>
</thead>
<tbody><tr id="row122361958192016"><td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.3.1.1 "><p id="p1223615586209"><a name="p1223615586209"></a><a name="p1223615586209"></a>特定用户</p>
</td>
<td class="cellrowborder" valign="top" width="73%" headers="mcps1.2.3.1.2 "><p id="p223612587202"><a name="p223612587202"></a><a name="p223612587202"></a>桶ACL支持通过账号或用户组授予桶的访问权限，授予特定用户权限即通过账号授权。桶拥有者通过账号ID或账号名授权。授予账号权限后，账号下所有具有OBS资源权限的IAM用户都可以拥有此桶的访问权限。当需要为不同IAM用户授予不同的权限时，可以用过桶策略，具体操作请参见<a href="配置桶策略.md">配置桶策略</a>。</p>
</td>
</tr>
<tr id="row14236115815207"><td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.3.1.1 "><p id="p4237195812018"><a name="p4237195812018"></a><a name="p4237195812018"></a>拥有者</p>
</td>
<td class="cellrowborder" valign="top" width="73%" headers="mcps1.2.3.1.2 "><p id="p82371758102019"><a name="p82371758102019"></a><a name="p82371758102019"></a>拥有者是指创建桶的账户。桶拥有者默认拥有所有的桶访问权限，其中桶ACL的读取和写入这两种权限永远拥有，且不支持修改。</p>
<div class="note" id="note1556018562260"><a name="note1556018562260"></a><a name="note1556018562260"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p8237175842016"><a name="p8237175842016"></a><a name="p8237175842016"></a>去掉桶读取权限和桶写入权限将导致用户无法执行获取桶内对象列表、在桶中上传对象等基本操作，为正常使用OBS，不建议修改桶拥有者的权限。</p>
</div></div>
</td>
</tr>
<tr id="row0239105872015"><td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.3.1.1 "><p id="p2239658142016"><a name="p2239658142016"></a><a name="p2239658142016"></a>匿名用户</p>
</td>
<td class="cellrowborder" valign="top" width="73%" headers="mcps1.2.3.1.2 "><p id="p112397589206"><a name="p112397589206"></a><a name="p112397589206"></a>未注册华为云云服务的普通访客。如果匿名用户被授予了访问桶的权限，则表示所有人都可以访问对应的桶，并且不需要经过任何身份认证。</p>
<div class="notice" id="note1437509296"><a name="note1437509296"></a><a name="note1437509296"></a><span class="noticetitle"> 注意： </span><div class="noticebody"><p id="p122391580206"><a name="p122391580206"></a><a name="p122391580206"></a>开启匿名用户的桶访问权限后，所有人都可以在不经过身份认证的情况下，对桶进行访问。为安全起见，不建议通过桶ACL为匿名用户设置桶的访问权限。</p>
</div></div>
</td>
</tr>
<tr id="row112391958122020"><td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.3.1.1 "><p id="p1123911582207"><a name="p1123911582207"></a><a name="p1123911582207"></a>注册用户组</p>
</td>
<td class="cellrowborder" valign="top" width="73%" headers="mcps1.2.3.1.2 "><p id="p6239185816209"><a name="p6239185816209"></a><a name="p6239185816209"></a>注册用户组代表所有注册了华为云云服务的账号（仅指账号，不包括通过IAM创建的用户组或用户）。注册用户必须要经过身份认证（目前主要通过AK/SK进行身份认证），才可以获取对应的访问权限。例如，当注册用户组被授予桶写入权限后，世界上任何已通过身份验证的华为云云服务账号，都可以向您的桶上传、覆盖和删除对象。</p>
</td>
</tr>
<tr id="row1123945814203"><td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.3.1.1 "><p id="p19239165817208"><a name="p19239165817208"></a><a name="p19239165817208"></a>日志投递用户组</p>
</td>
<td class="cellrowborder" valign="top" width="73%" headers="mcps1.2.3.1.2 "><p id="p11239175822012"><a name="p11239175822012"></a><a name="p11239175822012"></a>日志投递用户组用于投递OBS桶及对象的访问日志。由于OBS本身不能在账户的桶中创建或上传任何文件，因此在需要为桶记录访问日志时，只能由账户授予日志投递用户组一定权限后，OBS才能将访问日志写入指定的日志存储桶中。该用户组仅用于OBS内部的日志记录。</p>
<div class="notice" id="note71171158122010"><a name="note71171158122010"></a><a name="note71171158122010"></a><span class="noticetitle"> 注意： </span><div class="noticebody"><p id="p7241158152013"><a name="p7241158152013"></a><a name="p7241158152013"></a>当日志记录开启后，目标存储桶的日志投递用户组会同步开启桶的写入权限和ACL读取权限。若手动将日志投递用户组的桶写入权限和ACL读取权限关闭，桶的日志记录会失败。</p>
</div></div>
</td>
</tr>
</tbody>
</table>

针对桶ACL，OBS当前支持四种访问权限，如[表2](#table28226836)所示：

**表 2**  OBS支持的访问权限

<a name="table28226836"></a>
<table><thead align="left"><tr id="row61083978"><th class="cellrowborder" valign="top" width="19.55%" id="mcps1.2.4.1.1"><p id="p55592582172343"><a name="p55592582172343"></a><a name="p55592582172343"></a>权限</p>
</th>
<th class="cellrowborder" valign="top" width="14.97%" id="mcps1.2.4.1.2"><p id="p48855171"><a name="p48855171"></a><a name="p48855171"></a>选项</p>
</th>
<th class="cellrowborder" valign="top" width="65.48%" id="mcps1.2.4.1.3"><p id="p64954777"><a name="p64954777"></a><a name="p64954777"></a>描述</p>
</th>
</tr>
</thead>
<tbody><tr id="row26845555"><td class="cellrowborder" rowspan="2" valign="top" width="19.55%" headers="mcps1.2.4.1.1 "><p id="p6705326172343"><a name="p6705326172343"></a><a name="p6705326172343"></a>桶访问权限</p>
</td>
<td class="cellrowborder" valign="top" width="14.97%" headers="mcps1.2.4.1.2 "><p id="p27006329"><a name="p27006329"></a><a name="p27006329"></a>读取权限</p>
</td>
<td class="cellrowborder" valign="top" width="65.48%" headers="mcps1.2.4.1.3 "><p id="p40029077"><a name="p40029077"></a><a name="p40029077"></a>此权限可以获取该桶内对象列表和桶的元数据。</p>
</td>
</tr>
<tr id="row21129772"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p33789992"><a name="p33789992"></a><a name="p33789992"></a>写入权限</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.4.1.2 "><p id="p52634865"><a name="p52634865"></a><a name="p52634865"></a>此权限可以上传、覆盖和删除该桶内任何对象。</p>
</td>
</tr>
<tr id="row35565678"><td class="cellrowborder" rowspan="2" valign="top" width="19.55%" headers="mcps1.2.4.1.1 "><p id="p46542350172415"><a name="p46542350172415"></a><a name="p46542350172415"></a>ACL访问权限</p>
</td>
<td class="cellrowborder" valign="top" width="14.97%" headers="mcps1.2.4.1.2 "><p id="p62247688"><a name="p62247688"></a><a name="p62247688"></a>读取权限</p>
</td>
<td class="cellrowborder" valign="top" width="65.48%" headers="mcps1.2.4.1.3 "><p id="p8897958"><a name="p8897958"></a><a name="p8897958"></a>此权限可以获取对应的桶的权限控制列表。</p>
<p id="p12972762"><a name="p12972762"></a><a name="p12972762"></a>桶的拥有者默认永远具有ACL的读取权限。</p>
</td>
</tr>
<tr id="row49646001"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p61903120"><a name="p61903120"></a><a name="p61903120"></a>写入权限</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.4.1.2 "><p id="p48096812"><a name="p48096812"></a><a name="p48096812"></a>此权限可以更新对应桶的权限控制列表。</p>
<p id="p30218124"><a name="p30218124"></a><a name="p30218124"></a>桶的拥有者默认永远具有ACL的写入权限。</p>
</td>
</tr>
</tbody>
</table>

>![](public_sys-resources/icon-note.gif) **说明：**   
>每一次对桶的授权操作都将覆盖桶已有的权限列表，而不会对其新增权限。  

## 桶ACL使用场景<a name="section7479813113513"></a>

桶ACL建议使用的场景如下：

-   授予日志投递用户组桶写入权限，用以存储桶访问请求日志。
-   授予指定账号桶读取权限和桶写入权限，用以共享桶数据或挂载外部桶。比如，账号A授予账号B桶读取权限及桶写入权限后，账号B就可以通过OBS Browser挂载外部桶、API&SDK等方式访问到该桶。

