[**Users Guide**](https://portals.apache.org/jetspeed-2/usersguide/index.html)

# 1. **用户手册**

## 1.1. **欢迎**

Jetspeed 是一个开放门户平台和企业信息门户，在 Apache 许可下以 Java 和 XML 完全以开源方式编写。Jetspeed 是一个基于标准的开放组件门户架构。对门户的所有访问都通过强大的门户安全策略进行管理。在 Jetspeed 门户中，可以聚合各个 portlet 以创建页面。每个 portlet 都是一个独立的应用程序，Jetspeed 充当中心枢纽，以易于使用的方式提供来自多个来源的信息。

基于 Jetspeed 的门户可以通过单个网站向最终用户提供应用程序、数据库信息和其他数据源。Jetspeed 提供了一个安全基础设施，以便每个用户可以使用的信息和功能可以根据用户或用户拥有的角色进行定制。用户可以通过 Web 浏览器、WAP 电话、寻呼机或 servlet 引擎支持的任何其他设备访问门户。

用户可以通过使用 portlet 定制器添加新内容、使用门户装饰器（皮肤）和布局设计他们的视图来个性化他们的体验。个性化与安全访问相结合，以提供基于运行时自定义和参数的门户自定义视图。

Jetspeed 提供以下个性化功能：

· Portlet Selector（搜索 Portlet、添加 Portlet、对 Portlet 进行分类）

· 门户定制器（移动 portlet、选择装饰、布局）

· 桌面定制器（与门户相同、拖放、调整大小、分离）

· Portlet API 首选项编辑器

· 行政定制

## 1.2. [**关于本指南**](https://portals.apache.org/jetspeed-2/usersguide/aboutuserguide.html)

本用户指南专为 Jetspeed 新手设计，或作为普通用户登录时浏览 Jetspeed 界面的参考。本指南旨在为那些希望继续学习管理员指南、部署者指南和开发者指南的人奠定基础。某些概念（例如安全性）可能会跨越多个指南，但会针对该特定指南的角色进行结构化。

阅读本指南后，用户将能够：

· 创建一个新用户

· 登录 Jetspeed

· 请求忘记密码

· 更改 Jetspeed 中使用的语言

· 最小化、最大化和恢复 portlet 窗口

· 编辑 portlet 的首选项

· 添加、移动和删除 portlet

· 更改 Jetspeed 的装饰器

· 更改单个 portlet 的装饰器

· 创建和删除选项卡

· 创建和删除文件夹

· 浏览菜单和页面

· 使用面包屑导航文件夹

· 在 Jetpeed 桌面和门户之间切换

· 使用 Jetspeed 桌面

· 退出 Jetspeed

### 1.2.1. **用户指南**

用户指南将不涵盖与管理员指南、部署者指南或开发者指南相关的方面。用户指南将重点介绍用户登录门户、在门户内导航和自定义门户外观的方法。包含重要词或概念的定义页面，这将使不熟悉 Portal 或 Jetspeed 的人更容易理解该指南。

### 1.2.2. **管理员指南**

管理员指南不会涵盖用户指南中涉及的主题。本指南将重点介绍在 Jetspeed 运行时可以更改的任何配置和管理选项。管理员将拥有通过管理 portlet 配置用户、组和角色的完全访问权限。

### 1.2.3. **部署者指南**

部署者指南不会涵盖用户或管理员指南中涉及的主题。本指南将解决 Jetspeed 运行时无法执行的管理和配置任务。本指南的一部分将专门介绍在 Websphere 上部署 Jetspeed。

### 1.2.4. **开发者指南**

开发人员指南不会涵盖用户、管理员或部署人员指南中涉及的主题。

## 1.3. [**定义**](https://portals.apache.org/jetspeed-2/usersguide/definitions.html)

此处列出了用户指南中提到的定义和概念以供参考。

### 1.3.1. **装饰器**

门户设计或皮肤在 Jetspeed 中被称为装饰器。它们也可以称为主题。
![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps68.jpg)

### 1.3.2. **门户网站**

“门户是一个基于 Web 的应用程序，它通常提供个性化、单点登录、来自不同来源的内容聚合并托管信息系统的表示层。聚合是在网页中集成来自不同来源的内容的操作。门户可能具有复杂的个性化功能，可以为用户提供定制的内容。门户页面可能有不同的 portlet 集，为不同的用户创建内容。” JSR-168:PLT.2.1

基于 Jetspeed 的门户可以通过单个网站向最终用户提供应用程序、数据库信息和其他数据源。Jetspeed 提供了一个安全基础设施，以便每个用户可以使用的信息和功能可以根据用户或用户拥有的角色进行定制。用户可以通过 Web 浏览器、WAP 电话、寻呼机或 servlet 引擎支持的任何其他设备访问门户。

### 1.3.3. **小门户**

“Portlet 是一种基于 Java 技术的 Web 组件，由 Portlet 容器管理，它处理请求并生成动态内容。Portlet 被门户用作可插入的用户界面组件，为信息系统提供表示层。” JSR-168:PLT.2.2

### 1.3.4. **Portlet 窗口图**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps69.jpg)

### 1.3.5. **角色**

角色是用户在与系统交互时可以扮演的角色。这允许系统按角色而不是单个用户定义行为。

### 1.3.6. **平铺窗口**

Jetspeed 中的平铺窗口是不与任何其他窗口重叠的窗口。

Jetspeed 中的平铺窗口是不与任何其他窗口重叠的窗口

### 1.3.7. **窗口状态**

窗口状态指示将分配给生成的 portlet 内容的门户页面空间量。

· 正常 - 表示 portlet 可能正在共享页面的呈现。

· 最小化——portlet 应该只呈现最少的输出或根本不呈现输出。

· 最大化 - 指示该 portlet 可能是唯一正在呈现的 portlet。在这种状态下，portlet 可能会生成更丰富的内容。

# 2. **使用 Jetspeed**

## 2.1. [**入门**](https://portals.apache.org/jetspeed-2/usersguide/gettingstarted.html)

如果您在计算机上本地运行 Jetspeed，您可以通过将 Internet Web 浏览器指向 http://localhost:8080 来访问门户。本指南使用的屏幕截图是从 Jetspeed 生成的，没有任何额外的自定义。您的屏幕可能会有所不同，具体取决于您登录的用户或您是否使用定制版本的 jetspeed。

您可能会将本指南用作在 Internet 上访问 Jetspeed 的补充。输入门户的 URL 以开始遵循本指南。

阅读完本页后，通过 Login Portlet 登录以开始使用 Jetspeed。

### 2.1.1. **初始显示窗口**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps70.jpg)

您遇到的第一个屏幕有几个可帮助您入门的 portlet。每个 Portlet 都有一个标题栏来按名称识别它。这些 portlet 可以最小化、最大化、移动到不同的位置或删除，我们将在本指南中进行介绍。

### 2.1.2. **Portlet：语言环境选择器**

Locale Selector Portlet 允许您选择希望门户使用的语言。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps71.jpg)

