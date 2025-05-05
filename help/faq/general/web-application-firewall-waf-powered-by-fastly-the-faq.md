---
title: '由Fastly提供支持的Web应用程序防火墙(WAF)：常见问题解答'
description: Web应用程序防火墙(WAF)通过根据一组安全规则过滤流量，防止恶意流量进入站点和网络。 触发任何规则的流量会被阻止，以免损害您的网站或网络。
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Fastly支持的Web应用程序防火墙(WAF)：常见问题解答

## Adobe Commerce的托管云WAF（由Fastly提供支持）如何工作？

Web应用程序防火墙(WAF)通过根据一组安全规则过滤流量，阻止[恶意流量](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md)进入站点和网络。 触发任何规则的流量会被阻止，以免损害您的网站或网络。

Adobe Commerce的cloud WAF提供了WAF策略和规则集，旨在保护Adobe Commerce Web应用程序免受各种攻击。

WAF会检查Web和管理通信以识别任何可疑活动。 它会评估GET和POST流量（HTTP API调用），并应用规则集来确定要阻止的流量。 WAF可以阻止多种攻击，包括SQL注入攻击、跨站点脚本攻击、数据导出攻击以及违反HTTP协议等。

作为基于云的服务，WAF不需要安装或维护任何硬件或软件。 Fastly是一家现有的技术合作伙伴，负责提供软件和专业知识。 它们的高性能、始终可用的WAF驻留在Fastly全球交付网络的每个缓存节点中。

## WAF是否适用于所有云客户？

是，云WAF服务包含在您的Adobe Commerce on cloud基础架构订阅中，适用于Adobe Commerce on云基础架构入门计划架构和Adobe Commerce on cloud基础架构专业计划架构计划，无需额外费用。 WAF服务在生产和暂存环境中可用。

## WAF是否符合PCI DSS 6.6要求？

是的。

## 如果我的Adobe Commerce on cloud infrastructure帐户管理多个域上的网站，那么WAF配置文件是针对每个域进行优化还是针对所有域进行整体优化？

WAF针对单个云帐户下的所有域进行整体调整。

## WAF使用什么规则？

在云基础架构生产环境中应用于Adobe Commerce的WAF配置文件中的规则集基于OWASP十大威胁保护规则集，该规则集涵盖了对Web服务的常见攻击。 它还包含由TrustWave SpiderLabs开发的Adobe Commerce特定规则。 Fastly的安全研究团队还增加了保护网站和网络免受常见攻击的规则：错误的IP地址、错误的用户代理以及已知的僵尸网络命令和控制节点。 我们在OWASP Paranoia Level 3或更低级别启用规则，这提供了高安全保护。

## 如何访问日志？

要将日志发送到日志记录工具，请与技术客户经理(TAM)合作在Fastly中添加日志记录端点。

## 块请求是什么样的？

被阻止的请求会返回一个带有请求标识符的403页面。

只要自定义包含请求标识符，您就可以自定义此页面。 有关详细信息，请与您的技术客户经理联系。

## 如何更新WAF规则集？ WAF规则的更改或更新以及在生产中全局应用的速度如何？

作为云WAF服务的一部分，Fastly管理来自商业第三方、Fastly研究和开放源的规则更新。 他们可以根据需要或在可从各自来源对规则进行更改时，将发布的规则更新到策略中。 一旦启用任何服务的WAF实例，也会插入与已发布的规则类匹配的新规则。 这有助于确保即时涵盖新的或不断演变的利用漏洞攻击。 您可以在Fastly文档网站上查看有关规则更新和维护[的信息](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance)。

## Adobe Commerce的云WAF与Fastly为其直接客户提供的WAF解决方案有何不同？

Fastly直接销售的WAF解决方案是一种付费产品，包括更广泛的规则集和额外功能，如规则自定义和恶意软件保护。 Adobe Commerce的云WAF解决方案包含一组以Adobe Commerce应用程序为目标的规则，并且仅为每个客户的生产环境包含一个规则集。

## WAF可以抵御哪些类型的安全威胁？

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">威胁</th>
<th style="width: 497.5px; text-align: left;">WAF保护</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL注入攻击</td>
<td style="width: 497.5px;">OWASP ModSecurity核心规则集和TrustWave商业规则集都包含用于SQL注入攻击及其变体的特定过滤器。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>跨站点注射</p>
</td>
<td style="width: 497.5px;">OWASP规则集可抵御跨站点注入攻击。 Fastly利用评分机制来处理每个请求，以寻求对来源的跨站点注入和其他威胁。 我们根据整个核心规则集对每个请求进行评分，并验证请求得分是否低于可配置的阈值以便其通过。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">暴力攻击</td>
<td style="width: 497.5px;">已被OWASP规则集覆盖。 Fastly还通过使用VCL代码阻止暴力活动，该代码可识别特定源、请求，或在任何流量到达原始数据中心之前尝试暴力或压倒安全控制。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">网络攻击</td>
<td style="width: 497.5px;">Fastly自动管理网络攻击或针对网络基础架构的攻击。 Fastly不会将DNS传递到源，并且与窄HTTP、HTTPS或DNS配置文件不匹配的流量会在网络边缘被丢弃。 针对控制协议的攻击可通过验证整个网络的端点来防御。 此外，Fastly网络内使用的网络协议也经过了强化，以确保它们不能用作放大或反射的手段。 客户有责任利用Fastly缓存IP地址空间（作为CDN服务的一部分发布给我们的客户）来防御绕过Fastly网络的攻击。 建议不要在公共DNS中发布原始IP地址空间，以确保绕过攻击不能将这些地址用作目标。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript注入攻击</td>
<td style="width: 497.5px;">WAF规则可防止恶意的JavaScript代码插入到与Web服务的客户端通信中。 通过WAF过滤常见利用漏洞模式或得分，以确保原始服务的完整性。</td>
</tr>
</tbody>
</table>

