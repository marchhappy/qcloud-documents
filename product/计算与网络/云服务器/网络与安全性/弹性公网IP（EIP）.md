弹性公网 IP 地址( EIP )，简称弹性 IP 地址或弹性 IP 。是专为动态云计算设计的静态 IP 地址。它是某地域下一个固定不变的公网 IP 地址。借助弹性公网 IP 地址，您可以快速将地址重新映射到账户中的另一个实例（或  [NAT 网关实例](/doc/product/215/%E7%BD%91%E5%85%B3#2.-nat.E7.BD.91.E5.85.B3) ），从而屏蔽实例故障。

例如，如果您需要将自定义域名重新映射到一个新实例的公网 IP 上，映射关系在 Internet 上传播更新可能需要十几个小时至几十个小时的时间，请求仍然将全部被解析到原有实例上，出现这段时间内新实例无法接收到请求的问题。弹性 IP 可以解决这样的问题，快速将请求指向到新的实例。

## 规则与限制
使用规则：
 - 弹性 IP 地址同时适用于基础网络和私有网络的实例，以及私有网络中的 [NAT 网关](/doc/product/215/4975) 实例。
 - 弹性 IP 地址与腾讯云账户相关联，而不是与某个具体实例相关联。
 - 选择、释放弹性 IP 地址，或欠费超过 7 天之前，弹性 IP 地址会一直与腾讯云账户保持关联。
 - 将弹性 IP 地址与实例绑定时，实例的当前公网 IP 地址会释放到基础网络公网 IP 地址池中。如果将弹性 IP 地址与实例解绑时选择了重新分配公网 IP ，实例会很快自动分配到新的公网 IP 地址（无法保证与绑定前的公网 IP 一致）。此外，销毁实例也会断开与弹性 IP 地址的关联。
 
使用限制：
 - 每个腾讯云账户每个地域每天申购次数为** 配额数\*2  **次。
 - 每个腾讯云账户每个地域下最多可创建** 20 **个弹性公网 IP。
 - 解绑EIP时，可免费重新分配公网 IP 的次数为每个腾讯云账户每天** 10 **次。
 - 弹性公网 IP 与 CVM/NAT 网关实例的绑定是一对一的关系。即，**1 **个弹性公网 IP 同一时间只能绑定到** 1 **个 CVM/NAT 网关实例上，**1 **个 CVM/NAT 网关实例同一时间只能绑定** 1 **个弹性公网 IP ，支持动态的绑定和解绑。 


## 计费
### 费用计算
 - 没有绑定云产品实例（CVM 或 NAT 网关）时，将按下表价格收取少量资源占用费用（不足 1 小时按 1 小时计，每小时结算 1 次）。
 - 已经绑定云产品实例（CVM 或 NAT 网关）时，弹性 IP 均免费。
建议您主动及时释放不再使用的弹性公网 IP ，以保证 IP 资源的合理利用，并节省您的费用，操作办法详见 [释放弹性公网 IP](#jump) 。

| 弹性公网 IP 所在地域 | 未绑定时价格 |
|---------|---------|---------|
| 北京地域、上海地域、广州地域 | 0.20 元/小时 | 
| 香港地域 | 0.30 元/小时 | 
| 北美地域、美西地域（硅谷） | 0.25 元/小时 | 
| 新加坡地域 | 0.30 元/小时 | 

### 欠费处理
 - 若用户账户余额小于 0 元且持续超过 ** 2 ** 个小时后，则所有弹性 IP 地址将在未来 24\*7  小时内保持为不可操作状态，直至续费后帐号余额大于 0 。
 - 若 (24\*7) + 2 小时后余额仍为负，所有弹性公网 IP 将自动释放。

## 操作指南
以下部分介绍如何使用弹性 IP 地址。

### 申请弹性公网 IP 

 1. 登录 [云服务器控制台](https://console.qcloud.com/cvm)。
	
 2. 在左侧导航窗格中，单击【弹性公网 IP】。

 3. 单击【申请】按钮，填写地域与数量后单击【确定】。

 4. 申请结束后即可在列表中看到您申请的弹性公网 IP ，此时处于未绑定状态。

<span id = "jump2">  </span>
### 弹性公网 IP 绑定云产品

 1. 登录 [云服务器控制台](https://console.qcloud.com/cvm)。

 2. 在左侧导航窗格中，单击【弹性公网 IP】。

 3. 在需要绑定云产品的 EIP 列表项后，单击【绑定】。（若绑定时， EIP 已绑定了实例，此按钮将为不可用状态，请先解绑。）
	
 4. 在弹出框中选择您需要绑定的云产品类型，并选择相应的云产品实例 ID，单击【绑定】按钮即可完成与云产品的绑定。

### 弹性公网 IP 解绑云产品

 1. 登录 [云服务器控制台](https://console.qcloud.com/cvm)。

 2. 在左侧导航窗格中，单击【弹性公网 IP】。

 3. 在已绑定云产品的 EIP 列表项后，单击【解绑】按钮。

 4. 点击【确定】。
 
>**注意：**
>解绑后云产品实例可能会被分配新的公网 IP ，可能与绑定前公网 IP 不一致。

<span id = "jump">  </span>
### 释放弹性公网 IP
 1. 登录 [云服务器控制台](https://console.qcloud.com/cvm)。

 2. 在左侧导航窗格中，单击【弹性公网 IP】。

 3. 在需要释放的 EIP 列表项后，单击【释放】按钮。

 4. 单击【确认】完成释放。

## 异常排查
弹性 IP 地址可能出现网络不通的异常情况，一般有如下原因： 

- 弹性 IP 地址没有绑定云产品。具体绑定方法见 [弹性公网 IP 绑定云产品](#jump2) 。

- 安全策略无效。查看是否有生效的安全策略（ [安全组](/doc/product/213/5221) 或 [网络 ACL](/doc/product/215/5132) )。如果绑定的云产品实例有安全策略，例如：禁止 8080 端口访问，那么弹性公网 IP 的 8080 端口也是无法访问的。