### 2.1.3. **Portlet：忘记密码**

忘记密码允许用户在丢失或忘记当前密码的情况下请求新密码。Jetspeed 将通过电子邮件将新密码发送到输入的电子邮件地址，前提是该地址可以与 Jetspeed 用户数据库中的注册用户匹配。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps72.jpg)

### 2.1.4. **Portlet：用户注册**

如果管理员未向您提供用户名和密码，则用户注册是您的第一步。Jetspeed 用户数据库中每个用户的用户名和电子邮件地址必须是唯一的。当用户首次注册或由管理员创建时，Jetspeed 使用“模板”为用户创建默认页面。

通过填写用户名、地址、密码和密码确认的必填字段，在用户注册 portlet 中创建一个新用户 单击注册我按钮，您已经创建了一个准备登录 Jetspeed 的用户。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps73.jpg)

### 2.1.5. **小门户：登录**

登录 Portlet 是您在 Jetspeed 中访问您的私人安全区域的途径。您在登录时对设置所做的任何更改只会影响您。登录后，您还将看到更改密码链接可用。

将登录 Portlet 中的用户名更改为您刚刚注册的用户名。输入区分大小写的密码，然后按登录按钮。屏幕将重新加载，您现在将进入 Jetspeed 的私人安全区域。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps74.jpg)