## 是否提供其他特性和功能？

Adobe Commerce的WAF产品包括：作为PCI要求的一部分针对OWASP Top-10威胁的保护，全天候支持（包括误报鉴别）和版本升级。 标准选件不支持以下功能：

* 速率限制
* 规则自定义
* 机器人减缓
* 恶意软件防护

## WAF如何影响我的网站性能？

每个非缓存的请求都会经历约1.5毫秒(ms)到20毫秒的延迟。

## 客户是否可以创建和修改IP黑名单以阻止流量？

是，客户可以在云基础架构的Admin UI上通过Adobe Commerce启用按国家/地区和访问控制列表(ACL)进行阻止。 如果您希望阻止来自特定国家/地区或特定IP或IP范围的访客访问，请使用这些功能。 如果您希望被阻止的访客查看自定义页面而不是错误代码，可以通过在Fastly配置菜单中上传HTML来创建自定义错误页面。 请参阅我们的开发人员文档中的[创建自定义错误/维护页面](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)。

## 可在何处查看WAF服务的运行状态？

在[Fastly状态页](https://status.fastly.com/)上报告整体WAF服务可用性。 不提供单个客户的WAF的可用性报告。

## Adobe Commerce是否为WAF服务提供事件管理？

目前，不提供事件管理。

## Adobe Commerce是否有安全运营中心？

虽然Adobe Commerce没有安全运营中心，但我们确实有一个安全运营流程，使我们能够利用适当的资源实时响应安全事件。 我们还提供全天候的跟踪支持。

您还可以从[安全中心](https://helpx.adobe.com/security.html)获取与Adobe Commerce相关的安全新闻和更新。

## 提供哪些支持？

WAF支持提供以下资源来帮助您减轻不需要的或恶意请求对服务的影响：

* 入门：对支持Adobe Commerce托管云WAF的Fastly服务进行启用、初始设置和有限监控
* 持续误判以解决WAF阻止合法流量的情况
* 配置作为WAF版本升级的一部分引入的任何新标准规则

请参阅[云SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf)术语，了解其他支持信息，包括严重性定义、响应时间、渠道和可用性。

## 如果WAF阻止合法流量或导致其他问题，如何获得帮助？

[&#128279;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)在[Adobe Commerce帮助中心](https://support.magento.com)提交支持票证。 请包括指示票证与WAF服务相关，并包括阻止的请求标识符(ID)。

Adobe Commerce支持工单系统跟踪我们的支持工程师和客户人员之间的通信。 此系统提供了带有时间戳的沟通记录，并在票证更新时向客户和Adobe Commerce的员工发送电子邮件。

对于在线提交的所有事件，将通过Adobe Commerce客户帮助中心票证系统确认事件接收。 在收到正确提交的事故后，支持服务将根据上述优先级别优先处理。

下表汇总了WAF支持的支持渠道和可用性：

<table class="table-basic">
<tbody>
<tr>
<th>支持服务</th>
<th>详细信息</th>
</tr>
<tr>
<td>在线自助帮助</td>
<td>无限制访问</td>
</tr>
<tr>
<td>事件报告的可用性</td>
<td>24/7</td>
</tr>
<tr>
<td>Web门户</td>
<td>通过Zendesk提供</td>
</tr>
<tr>
<td>紧急升级*</td>
<td>请参阅有关美国和国际号码的<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">Adobe Commerce P1通知热线</a>文章。</td>
</tr>
</tbody>
</table>

*\* Adobe Commerce的免费支持电话线仅保留用于优先级1事件。 非优先级1调用将减慢对问题*&#x200B;的整体响应速度

## 如何对误报进行分级？

我们有一个误报分类流程（24x7全天候可用），可快速处理和解决合法请求触发了WAF规则的实例。 误报事件被视为优先级1问题。 作为默认操作，我们的支持团队可以立即更新WAF策略以禁用触发阻止事件的规则，并允许合法请求通过WAF。

## 如果流向Adobe Commerce云基础架构站点上的管理员部分的流量触发WAF规则，该怎么办？ Adobe Commerce支持部门能否解决阻止的管理员流量问题？

是，阻止的管理流量被视为优先级1问题。
