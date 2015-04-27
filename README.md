<h1 align="center">
<sub>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/icon38@2x.png"
height="38"
width="38">
</sub>
uBlock Origin
</h1>
<p align="center">
<sup> <!-- Pronounciation -->
      读作 <i>you-block</i> (<code>/ˈjuːˌblɒk/</code>) — <i>你</i> 来决定什么可以进入浏览器。
</sup>
<br>
</p>

**支持多浏览器的高效过滤工具，快速、有效且简洁。**&nbsp;&nbsp;[<img src="https://travis-ci.org/gorhill/uBlock.svg?branch=master" height="12">](https://travis-ci.org/gorhill/uBlock)

* [用途和常规信息](#基础介绍)
* [文档](#文档)
* [性能和运行效率](#性能比较)
  * [内存占用](#内存占用)
  * [CPU 占用](#cpu-占用)
  * [屏蔽能力](#屏蔽能力)
  * [快速测试](#快速测试)
* [安装](#安装)
  * [Chromium](#chromium)
  * [Firefox](#firefox)
  * [Safari](#safari)
* [发布历史](#发布历史)
* [维基页面](https://github.com/fang5566/uBlock/wiki)

## 基础介绍

uBlock Origin（或uBlock₀）不是一个*广告过滤工具*，它是具有一般性用途的过滤工具，屏蔽广告的功能是通过支持 [Adblock Plus 过滤规则语法](https://adblockplus.org/zh_CN/filters)实现的。uBlock₀ 还[扩充](https://github.com/fang5566/uBlock/wiki/%E6%89%A9%E5%85%85%E7%9A%84%E8%BF%87%E6%BB%A4%E8%A7%84%E5%88%99%E8%AF%AD%E6%B3%95)了语法，一开始就支持自定义过滤规则。

这就是说，最重要的是知道使用过滤工具**不是**一种[偷窃行为](https://twitter.com/LeaVerou/status/518154828166725632)，别总抱着这种令人不爽的想法。_最终_在逻辑上`屏蔽 = 偷窃`会成立也是因为侵犯隐私权利而被定罪。

无论"温和"与否，现如今在您浏览大多数网站的时候广告都是最显而易见的侵犯隐私行为。**uBlock₀ 的主要目的是帮助用户抵御这种侵犯隐私的行为**，针对的是那些不想用更具技术、更复杂的方法（比如 [µMatrix](https://github.com/gorhill/uMatrix)）解决问题的用户。

uBlock₀ 安装后会默认开启 _EasyList_、_Peter Lowe's Adservers_、 _EasyPrivacy_ 和 _Malware domains_，此外还有许多过滤规则列表可以屏蔽跟踪、分析等行为，我们也支持根据 hosts 文件来屏蔽。

如果你发现 uBlock₀ 安装完后屏蔽太多内容，你可以很方便地取消任何预开启的过滤规则列表，参考 Adblock Plus 安装后默认只开启 _EasyList_。

## 文档

[快速指南：弹出界面](https://github.com/fang5566/uBlock/wiki/%E5%BF%AB%E9%80%9F%E6%8C%87%E5%8D%97%EF%BC%9A%E5%BC%B9%E5%87%BA%E7%95%8C%E9%9D%A2)

![弹出界面](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png)

你还可以了解[动态过滤](https://github.com/fang5566/uBlock/wiki/%E5%8A%A8%E6%80%81%E8%BF%87%E6%BB%A4)等高级功能，更多的高级用法参见 [uBlock₀ 的维基页面](https://github.com/fang5566/uBlock/wiki)。

## 性能比较

#### 内存占用

<div align="center">
相比平均值，uBlock₀ <b>的确</b>让你的浏览器运行起来更轻巧。<sup>[1]</sup><br><br>

Chromium <sup>[2]</sup><br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20141224.png" /><br>打开 11 个高流量网页时的总体内存占用(MB)（64 位 Chromium）<br><br>

Firefox<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20150205.png" /><br>打开 11 个高流量网页时 "Explicit Allocations" 中的内存占用（64 位 Firefox 35）<br><sup>**Bluhell 只使用到 EasyList 的一部分过滤规则，所以它的屏蔽能力明显弱于其他工具</sup><br><br>

Safari<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-safari-20150205.png" /><br>打开 11 个高流量网页时的总体内存占用（Safari 8.0）<br><br>

</div>

<sup>[1] 基准测试详细情况参见： <a href="https://github.com/fang5566/uBlock/wiki/Firefox-%E5%9C%A8%E5%9F%BA%E5%87%86%E6%B5%8B%E8%AF%95%E4%B8%AD%E7%9A%84%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E5%80%BC">Firefox 在基准测试中的内存占用值</a>。</sup><br>

<sup>[2] 重要提示：目前[Chromium 39+ 存在一个每次打开扩展弹出界面都会产生新的内存泄漏的 bug](https://code.google.com/p/chromium/issues/detail?id=441500)，会影响<i>所有</i>扩展，测量 Chromium 的内存占用时别忘了这点。我自己在测试中已避免完全打开弹出界面。</sup><br>

#### CPU 占用

<p align="center">
uBlock₀ 也让 CPU 更省心<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/cpu-usage-overall-chart-20141226.png" /><br>统计在基准测试中扩展本身累计的内存占用<br>基准测试中收集到的 CPU 占用率样本（每秒的百分比）总和<br>
<sup>基准测试详细情况参见：<a href="https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/cpu-usage-overall-20141226.ods">LibreOffice 电子表格</a>。</sup>
</p>

#### 屏蔽能力

<p align="center">
变得简洁高效并不意味着屏蔽得少<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/privex-201409-30.png" /><br>连接到第三方服务器的网络请求数量<br>柱状图越低表示越少连接到第三方服务器<br>
<sup>基准测试详细情况参见： 
<a href="https://github.com/fang5566/uBlock/wiki/uBlock-%E5%92%8C%E5%85%B6%E4%BB%96%E5%B7%A5%E5%85%B7%E5%9C%A8%E5%B1%8F%E8%94%BD%E5%B9%BF%E5%91%8A%E3%80%81%E8%B7%9F%E8%B8%AA%E8%A1%8C%E4%B8%BA%E5%92%8C%E6%81%B6%E6%84%8F%E5%9F%9F%E5%90%8D%E6%96%B9%E9%9D%A2%E7%9A%84%E6%AF%94%E8%BE%83">uBlock₀ 和其他工具在屏蔽广告、跟踪行为和恶意域名方面的比较</a>。
</p>

#### 快速测试

- [Index](http://raymondhill.net/ublock/tests.html)
- [Web page components](http://raymondhill.net/ublock/tiles1.html)
- [Popups](http://raymondhill.net/ublock/popup.html)

## 安装

你可以随意阅读一下[扩展需要获得的权限](https://github.com/fang5566/uBlock/wiki/%E5%85%B3%E4%BA%8E%E6%89%A9%E5%B1%95%E9%9C%80%E8%A6%81%E8%8E%B7%E5%BE%97%E7%9A%84%E6%9D%83%E9%99%90)。

#### Chromium

你可以打开[Chrome 网上应用店](https://chrome.google.com/webstore/detail/cjpalhdlnbpafiamejdnhcphjbkeiagm)或 [Opera 商店](https://addons.opera.com/en-gb/extensions/details/ublock/)来[手动](https://github.com/gorhill/uBlock/tree/master/dist#install)安装最新的版本。

#### Firefox

你可以到 [Firefox 附加组件主页](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)安装，或直接下载最新版本的 [uBlock.firefox.xpi](https://github.com/gorhill/uBlock/releases) 文件，将下载好的 `xpi` 文件拖动到附加组件管理器安装。

#### Safari

uBblock Origin 不支持 Safari

建议你安装[chrisaljoudi 的 uBlock](https://github.com/chrisaljoudi/uBlock)，它官方支持 Safari。

#### 所有浏览器的注意事项

为了能够真正感受到 uBlock Origin 的高效，建议你不要同时安装其他的广告过滤工具，比如 AdBlock 或 Adblock Plus，因为 uBlock₀ [绝不逊色于](#屏蔽能力)这些流行的广告过滤工具。

## 发布历史

你可以打开[发布页面](https://github.com/chrisaljoudi/uBlock/releases)了解所有发布历史以及每次发布时的关键更新。


## 关于

[uBlock Origin 的声明](MANIFESTO.md)

它是免费、开源的，属于用户也来自用户，无需任何捐助。

没有预置的规则列表，扩展什么事也做不到，所以如果你真心想尽一份力，不妨记住那些维护规则列表的人，是他们的努力才让我们能免费用上这些规则列表。

你可以通过协助翻译项目来尽一份力，项目托管在 [Crowdin](https://crowdin.net/project/ublock)。

## 许可协议

[GPLv3](https://github.com/gorhill/uBlock/blob/master/LICENSE.txt)