### 2.1.6. **以不同的用户或角色登录**

Jetspeed 对不同的用户有不同的看法，对不同的角色有不同的看法。下面的屏幕截图说明了基于经过身份验证的用户或角色的菜单更改方式。

以用户身份![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps75.jpg)登录 以管理员身份登录![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps76.jpg)

## 2.2. [**导航**](https://portals.apache.org/jetspeed-2/usersguide/portalnavigation.html)

选项卡式菜单、面包屑和菜单项是在门户中导航的主要方式。编辑、帮助和其他 portlet 栏操作项可以显示不同的屏幕，但您还没有导航到新位置。门户管理员可以配置所有导航项的自定义。

### 2.2.1. **选项卡式菜单**

顶部的选项卡式菜单包含当前文件夹中每个页面的选择。当前选项卡可能已预先配置为标准，也可能已由用户创建和配置。每个选项卡都可以配置不同的主题、布局、Portlet 主题和不同的 Portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps77.jpg)

### 2.2.2. **面包屑**

面包屑位于选项卡式菜单的正下方。面包屑为您提供到达当前位置的路径的可视化表示。从面包屑路径中，您可以从文件夹层次结构导航回之前的目的地。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps78.jpg)

### 2.2.3. **菜单项**

菜单项位于左侧菜单中。这些链接中的每一个都可以将您带到门户内的位置或外部位置，例如网站。您创建的文件夹将出现在此菜单中。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps79.jpg)

## 2.3. [**Portlet 模式和操作栏**](https://portals.apache.org/jetspeed-2/usersguide/portletmodes.html)

### 2.3.1. **Portlet 模式**

Portlet 模式指示 Portlet 正在执行的功能。Portlet 模式建议 Portlet 应该执行什么任务。Portlet 模式的可用性可能会受到用户角色的限制。

· 视图 - 一般的 portlet 呈现和交互。

· 编辑 - 自定义 portlet 的行为，更新首选项。

· 帮助 - 为这个 portlet 提供上下文相关的帮助。

· 自定义 Portlet 模式 - 特定于供应商。

### 2.3.2. **Portlet 操作栏**

portlet 操作栏![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps80.jpg)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps81.jpg)编辑图标将更改 portlet 窗口以显示该特定 portlet 的可配置首选项。例如，天气 portlet 可以为您提供更改其显示的城市的选项以及其他选项。每个 portlet 都有独特的首选项。可以显示两个或多个相同的 portlet，但每个 portlet 都将使用它自己的一组首选项。这将允许您拥有两个显示两个不同城市的天气的天气 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps82.jpg)帮助图标将显示一个页面，该页面显示有关如何使用 portlet、版本号或开发人员选择在此页面中显示的任何内容的详细信息。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps83.jpg)最小化图标会将您的 portlet 缩小为仅显示 portlet 的标题栏。 ![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps84.jpg)您可以单击可用于将 portlet 恢复到其原始窗口状态的恢复。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps85.jpg)最大化图标将放大 portlet 以在您的门户窗口中仅显示该 portlet。 ![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps86.jpg)在此模式下，恢复按钮将再次可用。

您可能在图标栏中看到的其他图标是![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps87.jpg)打印和其他自定义图标。

## 2.4. [**注销**](https://portals.apache.org/jetspeed-2/usersguide/logout.html)

### 2.4.1. **注销链接**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps88.jpg)注销链接位于 portlet 窗口正上方的右上角。

