# 一个发票管理工具

## 使用说明

需要安装依赖，Wand库依赖
ImageMagick（ https://imagemagick.org/script/download.php ）
和
Ghostscript（ https://www.ghostscript.com/download/gsdnld.html ）。

Windows系统下在安装ImageMagick时记得勾选"Install development headers and libraries for C and C++ "选项。

装好依赖后命令行执行`python manage.py runserver`启动，然后就可以在 http://127.0.0.1:8000 里访问了，默认账号密码都是`admin`。

## 这个工具的起源

现在的老板们骚操作多，很多公司每个月都会有定额的福利，但需要拿发票去报销才能拿，于是就会有很多朋友碰到这样的问题：

- 由于日常生活中不会经常出去吃饭、打车或是买一些价格较高的物品，导致每个月收集到的发票都极为零散，而且有些是纸质发票、有些是电子发票，整理起来极其麻烦。
- 由于收集到的发票都是小额发票，而且各种类型都有，在有特定类型限制（比如说餐饮类多少、交通类多少）的情况下，需要将发票分门别类地整理好，并计算出该类型的总额，对着计算器一张一张敲金额敲到头疼。
- 如果每个月收集的发票会比较多的话，还可能会出现一张发票开了多次、发票抬头或税号错误的情况，一不留神可能就得重新找发票补上空缺金额。而且多了的发票还得流转到下个月继续使用，管理已使用和未使用的发票又是件麻烦事。
- 电子发票现在还无法实现纯数字化处理，所以整理好发票之后还得打印出来才行，一张一张打开、打印点到手酸。
- 等等...

其实不单单是我们，财务在处理这种事情的时候其实也很头疼，他们会碰到这样的问题：

- 有些人的发票金额没凑够，但报销单上写的却是完整的福利金额。
- 有些人的抬头或税号填错了，但他们自己却没有核对过。
- 有些人有部分发票的类型不符合要求，但他们却混着给了过来。
- 为了方便整理，电子发票要求按规定格式命名并打包发给财务，但有些人给的发票名很混乱，或者发票号之类的打错了。
- 等等...

这些其实都是很机械化的操作，但毕竟是涉及到钱的问题，必须得要严谨，所以我们和财务都需要对发票一个一个地进行查看、核实，无形之中大家都浪费了很多时间在做这些没有多大意义的事情上。

那么，有没有什么办法能解决呢？有，用发票管理工具就好了...吗？

### 理想与现实

如果你有调研过这种工具的情况的话，你会发现，虽然这种工具在专业的财务工具中基本都有，但由于对发票的处理只是财务工作的一部分，所以他们往往不会将这部分独立出来，而是作为自家产品的一个子功能。

但问题在于，这些产品往往年费高昂或是需要按照使用人数付费，对于中小企业而言，其实是没有必要为了这一个功能而付费的。毕竟...我们换位思考一下，作为一个企业的老板、股东，在人员不多的情况下，人工处理各种事务对财务来说不会有太大的负担，而对于其他员工来说，每个月就处理一次，还有钱拿，压根就不会说什么，那为什么还要为这种东西付钱呢？

而作为员工，即使自己觉得太麻烦了想省点事，为这种工具掏钱也仍然是没必要，毕竟这钱出了之后每个月也就用那么一两次，太亏了。

### 免费工具？

所以...有免费的发票管理工具吗？当然有，但问题更多，拿比较典型的在线工具举例，最直接、最明显的就是会涉及到隐私问题，毕竟你买了啥东西，在发票上可是一清二楚的，而这发票还是能精确到公司和个人的，你愿意舍弃掉这部分隐私吗？

还有是否付费使用也是个问题，免费的话别人服务器资源收不回来随时可能关站，加上这种工具使用频率很低，挂广告也不现实；

而付费的话，功能上总得比较有特色吧？得要人愿意买吧？如果定价太低，人家可能根本收不回开发各种特殊功能、推广等所花的时间成本，如果定价太高...和前面所说的中小企业的情况一样，你会愿意出钱吗？

### 自己动手

这个工具我很久以前就写了个纯命令行的版本，想着搞成网页并且加上各种功能的，但由于时间的问题一直没有搞，搁置了很久。

而很巧的是，华为云2020双十一想要我这边写篇使用它们服务的软文出来，于是，这个开源的发票管理工具应运而生，既能让我水两篇文章，又能把开发所花的时间成本所对应的金钱从他们手里拿到，何乐而不为呢？

## 目前已有功能

1. 发票自动识别、入库，避免人工一张一张输入进工具的操作。
2. 发票分类，用于区分不同类别的发票要求。
3. 发票总额计算，用于方便地凑到指定金额。
4. 去重，避免出现多张一样的发票。
5. 抬头、税号检测，避免出现开票开错抬头或税号的情况。
6. 自动排除已使用的发票，避免重复使用到旧的发票。
7. 批量打印，不然还得一张一张点开打印。
8. 自动导出已使用的发票并规范化命名，以方便财务收集。

## TODO

1. 自动读邮箱找到发票邮件，并提取其中的发票，实现几乎完全自动化的导入。
2. 将滴滴打车发票之类有多个文件的情况（比如行程单）处理一下，以实现像打车发票这种东西能将行程单一并导入、导出。
3. 发票使用时间限制设定以及快到限期的提示，避免发票被财务拒收。
4. 支持ofd和图片格式的导入，以解决部分奇葩开票系统不开PDF格式导致无法统一管理的问题。
5. 支持拍照导入纸质发票，以解决部分城市还未普及电子发票的问题。
6. 导出命名格式支持网页端配置，提升非技术人员的体验。
7. 打包成二进制格式，降低非技术人员的使用复杂度。
8. 支持多张发票合并到一张纸上打印，节省纸张。（正常一张纸打印一个发票的话需要折叠起来，如果多张的话撕开就可以直接贴发票了）
9. 支持将多张发票归于一次事务下，以方便出差、办事之类的场景下需要集中报销的情况。
10. 支持定期事务，以方便像每个月有餐饮费福利多少、请客户吃饭报销额度多少等场景的处理。
11. 自动按开票时间序列生成报销单并放入压缩包中，以方便部分公司财务要求有某个事务的整体报销单的情况。
12. 事务发票导出时压缩包自动规范化命名，以方便有多个事务时的区分。
13. ...

## 小广告

欢迎使用我们团队（NightTeam）的邀请链接或二维码进行注册，通过这个链接或二维码注册的帐号**会与我们团队（NightTeam）的帐号进行关联**。

关联后可以获得一些**直接注册无法获得的权益和福利**，并且在华为云搞促销活动时也能参与到一些**不对外公开的隐藏活动**（俗称暗促，一般是**打骨折的价格**...），强烈推荐关联注册一下。

注意，**注册后的帐号是无法关联分销商帐号的，只能重新注册。**

优惠相关信息可以在NightTeam公众号的菜单中点击聊一聊-加微信（快速通道）进行咨询。

邀请链接：https://account.huaweicloud.com/obmgr/invitation/invitation.html?bpName=0770da66a30025170f54c01c9831c7e0&inviteCode=invoice_manager&bindType=1&isDefault=0

邀请二维码：

![](./huaweicloud_register.png)

---

本项目为「NightTeam」成员 Loco 的原创系列文章《公司每个月整理发票报销太头疼？教你一招快速解决！》配套内容，如有相关问题，可在公众号「NightTeam」上发消息联系，也可发送邮件至 contact@nightteam.cn，我们会尽快回复你。

欢迎关注我们的公众号「NightTeam」，更多高质量文章都在这里：

![扫码关注NightTeam](./nightteam_qrcode.jpg)