有多种方法可以结束您与 Jetspeed 的会话。最简单和最安全的方法是单击位于门户窗口右上角的注销链接。注销会将用户返回到 Jetspeed 欢迎页面，您可以在其中再次登录。

### 2.4.2. **会话超时**

会话超时发生在经过指定的时间后并且 Jetspeed 与浏览器之间没有发生交互。此设置可由管理员配置。在发生超时后的任何时间与 Jetspeed 交互都会导致用户看到 Jetspeed 欢迎页面。

### 2.4.3. **清除 Cookie**

清除浏览器 cookie 也会导致用户退出。在某些情况下，例如 SSO（单点登录），清除 cookie 可能是最安全的注销方式。

# 3. **定制**

## 3.1. [**装饰器**](https://portals.apache.org/jetspeed-2/usersguide/decorators.html)

· 门户设计或皮肤在 Jetspeed 中被称为装饰器。使用装饰器，您可以根据组织的品牌定制门户体验。

· 有两种不同类型的装饰器：页面装饰器和 Portlet 装饰器

o 页面装饰器装饰整个页面

o Portlet 装饰器 装饰器 单个 portlet

### 3.1.1. **页面装饰器**

· 每个 Jetspeed 页面都可以与不同的页面装饰相关联。也就是说，建议您在文件夹甚至根文件夹级别设置页面装饰。

· 装饰品继承。

· 页面装饰器控制页面的重要方面：

o 为页面设置皮肤的颜色、图像、CSS 样式。

o 页面的元信息，例如标题。

o 页面的品牌、企业形象、颜色。

o 显示操作按钮。

o 菜单和导航元素。

### 3.1.2. **Portlet 装饰器**

· 页面上的每个 Jetspeed portlet 窗口都可以与不同的 portlet 装饰相关联。

· Portlet 装饰控制 Portlet 窗口的一些重要方面：

o 显示此窗口的颜色、图像、CSS 样式。

o portlet 的标题部分。

o 窗口的边框。

o 显示操作按钮。

在 Jetspeed 门户窗口的右上角，您将看到一个注销链接，后跟两个图标。第一个图标是编辑图标，在这种情况下，它是我们访问整个门户窗口自定义选项的方法。单击铅笔（编辑）图标![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps89.jpg)，您现在应该会看到类似于下图的页面。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps90.jpg)

### 3.1.3. **页面/文件夹定制器**

Page/Folder Customizer 部分有三个选项供我们配置。主题将为门户窗口的选项卡、菜单和窗口本身设置装饰器。布局将允许我们更改 Jetspeed 窗口中的列数。Portlet 主题是门户窗口中包含的所有 Portlet 的全局设置。此全局设置可以被窗口中的各个 portlet 覆盖。如果您不设置单独的 portlet 装饰器，它们将从本节继承 Portlet 主题。Tigris 是标准 jetspeed 安装的默认装饰器。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps91.png)![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps92.jpg)![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps93.jpg)

请注意，主题下拉菜单不需要按下更改按钮即可使您的选择变为活动状态。从下拉菜单中选择一个选项后，Jetspeed 将根据您的选择呈现窗口。只有布局受到影响，portlet 窗口不受影响。

### 3.1.4. **布局定制器**

布局允许您为整个窗口选择多列布局或单列。Jetspeed 在更改此布局时会记住 portlet 的位置。更改布局以将所有 portlet 放入四列并更改回两列将使 portlet 返回到其原始列。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps94.jpg)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps95.jpg)![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps96.jpg)

添加布局将在带有 portlet 的窗口中插入布局选项。这允许您在一列中设置多个列。单击添加布局，在我们之前的示例中的书签 Portlet 2 下方添加了一个新的页面/定制器选项。用户现在可以使用提供的选项在布局中自定义这个新布局。您还会注意到箭头图标和 X 图标。这些将在定制的 Portlets 部分中讨论，但它们用于移动和删除 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps97.jpg)

### 3.1.5. **Portlet 主题定制器**

Portlet Theme 将为窗口中的所有 Portlet 设置装饰器。如果您在 portlet 上设置了单独的装饰器，这会将窗口中的所有 portlet 重置为您选择的 portlet 主题。如果您希望它们具有不同的装饰器，则必须在选择此选项后重新设置各个 portlet。要使 Layout 和 Portlet 都使用相同的主题，您必须将它们设置为相同的装饰器。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps98.jpg)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps99.jpg)![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps100.jpg)

## 3.2. [**小门户**](https://portals.apache.org/jetspeed-2/usersguide/portlets.html)

在门户窗口的编辑模式下，您会注意到页面上的每个 portlet 现在都有几个自定义选项。用于更改单个 portlet 的装饰器的下拉菜单选项、![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps101.jpg)用于移除 portlet 的图标栏或用于将 portlet 沿箭头方向移动一个位置的箭头。对于不可访问的资源，不会显示菜单。

每个 portlet 都可以拥有自己的装饰器，该装饰器将覆盖在门户窗口部分中选择的装饰器。但是，在页面/文件夹定制器中选择一个新主题会将所有 portlet 更改为该主题，无论它们是否被赋予了单独的主题。如果您已全局设置主题，您将需要再次更改各个 portlet 主题以使 portlet 显示它们自己的主题。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps102.jpg)

### 3.2.1. **移动 Portlet**

根据它们在窗口中的当前位置，箭头可用于跨列或在列中上下移动您的 portlet。Portlet 将针对每次移动进行自动调整。

在单击日历 Portlet 的右箭头之前。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps103.jpg)

单击日历 Portlet 的右箭头后。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps104.jpg)

### 3.2.2. **删除 Portlet**

要从您的窗口中删除一个 portlet，请单击您要删除的 portlet 的![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps105.jpg)图标。如果同一列中有任何较低的 portlet，其余 portlet 将进行调整以填充空间。

### 3.2.3. **添加 Portlet**

单击右上角的添加 Portlet。 ![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps106.jpg)

Portlet Selector 显示可添加的 Portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps107.png)

您可以使用带编号的链接浏览多个页面。 ![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps108.jpg)

有一个搜索字段，您可以在其中按名称搜索 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps109.jpg)

Portlet 也被分成不同的类别。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps110.jpg)

portlet 选择器显示 portlet 的名称、简要说明、添加选项和当前正在运行的 portlet 实例数量的计数器。单击添加链接将使计数器增加 1，但此时不会发生其他可见更改。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps111.jpg)

单击 [GoBack] 选项或箭头将带您进入原始定制窗口，您可以在该窗口中看到您的 portlet 已添加到您的 portlet 窗口中。如果您更改了默认装饰器的装饰器，您可能会发现新的 portlet 使用的是不同的装饰器，而不是您现在使用的装饰器。

在看到恢复选项以离开配置区域之前，您需要先返回到原始自定义窗口。

## 3.3. [**标签**](https://portals.apache.org/jetspeed-2/usersguide/tabs.html)

页面配置区域允许您创建用于在窗口顶部创建新页面的选项卡。输入页面名称、标题和短标题。短标题字段将是窗口中选项卡的名称。创建选项卡后，您可以更改名称、向左或向右移动页面或删除页面。您必须在字段中输入一些信息才能使这些按钮起作用。仅使用短标题字段即可。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps112.jpg)

创建页面后，您还可以更改窗口的装饰器主题、更改布局列并设置全局 Portlet 主题。将 Portlet 添加到您的页面，您现在拥有一个只能由您查看的新页面，并且与任何其他页面完全分开。添加 Portlet 包含在定制的 Portlet 部分中。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps113.jpg)

## 3.4. [**菜单**](https://portals.apache.org/jetspeed-2/usersguide/menu.html)

门户窗口的左侧菜单包含额外的导航项。链接、页面和文件夹是预配置的链接，可以根据个人的角色或组而有所不同。您可以使用文件夹配置选项添加新文件夹。输入文件夹名称、标题和短标题。短标题将用于左侧菜单中的文件夹名称。文件夹名称将是您在菜单中单击文件夹名称时出现的窗口中选项卡的名称。创建文件夹后，您可以更改名称、向左或向右移动文件夹或删除文件夹。您必须在字段中输入一些信息才能使这些按钮起作用。仅使用短标题字段即可。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps114.jpg)

您可以添加其他文件夹、在文件夹中添加文件夹以及在每个文件夹中添加选项卡。每个新文件夹都会创建一个新的空白页面，然后您可以通过更改主题、布局、Portlet 主题和添加 Portlet 来自定义该页面。当您单击文件夹名称时，左侧的菜单和顶部的选项卡栏将发生变化。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps115.jpg)

最左侧选项卡下方的面包屑栏为您提供返回用户主页的导航链接。

## 3.5. [**桌面**](https://portals.apache.org/jetspeed-2/usersguide/desktop.html)

Jetspeed 启动后，Jetspeed Desktop 和 Jetspeed Portal 同时运行。在两者之间来回切换就像在 Web 浏览器中更改 URL 一样简单。我们的示例一直使用 http://localhost:8080/jetspeed/portal 作为访问门户的 url。将 url 更改为 http://localhost:8080/jetspeed/desktop 并回车。如果您在更改 url 之前已登录，您现在将在 Jetspeed Desktop 中并且当前已登录。

Jetspeed 桌面使用Web 2.0 技术。与 Jetspeed 门户不同，屏幕更新仅在需要时进行。当对任何 portlet 进行更改时，Jetspeed 门户必须呈现整个屏幕。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps116.jpg)

更新部分屏幕并不是两者之间的唯一区别。用户无需进入编辑模式即可将 portlet 拖放到新位置。单击并按住任何 portlet 的标题栏上的鼠标按钮，可以将 portlet 移动到 portlet 允许区域中的任何位置。Portlet 将在您移动它们时自动调整。

现在，最小化和最大化选项旁边有一个新图标。此自定义图标可以包含编辑和帮助链接以及其他选项。当您处于帮助和编辑模式时，视图是一种正常的 portlet 模式，就像恢复一样，现在是一个选项。通过此图标可以使用几个选项：

· Portlet 窗口的平铺和平铺

· 可变高度选项和适合窗口

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps117.jpg)

Portlet 首选项可通过编辑图标获得，就像在 Jetspeed Portal 中一样。

Jetspeed 中的平铺窗口是不与任何其他窗口重叠的窗口。平铺 portlet 会将 portlet 窗口与其他 portlet 一起移动到布局结构中，这是默认选项。直到portlet 将portlet 移动到其他portlet 的前面或顶部。在标题栏上单击并按住鼠标将允许您将 portlet 放置在浏览器窗口中的任何位置而不受限制。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps118.jpg)

根据窗口的高度，无论是否被修改，您都会在高度选项下选择适合内容或变量。适合内容将围绕该 portlet 窗口中的所有数据调整 portlet 的大小。变量，默认选项，如果内容超过当前窗口大小，则为您提供一个可滚动的窗口。您还可以在适合内容模式或变量模式下使用位于 portlet 窗口右下角的调整大小箭头来调整 portlet 的高度。

添加 Portlet 不再需要您进入门户窗口的编辑模式。加号图标现在在门户窗口中显示为标准，并将直接将您带到 Portlet 选择器。单击箭头或 [GoBack] 将带您回到正常的门户窗口

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps119.jpg)

帮助页面可通过帮助图标访问，就像在 Jetspeed Portal 中一样。

# 4. **支持**

## 4.1. [**邮件列表**](https://portals.apache.org/jetspeed-2/mail-lists.html)

这些是为此项目建立的邮件列表。对于每个列表，都有一个订阅、取消订阅和一个存档链接。


| **姓名**             | **订阅**                                                  | **退订**                                                    | **邮政**                                        | **档案**                                                                               |
| -------------------- | --------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------- | -------------------------------------------------------------------------------------- |
| Jetspeed 2用户列表   | [订阅](mailto:jetspeed-user-subscribe@portals.apache.org) | [退订](mailto:jetspeed-user-unsubscribe@portals.apache.org) | [邮政](mailto:jetspeed-user@portals.apache.org) | [邮件存档.apache.org](http://mail-archives.apache.org/mod_mbox/portals-jetspeed-user/) |
| Jetspeed 2开发者列表 | [订阅](mailto:jetspeed-dev-subscribe@portals.apache.org)  | [退订](mailto:jetspeed-dev-unsubscribe@portals.apache.org)  | [邮政](mailto:jetspeed-dev@portals.apache.org)  | [邮件存档.apache.org](http://mail-archives.apache.org/mod_mbox/portals-jetspeed-dev/)  |

## 4.2. [**错误数据库**](https://portals.apache.org/jetspeed-2/issue-tracking.html)

该项目使用[JIRA](http://www.atlassian.com/software/jira)一个基于 J2EE 的问题跟踪和项目管理应用程序。

### 4.2.1. **问题跟踪**

问题、错误和功能请求应提交到该项目的以下问题跟踪系统。

[http://issues.apache.org/jira/browse/JS2](http://issues.apache.org/jira/browse/JS2)

## 4.3. [**维基**](http://wiki.apache.org/portals/Jetspeed2)

## 4.4. [**常问问题**](https://portals.apache.org/jetspeed-2/faq.html)

有几种方法可以创建新用户、角色和组：

· 使用管理用户/角色/组浏览器/详细信息 portlet

· 使用自注册 portlet

· 使用 Jetspeed 种子数据

· 以编程方式编写自己的 portlet

### 4.4.1. **管理门户**

使用管理 portlet 创建新用户很容易：

· 以管理员身份登录（默认密码为管理员）

· 从 LHS 菜单，导航到**Jetspeed 管理 Portlets**链接

· 用户管理页面是顶部管理菜单上的第一个选项卡

· 在这里您可以看到左侧的用户浏览器和右侧的用户详细信息

从这里您可以创建一个新用户。选择一个没有空格的唯一用户名。然后输入安全密码。您可以要求在首次登录时更改密码。您还可以选择分配给该用户的默认角色以及默认分析规则。最后，您可以将此用户分配给子站点

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps120.jpg)

进入编辑模式，您将进一步配置用户详细信息 portlet。请注意，可以默认以下字段：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps121.jpg)

· 新用户的默认角色

· 新用户所需的角色（未在查看模式下显示）

· 新用户的默认配置文件

· 新用户模板目录 - 留空不使用模板

· 子站点根文件夹

· 新用户的默认子站点

用户详细信息配置对于委派的安全方案很有用。例如，为所有具有*开发人员*角色的用户设置用户管理页面。*首先，在Developer*上将 User Browser 首选项设置为 FilterByRole 。然后，您可以为新开发人员分配默认角色、所需角色、新用户模板和子站点区域，由具有*DeveloperManager*角色的用户管理。然后，该用户只能创建具有正确角色和用户模板的开发人员类型用户。User Details portlet 的编辑模式可以得到保护，全局管理员只能编辑配置，限制开发经理只能创建或删除开发人员

组和角色管理页面的工作方式与用户管理页面类似。您可以添加/编辑/删除组和角色

### 4.4.2. **自注册 portlet**

最终用户也可以在门户中创建用户，无需管理操作。自助注册可能是门户网站中自定义程度最高的领域之一，因为所有门户网站对自助注册都有不同的要求。自注册 Portlet 还具有可由管理员配置的首选项：

· 一个或多个组的列表

· 一个或多个角色的列表，以逗号分隔

· 子站点根文件夹

· 是否发送电子邮件通知的布尔标志

· 一个新的用户模板

· 分析规则名称和值以逗号分隔
