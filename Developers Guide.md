# 1. [**Developers Guide**](https://portals.apache.org/jetspeed-2/devguide/index.html)

## 1.1. **开发 Jetspeed**

使用 Jetspeed 进行开发时，您可能正在创建 portlet 应用程序，或者构建和创建 Jetspeed 门户的扩展。如果您要创建 portlet 应用程序，请查看这本精美的电子书，了解编写 portlet 的总体指南：

· [Portlet 和 Apache 门户书籍](http://www.manning.com/hepper/)

Jetspeed 开发人员的核心团队直接使用源代码，构建最新版本的 Jetpeed。我们欢迎所有软件开发人员与我们合作。但是，完整的开发过程可能会超出您的需求。如果您只是想创建和构建自定义的 Jetspeed 门户并对其进行扩展，请查看下面的*自定义构建*部分。如果您想更多地参与并开始为 Jetspeed 做出贡献，请参阅下面关于*从源代码构建的部分*

开始开发 Jetspeed 的最佳地点是阅读我们的[构建指南](https://portals.apache.org/jetspeed-2/buildguide/index.html)

从 Jetspeed 2.3.0 开始，所有 Jetspeed 构建都使用 Maven-3。

### 1.1.1. **使用 Maven 插件进行自定义构建**

使用 Jetspeed 自定义构建，您实际上可以在没有 Jetspeed 源的情况下构建自己的门户。您将希望自定义您的 Jetspeed 构建，覆盖皮肤和主题，添加您自己的 portlet 应用程序，并且可能覆盖门户的关键组件。为此，我们提供了一个扩展 Maven-2 的自定义构建框架。

通过自定义构建，您可以轻松构建和创建自己的 Jetspeed 驱动门户，而无需构建 Jetspeed 本身。

创建 Jetspeed 的自定义构建可能是 Jetspeed 最常见的用法。可以在此处找到使用自定义构建和插件的文档：

· [使用 Maven 的 Jetspeed 自定义构建](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-archetype.html)

### 1.1.2. **从源头构建**

如果您需要构建源代码，请参考构建指南：

· [使用 Maven-2 从源代码构建 Jetspeed](https://portals.apache.org/jetspeed-2/buildguide/maven-2-build.html)

Jetspeed 是使用 Maven 从命令行构建的。但是，您仍然可以在 Eclipse 中进行开发、编译、调试、远程调试。Eclipse 是用于开发 portlet 应用程序以及 Jetspeed 扩展的好工具。

· [使用 Eclipse 进行开发](https://portals.apache.org/jetspeed-2/devguide/jetspeed-eclipse.html)

要获得官方 Jetspeed 版本的二进制安装，请转到此处：

· [获取二进制安装程序](https://portals.apache.org/jetspeed-2/download.html)

您可以从此处从 SVN HEAD 结帐：

· [从 Subversion 查看源代码](http://svn.apache.org/repos/asf/portals/jetspeed-2/portal/trunk/)

在此处获取您的 Javadocs：

· [Portlet API 文档](http://www.bluesunrise.com/portlet-api/index.html)

· [Jetspeed API 文档](https://portals.apache.org/jetspeed-2/apidocs/index.html)

### 1.1.3. **教程**

本教程将所有内容放在一起：自定义构建、portlet 开发、部署。您可以在此处找到 Jetspeed 教程：

[Jetspeed 教程](https://portals.apache.org/jetspeed-2/tutorial/index.html)

### 1.1.4. [**发送补丁**](https://portals.apache.org/jetspeed-2/devguide/patches.html)

### 1.1.5. [**编码标准**](http://portals.apache.org/development/code-standards.html)

# 2. **构建****Jetspeed**

## 2.1. [**构建指南**](https://portals.apache.org/jetspeed-2/buildguide/index.html)

### 2.1.1. **构建指南**

#### 2.1.1.1. **概述**

从 2.3 版开始，Jetspeed-2 构建系统完全基于[Apache Maven 3](http://maven.apache.org/)。

这意味着为 Jetspeed 项目开发人员以及自定义门户开发人员和系统集成商提供了一个遵循 Maven 2 构建框架的标准指南的标准化、可插拔和可配置的构建环境。

Jetspeed-2 Portal 本身是一个应用程序以及一个基于非常灵活的组件架构的门户框架，该架构是使用 [Spring Framework](http://www.springframework.org/)在运行时“组装”和配置的。Jetspeed-2 Portal 的主要特点之一是它可以针对非常潜水员和特定要求进行调整和配置。为了能够将 这些功能用于自定义门户项目，配置 Jetspeed-2 以针对许多不同的目标环境进行组装和集成还需要非常灵活的构建和配置工具集 。

**Maven 插件**

“标准”Maven-2 工具集足以构建和动态解析 （自定义）Jetspeed-2 门户所需的大多数组件和工件。但是在您的特定项目环境中配置和集成Jetspeed-2 通常远远超出构建它的范围。

设置后端数据库并与之交互，为特定目标部署环境创建和维护多个门户配置，不仅“只是”部署门户战争，而且在运行时所需的一切，大多是“超出范围”的标准 Maven-2 工具集。

为了能够满足如此复杂的集成要求（来自 Jetspeed-2 项目 POV）并仍然利用 Maven 2 工具集，已经编写了一些自定义 Maven“插件”来提供数据库初始化、门户配置和门户部署等功能可以在标准的 Maven 2 构建环境中配置和使用。

Jetspeed Maven 主插件 jetspeed:mvn 编排其他 Jetspeed 插件的使用的基本原理在 [自定义 Maven 生命周期的需求中进行了](https://portals.apache.org/jetspeed-2/buildguide/the-need-for-a-custom-lifecycle.html)描述。

每个 Maven 插件的详细文档和配置通过插件菜单 的[插件概述](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-maven-plugins.html)和相应的插件页面提供。

如何使用这些插件从源代码构建 Jetspeed-2，在**Building Jetspeed**菜单 的[From Source](https://portals.apache.org/jetspeed-2/buildguide/maven-2-build.html)页面上提供。

**使用 Jetspeed 原型快速启动新的自定义门户项目**

从每个插件提供的更详细的描述及其用法中可以清楚地看出，手动设置和配置一个完整的（自定义）Jetspeed Portal 项目绝非易事，需要执行相当多的步骤。

然而，在大多数情况下， 基本的[项目布局和配置是相同的。](https://portals.apache.org/jetspeed-2/buildguide/project-layout.html)

设置初始构建项目配置的一种快速简便的方法是使用**Jetspeed Archetype Maven **插件，在Building Jetspeed菜单 的[Jetspeed Archetype](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-archetype.html)页面上提供了详细描述和使用方法。

**先决条件：Maven Settings pluginGroups 的配置**

从命令行使用非标准 Maven 插件（例如，不由 Maven 或 CodeHaus 插件项目本身提供）需要插件坐标和执行目标的完全限定规范。在大多数情况下，这需要繁琐、容易出错和冗长的输入！

例如，对于 Jetspeed-2 Maven 插件，调用[jetspeed:mvn](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-maven-plugins.html)插件需要以下内容：

$mvn org.apache.portals.jetspeed-2:jetspeed:mvn -Dtarget=demo

然而，这可以通过在您的用户 Maven 设置中配置如何自动解析（附加）插件组来简化，而无需在命令上指定完整的插件 groupId 坐标。

另请参阅[Maven 设置](http://maven.apache.org/settings.html)的主要文档。

因此，建议将 Jetspeed-2 Maven 插件 groupId 添加到您的用户 Maven settings.xml 中的 pluginGroups 中，并在整个 Jetspeed-2 文档中给出的所有示例用法中都假定了这一点。

可以在以下位置找到用户 Maven settings.xml：（**\${user.home}/.m2/settings.xml**如果尚不存在，请创建一个）。

Jetspeed-2 groupId**org.apache.portals.jetspeed-2**需要作为 pluginGroup 定义添加到您的用户 settings.xml 中，如下所示：

<?xml 版本="1.0" 编码="UTF-8"?>

<settings xmlns="http://maven.apache.org/POM/4.0.0">

<插件组>

<pluginGroup>org.apache.portals.jetspeed-2</pluginGroup>

...
</pluginGroups>

...

</设置>

定义 Jetspeed-2 pluginGroup 后，如上所示的示例命令行执行可以简化为：

$mvn jetspeed:mvn -Dtarget=demo

#### 2.1.1.2. [**项目布局**](https://portals.apache.org/jetspeed-2/buildguide/project-layout.html)

一个典型的自定义 Jetspeed 门户项目通常包含一个用于构建和配置自定义 Jetspeed 门户本身的模块（子项目）以及一个或多个用于部署到 Jetspeed 门户的 portlet 应用程序的模块。

以下标准项目布局作为最佳实践提供，并符合标准 Maven 项目指南。它还可以轻松扩展和定制，以将未来的更改纳入项目目标和要求。

[Jetspeed Archetype](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-archetype.html) Maven 插件可用作设置新的自定义 Jetspeed Portal 项目的快速入门，并将使用此标准布局创建项目结构 。此外，它将包含 [Jetspeed Maven 插件](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-maven-plugins.html)的典型和默认设置和配置，用于使用 Maven 本身自动执行常见的门户部署和集成任务。

**主项目**

为了支持所有或大部分单个 (Maven) 项目工件和 (Jetspeed) 集成任务的集中管理和配置，使用 <packaging>pom</packaging> 类型的主/根 Maven 项目 pom.xml。

这个根项目将包含一个或多个模块（子项目），这些模块将把这个根项目定义为它们的父项目。这样，所有工件都可以直接从根项目构建和安装，并且可以使用[jetspeed:mvn 插件](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html)从该项目结构中的任何位置执行 (Jetspeed) 集成任务。

除了“标准”pom.xml 项目文件之外，还可以定义一个或多个自定义 jetspeed-mvn-${target name}-pom.xml 项目文件，以及相应的 jetspeed-mvn[... ].properties 文件，甚至使用 jetspeed-mvn-settings.xml 文件自定义覆盖 Maven 用户 settings.xml。

自定义 jetspeed-mvn[...].properties 和自定义 jetspeed-mvn-settings.xml 文件将作为默认配置，如果子项目在执行时不自己提供这些配置，则会通过项目父链自动查找这些配置jetspeed [:mvn](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-maven-plugins.html) 针对子项目调用目标任务。

**门户子项目模块**

为了构建和配置自定义 Jetspeed 门户本身，以及配置和运行 Jetspeed 门户特定的集成任务，根项目包含一个“门户”子项目模块。由于 Jetspeed 门户“只是”一个 Web 应用程序，因此 <packaging>war</packaging> 用于其 pom.xml。

为了构建自定义 Jetspeed Portal 战争工件，在 pom.xml 中使用了战争覆盖机制，使用 Jetspeed-2 提供的 **org.apache.portals.jetspeed-2:jetspeed:war**工件作为覆盖。注意：此 jetspeed 战争仅包含默认（演示）Jetspeed Portal Web 应用程序资源。

为了拉入所需的门户应用程序 jar 依赖项（放在其 WEB-INF/lib 下）文件夹，pom.xml 包含对 **org.apache.portals.jetspeed-2:jetspeed-dependencies:pom**工件的依赖项。

将依赖项与默认的 jetspeed 应用程序战争分开的好处是，jetspeed-dependencies 依赖项本身可以在 pom.xml 中进一步限制或覆盖。当这些依赖项被合并到默认的 jetspeed 战争中时，这是不可能的（使用标准的 Maven 配置）。

**Portlet 应用程序子项目模块**

为了构建要在自定义 Jetspeed 门户上部署的其他 portlet 应用程序，可以将一个或多个额外的“portlet application”子项目模块添加到根项目（注意：“portlet application”的常用缩写是“pa”）。由于 pa 也“只是”一个 Web 应用程序，因此 <packaging>war</packaging> 再次用于他们的 pom.xml。

而且，与门户模块一样，除了“标准”pom.xml 之外，pa 模块还可以包含一个或多个自定义 jetspeed-mvn-${target name}-pom.xml 项目文件，以及相应的 jetspeed -mvn[...].properties 甚至使用（特定于模块的）jetspeed-settings.xml 文件对 Maven 用户 settings.xml 进行自定义覆盖。

对于 portlet 应用程序模块，这确实是可选的并且通常不需要，因为通常只需要部署 pa 战争文件。

然而，可能需要额外集成任务的常见用例是当 pa 定义和使用需要设置/创建/升级或其他任何内容的自定义数据库后端（或类似：ldap、JCR 等）时。如果可以使用适当的 Maven 插件来执行此类集成任务（例如，像[jetspeed-db:init 插件），那么使用](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html)[jetspeed:mvn 插件](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html)标准化和自动化此类任务的执行应该非常容易。

**概念性的项目布局和内容**

使用上述规范，可概念化的自定义 Jetspeed 门户布局及其内容将如下所示：

/我的门户项目

| pom.xml // my-portal 项目的标准 maven 根 pom

| jetspeed-mvn.settings.xml // 项目范围的 Maven 设置配置用于 jetspeed:mvn 目标执行

| jetspeed-mvn-<target name>-pom.xml // 自定义 pom 为全局/通用 jetspeed:mvn 目标提供“构建”任务

| jetspeed-mvn.properties // jetspeed:mvn 目标执行的默认属性

| jetspeed-mvn-${target name}.properties //jetspeed:mvn target 执行的默认 ${target name} 特定属性

| jetspeed-mvn-${target name}-${target id}.properties //jetspeed:mvn target 执行的默认 ${target id} 特定属性

+ /我的门户

  | pom.xml // 使用战争覆盖机制的标准 maven my-portal 战争 pom

  | jetspeed-mvn.settings.xml // my-portal 范围内的 Maven 设置配置，用于 jetspeed:mvn 目标执行

  | jetspeed-mvn-${target name}-pom.xml // 自定义 pom 为 my-portal 特定的 jetspeed:mvn 目标提供“构建”任务

  | jetspeed-mvn.properties // 用于 jetspeed:mvn 目标执行的 my-portal 特定属性

  | jetspeed-mvn-${target name}.properties // 用于 jetspeed:mvn 目标执行的 my-portal 和 ${target name} 特定属性

  | jetspeed-mvn-${target name}-${target id}.properties // 用于 jetspeed:mvn 目标执行的 my-portal 和 ${target id} 特定属性
+ /我的-pa1

  | pom.xml // 标准 maven my-pa1 战争 pom

  | jetspeed-mvn.settings.xml // my-pa1 范围内的 Maven 设置配置用于 jetspeed:mvn 目标执行

  | jetspeed-mvn-${target name}-pom.xml // 自定义 pom 为 my-pa1 特定 jetspeed:mvn 目标提供“构建”任务

  | jetspeed-mvn.properties // my-pa1 jetspeed:mvn 目标执行的特定属性

  | jetspeed-mvn-${target name}.properties // my-pa1 和 ${target name} 特定属性，用于 jetspeed:mvn 目标执行

  | jetspeed-mvn-${target name}-${target id}.properties // my-pa1 和 ${target id} jetspeed:mvn 目标执行的特定属性
+ /我的-pa2

  | pom.xml // 标准 maven my-pa2 战争 pom

  | jetspeed-mvn.settings.xml // my-pa2 范围内的 Maven 设置配置用于 jetspeed:mvn 目标执行

  | jetspeed-mvn-${target name}-pom.xml // 自定义 pom 为 my-pa2 特定的 jetspeed:mvn 目标提供“构建”任务

  | jetspeed-mvn.properties // 用于 jetspeed:mvn 目标执行的 my-pa2 特定属性

  | jetspeed-mvn-${target name}.properties // my-pa2 和 ${target name} jetspeed:mvn 目标执行的特定属性

  | jetspeed-mvn-${target name}-${target id}.properties // my-pa2 和 ${target id} jetspeed:mvn 目标执行的特定属性

**典型项目布局和内容**

实际上，并非所有上述可能的布局结构和文件都需要。

典型的自定义 Jetspeed Portal 项目要简单得多，如下所示：

/我的门户项目

| pom.xml // my-portal 项目的标准 maven 根 pom

| jetspeed-mvn.settings.xml // 项目仅用于 jetspeed:mvn 目标执行的 Maven 设置配置

| jetspeed-mvn-prod.settings.xml.sample // 仅可选项目 Maven 生产设置 *sample* 配置用于 jetspeed:mvn 目标执行：

                                       // 通常，生产设置包含不应包含的安全敏感参数

                                       // 致力于版本控制系统和具体的 jetspeed-mvn-prod.settings.xml 将

                                       // 不允许提交。

                                       // 示例配置然后只提供一个模板以复制到 jetspeed-mvn-settings.xml

                                       // 并由开发人员/部署人员在本地进一步配置。
| jetspeed-mvn.properties // 用于 jetspeed:mvn 目标执行的可选（默认）属性

+ /我的门户

  | pom.xml // 使用战争覆盖机制的标准 maven my-portal war pom

  | jetspeed-mvn-portal-pom.xml // 自定义 pom 为 my-portal 特定的 jetspeed:mvn 目标提供所有“构建”任务，例如使用 jetspeed-db 和 jetspeed-deploy 插件
+ /我的爸爸

  | pom.xml // 标准 maven my-pa 战争 pom

  | jetspeed-mvn-pa-pom.xml // 自定义 pom 为 my-pa 特定的 jetspeed:mvn 目标提供所有“构建”任务，例如使用 jetspeed-deploy 插件

上面的示例项目布局是[Jetspeed Archetype](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-archetype.html) Maven 插件（部分）生成的，其中“my-”前缀和 maven 工件坐标（groupId、artifactId、version）是可配置的。

#### 2.1.1.3. [**门户资源**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-portal-resources.html)

Jetspeed-2 Portal作为一个门户框架，提供了许多可选功能和配置元素，其中一些甚至在 Jetspeed-2 Portal 项目本身的构建（和测试）期间使用。

此外，由于 Jetspeed-2 门户的高度可定制配置，并非所有可用资源和配置文件都不需要也不希望为每个目标环境使用和打包。

由于这些原因，Jetspeed-2 Portal 项目提供了作为 Maven 工件的预打包资源**jetspeed-portal-resources:jar**，它可用于仅选择性地使用（解包）特定目标（工件）或集成任务所需的资源。

**jetspeed-portal-resources:jar**工件 提供的重要且常用的资源有：

· 弹簧配置（/装配）

· 数据库架构定义 (/ddl-schema)

· 预生成的数据库 ddl 脚本 (/ddl)

· 门户和应用程序服务器属性和配置文件 (/conf)

· 预定义的最小和示例数据库初始化数据 (/seed)

[jetspeed-unpack:unpack](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-unpack-plugin.html)和[jetspeed-db:init](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html)插件 都可以从资源档案中“解包”选定的资源，如**jetspeed-portal-resources:jar**工件。

#### 2.1.1.4. [**自定义 Maven 生命周期**](https://portals.apache.org/jetspeed-2/buildguide/the-need-for-a-custom-lifecycle.html)

一个标准的 Maven 2.0 项目提供了 3 个固定的构建“生命周期”，称为 clean、default 和 site。

另请参阅： Maven 网站上的 [“构建生命周期简介” 。](http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)

这些标准构建生命周期都专注于并且仅关注于项目工件本身。这意味着构建生命周期及其所有可能的配置实际上只涉及最终工件及其元数据， 而不是打算使用它的（目标）环境。

默认生命周期的最后阶段**deploy**，涉及将项目工件部署到远程 Maven 存储库。已部署工件的预期用途仅在此阶段之后出现，并且通常超出 Maven 本身的 POV 范围，除非工件本身被另一个 Maven 项目用作依赖项。（这实际上是最常见的“预期”用例）。

对于默认和最常见的 Maven 工件类型**jar**，这是非常好的，但对于像 Jetspeed-2 Portal 这样的应用程序服务器集成框架，它不是。

与 Springframework 等更通用的低级（开发）框架相比，Jetspeed-2 带有一组非常具体的组件，通常仅在集成级别进行组装和配置。虽然 Jetspeed-2本身是使用 Maven-2 和 Springframework 在非常底层的细节上组装和配置的，但它应该只需要一些特定的配置（并为扩展提供空间）来适应和集成自定义项目及其环境。

这些自定义项目和环境特定的更改/覆盖和扩展应该独立于基本的 Jetspeed-2 门户配置进行配置，以支持自定义项目生命周期本身的干净和清晰的维护。

对于这些要求，标准提供的 Maven 构建生命周期和扩展点（目前）有点短。

### 2.1.2. **自定义 Maven 构建生命周期的方法**

有很多方法可以自定义 Maven 构建生命周期：

1. **在 Maven 项目 (pom.xml) 文件中使用（仅）配置**
2. 文件配置文件允许增加或替换默认生命周期行为，但保持 预定义的生命周期阶段处理。而且，由于默认生命周期已经配置了标准行为，因此尝试实现与此标准行为截然不同的东西（例如为特定应用程序服务器部署和配置完整的 Portal 应用程序）很快就会变得非常笨拙且难以设置和维护（如果可行的话）完全）。
3.
4. **使用“独立”插件另一种方法是编写和/或利用在生命周期**之外
5. 运行的所谓“独立”Maven 插件 。这些插件不影响或受默认生命周期的影响。但是...对于当前的 Maven 2.0 模型，它们也只能在项目 (pom.xml) 文件中具有单个配置。如果需要许多不同的任务（以及可能的不同环境），配置很快就会变得非常庞大和复杂和/或需要将其拆分为多个配置文件定义。但是，复杂的配置只会被最终用户的更复杂且容易出错的（手动）构建指令所取代。

此外，由于这些插件在任何生命周期之外运行，因此不能利用任何标准的 Maven 插件（也不能直接“调用”，这是 Maven 不支持的）。通常需要的标准功能，如复制/过滤资源文件，也必须由独立插件本身提供！

最后，虽然独立插件可以“分叉”默认生命周期（阶段），但这也意味着（可能）所有 标准提供的生命周期行为也会再次执行，导致与前一个选项相同的问题（参见：上文） .

7.
8. **添加额外的专用子项目**
9. 如果某个项目需要多个“工件”，这是“标准” Maven-2 解决方案：将项目拆分为其他子项目，每个子项目都提供自己的“专用”结果（注意：使用 Maven- 1 为此目的，在 maven.xml 中编写自定义果冻“目标”是一种简单且常见的做法）。

虽然这当然是一个很好的解决方案，并且允许利用完整的 Maven-2 功能集，但它也有一些注意事项。

首先，当需要许多不同的“任务”时，它会使项目结构变得相当混乱。而且，由于这些“任务”通常不会在正常的构建生命周期中自动运行，因此不应将它们配置为父项目的子模块，而是需要手动导航和调用开发人员。使用（再次）多个配置文件（见上文）将其中几个任务“合并”到一个通用项目（pom）文件中可以“自动化”这一点，但随后需要开发人员知道并指定每个需要的配置文件（组合） ） 执行。

此外，虽然它本身可能是“好的”实践，但它通常需要首先在本地或远程 Maven 存储库中构建和安装此类专用“任务”子项目所需的所有工件和资源。当这样的资源已经在另一个（子）项目的上下文中本地可用时，这可能会给项目配置增加更多的复杂性和冗余。

12.
13. **使用自定义项目 (pom.xml) 文件**
14. Maven-2 允许使用命令行选项 (-f <project file>) 执行非默认 (pom.xml) 项目文件。

该解决方案提升了之前解决方案的一些注意事项：无需将项目拆分为多个子项目，因为自定义的“面向任务”项目文件可以直接访问项目本地资源。

另一方面，此解决方案需要使用额外的命令行参数，因此开发人员需要付出更多的努力。

16.
17. **使用自定义生命周期扩展**
18. 最后，可以使用自定义 <packaging> 类型一起替换项目 (pom.xml) 文件的默认生命周期。

这种自定义生命周期定义必须通过自定义插件扩展提供，并在项目文件本身中专门配置。并且自定义生命周期扩展必须提供所有预期行为的完整定义。如果这包括“旧”标准行为（例如构建和安装战争），那么这种解决方案很快就会落入上面讨论的第一个解决方案，尽管它允许更多（但仍然是固定的）灵活性和配置选择。

此解决方案的其他注意事项是可能需要多个自定义生命周期（例如 pom、war、jar、ear 等不同的生命周期），并且（未来）默认 IDE 工具支持将非常不可能。

在上述方案中，方案2和方案5是最难维护和使用的。解决方案 3 或 4，可能与解决方案 1 结合使用，更符合 Maven-2 的预期用途，但确实有一个主要警告，即它们需要更复杂的手动（命令行）使用说明。

这里真正缺少的是自动化：针对特定自定义项目及其目标环境所需的不同任务和命令行参数的脚本/配置支持。

虽然编写自定义 shell 脚本，或者甚至使用[Apache Ant](http://ant.apache.org/)脚本来自动化不同的 Maven-2 命令是非常可行的，但它很容易导致每个项目都有自己的自定义（因此是不同的）做事方式。而且，由于它将依赖于另一个构建工具，环境不兼容问题（例如 bash 脚本通常不能在 Windows 上运行）很容易使维护变得更加复杂。

**jetspeed:mvn Maven 插件 - 使用 Maven 自动化 Maven 任务**

为了“解决”这些问题，Jetspeed-2 提供的解决方案是一个定制的 Maven 插件，jetspeed:mvn，它使用与 Apache Ant 目标非常相似的（父）项目文件中的配置，从 Maven内部 自动执行 Maven-2定义。

jetspeed:mvn 插件是一个独立的插件（见上面的讨论），但只需要一个非常简单的配置和一个额外的命令行参数来执行。

Jetspeed-2 项目本身用于构建、安装、配置数据库并最终部署完整 Jetspeed 演示门户的示例命令行用法和（简化）配置的一部分是：

$mvn jetspeed:mvn -Dtarget=demo

<插件>

<groupId>org.apache.portals.jetspeed-2</groupId>

<artifactId>jetspeed-mvn-maven-plugin</artifactId>

<version>${org.apache.portals.jetspeed.version}</version>

<配置>

<targets combine.children="append">

  <目标>

    <id>演示安装</id>

    <dir>@rootdir@/applications/jetspeed-demo</dir>

  </目标>

  <目标>

    <id>产品数据库</id>

    <name>db-init</name>

    <属性>

      <database.type>生产</database.type>

    </属性>

  </目标>

  <目标>

    <id>演示种子</id>

    <name>演示</name>

    <dir>@rootdir@/applications/jetspeed-demo</dir>

    <profiles>种子</profiles>

  </目标>

  <目标>

    <id>演示数据库</id>

    <depends>proddb,demo-seed</depends>

  </目标>

  <目标>

    <id>演示部署</id>

    <name>演示</name>

    <dir>@rootdir@/applications/jetspeed-demo</dir>

    <profiles>部署</profiles>

  </目标>

  <目标>

    <id>演示</id>

    <depends>demo-install,demo-db,demo-deploy</depends>

  </目标>

</目标>
</配置>

</插件>

上面的示例配置显示了几个目标“任务”，它们可以选择“依赖”其他将首先自动执行的目标（任务）。此外，还可以定义特定的属性、配置文件和目标，并将其传递给 Maven 执行环境。此外，还可以指定和使用另一个（可能是自定义）要执行的项目文件的位置，甚至是自定义的 maven 用户设置文件，从而可以完全控制目标 Maven 执行环境。

jetspeed:mvn 插件基于并改编自标准[Maven Invoker 插件](http://maven.apache.org/plugins/maven-invoker-plugin/)，该插件（仅）针对运行附加到集成测试生命周期阶段的集成测试项目。

jetspeed:mvn 插件扩展了标准 Invoker 插件，允许直接从命令行调用并提供通用且可配置的执行目标链。在某种程度上，这类似于 Apache Ant 构建脚本，但使用标准 Maven-2 项目构建生命周期处理来实际执行各个目标任务。

jetspeed:mvn 插件的完整描述和配置定义在[Mvn 插件](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html) 页面上提供，详细用法在**Building Jetspeed**菜单页面上提供。

### 2.1.3. **建造 Jetspeed**

#### 2.1.3.1. [**从源头**](https://portals.apache.org/jetspeed-2/buildguide/maven-2-build.html)

##### 2.1.3.1.1. **先决条件**

从源代码构建和部署 Jetspeed-2 具有以下先决条件：

· Java 开发工具包 1.7

· [Apache Maven](http://maven.apache.org/) 3.3.1+

· [Apache Tomcat](http://tomcat.apache.org/) 7.0+

· Settings pluginGroup的配置**org.apache.portals.jetspeed-2**，请参阅：先决 条件： 在**Overview**页面 上[配置 Maven Settings pluginGroups 。](#PREREQUISITE:_configuration_of_the_Maven_Settings_pluginGroups)

· 下载的[发布](http://portals.apache.org/jetspeed-2/download.html)源分发存档或使用 SVN 客户端工具直接从 ASF Subversion 源存储库中检出。

· 您可以从 [http://svn.apache.org/repos/asf/portals/jetspeed-2/portal/trunk/查看源代码](http://svn.apache.org/repos/asf/portals/jetspeed-2/portal/trunk/)

##### 2.1.3.1.2. **配置构建环境**

构建期间和 jetspeed 演示门户部署所需的所有设置都需要在项目根文件夹中的单个文件中定义：**jetspeed-mvn-settings.xml**.

注意：此文件未提供，但需要先手动创建。

然而，为了方便起见，**jetspeed-mvn-settings-sample.xml**提供了一个示例文件，可以简单地将其复制到**jetspeed-mvn-settings.xml**.

提供使用嵌入式 Derby 数据库的**jetspeed-mvn-settings-sample.xml**默认配置，如果适合您，可能唯一需要更改的是 Derby 数据库的位置和部署目标目录 ( **org.apache.jetspeed.server.home**)：

<属性>

...

<!-- 你的 Tomcat 安装路径 -->

<org.apache.jetspeed.server.home>/home/demo/tomcat-7</org.apache.jetspeed.server.home>

<org.apache.jetspeed.catalina.version.major>7</org.apache.jetspeed.catalina.version.major>

                  

<!-- 生产jdbc驱动神器属性-->

<org.apache.jetspeed.production.jdbc.driver.groupId>org.apache.derby</org.apache.jetspeed.production.jdbc.driver.groupId>

<org.apache.jetspeed.production.jdbc.driver.artifactId>derby</org.apache.jetspeed.production.jdbc.driver.artifactId>

<org.apache.jetspeed.production.jdbc.driver.version>10.3.2.1</org.apache.jetspeed.production.jdbc.driver.version>



<!-- 生产数据库名称、JDBC url、JDBC驱动名称和连接信息-->

<org.apache.jetspeed.production.database.default.name>derby</org.apache.jetspeed.production.database.default.name>

<org.apache.jetspeed.production.database.url>jdbc:derby:/tmp/derby/productiondb;create=true</org.apache.jetspeed.production.database.url>

<org.apache.jetspeed.production.database.driver>org.apache.derby.jdbc.EmbeddedDriver</org.apache.jetspeed.production.database.driver>

<org.apache.jetspeed.production.database.user></org.apache.jetspeed.production.database.user>

<org.apache.jetspeed.production.database.password></org.apache.jetspeed.production.database.password>



...



<!-- 如果要运行单元测试，还可以在下面配置测试数据库属性。-->



<!-- 测试jdbc驱动工件属性-->

<org.apache.jetspeed.test.jdbc.driver.groupId>org.apache.derby</org.apache.jetspeed.test.jdbc.driver.groupId>

<org.apache.jetspeed.test.jdbc.driver.artifactId>derby</org.apache.jetspeed.test.jdbc.driver.artifactId>

<org.apache.jetspeed.test.jdbc.driver.version>10.3.2.1</org.apache.jetspeed.test.jdbc.driver.version>



<!-- 测试数据库名、JDBC url、JDBC驱动名和连接信息-->

<org.apache.jetspeed.test.database.default.name>derby</org.apache.jetspeed.test.database.default.name>

<org.apache.jetspeed.test.database.url>jdbc:derby:/tmp/derby/testdb;create=true</org.apache.jetspeed.test.database.url>

<org.apache.jetspeed.test.database.driver>org.apache.derby.jdbc.EmbeddedDriver</org.apache.jetspeed.test.database.driver>

<org.apache.jetspeed.test.database.user></org.apache.jetspeed.test.database.user>

<org.apache.jetspeed.test.database.password></org.apache.jetspeed.test.database.password>

...
</属性>

注意：根据您的数据库平台，该**org.apache.jetspeed.production.database.default.name**属性的值可以是以下之一，具体取决于您的数据库平台：

· 数据库2

· db2v8

· 德比

· mssql

· mysql

· mysql5

· 甲骨文9

· 甲骨文10

· PostgreSQL

· 数据库

有关支持的数据库的详细信息，请参阅[Apache DB 项目 - DdlUtils 主页](http://db.apache.org/ddlutils/)。

以下**jetspeed-mvn-settings.xml**提供了使用 PostgreSQL 数据库的示例配置：

<属性>

...

<!-- 你的 Tomcat 安装路径 -->

<org.apache.jetspeed.server.home>/home/demo/tomcat-7</org.apache.jetspeed.server.home>

<org.apache.jetspeed.catalina.version.major>7</org.apache.jetspeed.catalina.version.major>

<!-- 生产jdbc驱动神器属性-->

<org.apache.jetspeed.production.jdbc.driver.groupId>postgresql</org.apache.jetspeed.production.jdbc.driver.groupId>

<org.apache.jetspeed.production.jdbc.driver.artifactId>postgresql</org.apache.jetspeed.production.jdbc.driver.artifactId>

<org.apache.jetspeed.production.jdbc.driver.version>8.3-603.jdbc3</org.apache.jetspeed.production.jdbc.driver.version>



<!-- 生产数据库名称、JDBC url、JDBC驱动名称和连接信息-->

<org.apache.jetspeed.production.database.default.name>postgresql</org.apache.jetspeed.production.database.default.name>

<org.apache.jetspeed.production.database.url>jdbc:postgresql://localhost/j2</org.apache.jetspeed.production.database.url>

<org.apache.jetspeed.production.database.driver>org.postgresql.Driver</org.apache.jetspeed.production.database.driver>

<org.apache.jetspeed.production.database.user>j2</org.apache.jetspeed.production.database.user>

<org.apache.jetspeed.production.database.password>j2</org.apache.jetspeed.production.database.password>



...



<!-- 如果要运行单元测试，还可以在下面配置测试数据库属性。-->



<!-- 测试jdbc驱动工件属性-->

<org.apache.jetspeed.test.jdbc.driver.groupId>postgresql</org.apache.jetspeed.test.jdbc.driver.groupId>

<org.apache.jetspeed.test.jdbc.driver.artifactId>postgresql</org.apache.jetspeed.test.jdbc.driver.artifactId>

<org.apache.jetspeed.test.jdbc.driver.version>8.3-603.jdbc3</org.apache.jetspeed.test.jdbc.driver.version>



<!-- 测试数据库名、JDBC url、JDBC驱动名和连接信息-->

<org.apache.jetspeed.test.database.default.name>postgresql</org.apache.jetspeed.test.database.default.name>

<org.apache.jetspeed.test.database.url>jdbc:postgresql://localhost/j2test</org.apache.jetspeed.test.database.url>

<org.apache.jetspeed.test.database.driver>org.postgresql.Driver</org.apache.jetspeed.test.database.driver>

<org.apache.jetspeed.test.database.user>j2test</org.apache.jetspeed.test.database.user>

<org.apache.jetspeed.test.database.password>j2test</org.apache.jetspeed.test.database.password>

...
</属性>

另外，以下提供了使用 MySQL 数据库的示例配置：

<属性>

...

<!-- 你的 Tomcat 安装路径 -->

<org.apache.jetspeed.server.home>/home/demo/tomcat-7</org.apache.jetspeed.server.home>

<org.apache.jetspeed.catalina.version.major>7</org.apache.jetspeed.catalina.version.major>



<!-- 生产jdbc驱动神器属性-->

<org.apache.jetspeed.production.jdbc.driver.groupId>mysql</org.apache.jetspeed.production.jdbc.driver.groupId>

<org.apache.jetspeed.production.jdbc.driver.artifactId>mysql-connector-java</org.apache.jetspeed.production.jdbc.driver.artifactId>

<org.apache.jetspeed.production.jdbc.driver.version>5.1.6</org.apache.jetspeed.production.jdbc.driver.version>



<!-- 生产数据库名称、JDBC url、JDBC驱动名称和连接信息-->

<org.apache.jetspeed.production.database.default.name>mysql5</org.apache.jetspeed.production.database.default.name>

<org.apache.jetspeed.production.database.url>jdbc:mysql://localhost:3306/j2</org.apache.jetspeed.production.database.url>

<org.apache.jetspeed.production.database.driver>com.mysql.jdbc.Driver</org.apache.jetspeed.production.database.driver>

<org.apache.jetspeed.production.database.user>j2</org.apache.jetspeed.production.database.user>

<org.apache.jetspeed.production.database.password>j2</org.apache.jetspeed.production.database.password>



...



<!-- 如果要运行单元测试，还可以在下面配置测试数据库属性。-->



<!-- 测试jdbc驱动工件属性-->

<org.apache.jetspeed.test.jdbc.driver.groupId>mysql</org.apache.jetspeed.test.jdbc.driver.groupId>

<org.apache.jetspeed.test.jdbc.driver.artifactId>mysql-connector-java</org.apache.jetspeed.test.jdbc.driver.artifactId>

<org.apache.jetspeed.test.jdbc.driver.version>5.1.6</org.apache.jetspeed.test.jdbc.driver.version>



<!-- 测试数据库名、JDBC url、JDBC驱动名和连接信息-->

<org.apache.jetspeed.test.database.default.name>mysql5</org.apache.jetspeed.test.database.default.name>

<org.apache.jetspeed.test.database.url>jdbc:mysql://localhost:3306/j2test</org.apache.jetspeed.test.database.url>

<org.apache.jetspeed.test.database.driver>com.mysql.jdbc.Driver</org.apache.jetspeed.test.database.driver>

<org.apache.jetspeed.test.database.user>j2test</org.apache.jetspeed.test.database.user>

<org.apache.jetspeed.test.database.password>j2test</org.apache.jetspeed.test.database.password>

...
</属性>

注意：要使用** MySQL **数据库正确运行单元测试，您应该启用 InnoDB 存储引擎并使用 InnoDB 表。InnoDB 是 MySQL 数据库的事务安全（符合 ACID）存储引擎。有关详细信息，请参阅 MySQL 的文档。

##### 2.1.3.1.3. **配置 Tomcat**

需要对默认提供的 Tomcat 配置进行一些更改和添加，以支持正确的 Portlet API 会话管理要求和 Jetspeed Portlet 应用程序管理集成：

· In **<TOMCAT\_HOME>/conf/server.xml**：

· 通过添加以下属性和值来修改连接器元素（默认在端口 8080 上）：

空会话路径 =“真”

·

· 在**<TOMCAT\_HOME>/conf/context.xml**：

· 取消注释以下内容以禁用跨 Tomcat 重新启动的会话持久性：

<经理路径名=""/>

·

· 可选： 在**<TOMCAT\_HOME>/conf/tomcat-users.xml**:

· 选择或添加一个特定的 Tomcat 用户，该用户至少具有**manager-script**Jetspeed 用于与 Tomcat 管理器应用程序通信的角色：

<user username="j2deployer" 密码="<<em>strong</em> 密码<" 角色=“经理脚本”/>

· 然后，在门户网站在运行时读取的文件中定义此用户名及其密码**jetspeed.properties**，但可以在**override.properties**.

· 有关详细信息，请参阅 Deployers Guide 中的[Tomcat Manager 和 Jetspeed](https://portals.apache.org/jetspeed-2/deployguide/guide-tomcat.html)部分。

##### 2.1.3.1.4. **构建和安装 Jetspeed 门户**

###### 2.1.3.1.4.1. **可选：Bootstrap 首先构建 Jetspeed Maven 插件**

从已发布的源分发存档或 SVN 签出相应的发布标签构建 Jetspeed 2.3 时，可以跳过以下步骤。

但是，在构建尚未（尚未）发布的特定 Jetspeed 2.3.x SNAPSHOT 或分支 SVN checkout 时，您必须首先运行以下命令，但**仅**是第一次（对于 checkout 版本）：

$mvn 安装 -P 初始化

上述命令将确保自定义 Jetspeed Maven 插件以及此构建版本的门户资源已预先构建并安装在您的本地 Maven 存储库中，因为它们可能无法从远程 Maven 存储库获得。

如果没有上述引导构建，初始**/**首次**\$mvn clean**执行可能会导致构建失败：“找不到所需的插件”错误。

###### 2.1.3.1.4.2. **标准 Maven 构建和安装**

使用标准 Maven 安装目标将所有 Jetspeed-2 组件完整构建并安装到本地 Maven 存储库中：

$mvn 安装

###### 2.1.3.1.4.3. **部署 jetspeed 演示门户**

首先确保在本地设置 Tomcat 6 (6.0.33+) 并首先应用上述 Tomcat 配置更改。

还要确保在 Jetspeed 项目根目录的 本地文件中配置适当的 Tomcat 主要版本 ( **org.apache.jetspeed.catalina.version.major**) 和安装路径 ( )。**org.apache.jetspeed.server.homejetspeed-mvn-settings.xml**

使用上述方法首次构建和安装 Jetspeed 项目后**\$mvn install**，使用以下命令将 Jetspeed 演示门户部署到 Tomcat：

$mvn jetspeed:mvn -Dtarget=demo

此后启动 Tomcat（在单独的控制台中）：

请注意，在以下示例中，CATALINA\_OPTS 的设置是可选的。（有关详细信息，请参阅[有关 JVM 的永久生成大小的注释](#Note_on_Permanent_Generation_Size_of_Your_JVM)。）

$ cd $TOMCAT_HOME/bin

$ 出口 CATALINA_OPTS="-Xmx256m -XX:MaxPermSize=128m"

$ ./catalina.sh 运行

等待几秒钟直到 Tomcat 服务器完成启动后，可以通过以下方式访问 Jetspeed 演示门户：

[http://localhost:8080/jetspeed](http://localhost:8080/jetspeed)

对于登录，请使用以下用户名/密码组合之一：admin/admin、user/user、jetspeed/jetspeed

###### 2.1.3.1.4.4. **关于 JVM 的永久生成大小的注意事项**

注意：当有很多 Servlet、JSP 或使用脚本 portlet 时，您可能需要增加 JVM 的永久生成大小，以避免**OutOfMemoryError**错误。默认情况下，它是 64MB。增加它**-XX:MaxPermSize=128m**可能是一个好的开始。有关详细信息，请参阅[http://wiki.apache.org/tomcat/FAQ/Memory](http://wiki.apache.org/tomcat/FAQ/Memory)。

##### 2.1.3.1.5. **部署最小的 Jetspeed 门户**

如果您不需要演示 portlet 应用程序，您也可以使用以下命令仅使用 j2-admin portlet 应用程序部署 Jetspeed：

$mvn jetspeed:mvn -Dtarget=min

##### 2.1.3.1.6. **构建和安装选项**

###### 2.1.3.1.6.1. **概述**

使用 jetspeed:mvn 插件，为 Jetspeed Portal 项目本身提供了几个定义的自定义构建和安装任务（目标）。

**-Dlist**可以使用特殊的命令行参数 查询可用目标的完整列表：

$mvn -o jetspeed:mvn -Dlist

下面详细描述了主要的 jetspeed:mvn 目标。请参阅[Mvn 插件](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html)配置文档和根项目**pom.xml**构建文件以获取更多参考。

###### 2.1.3.1.6.2. **主要喷气机速度：MVN目标**

可以在以下四种主要模式下构建和部署门户：

· ui：完整的 ui 管道演示构建

· min-ui：最小的 ui 管道演示构建

· 演示：完整的门户管道演示构建

· min：最小的门户管道演示构建

此外，每种模式都有两个页面管理器变体：

· 基于 XML 文件系统的 PSML

· 数据库 PSML

此处概述了可用于构建和部署门户的全部或部分的主要构建目标：


| 测试                                                                               | 执行**test**目标将简单地执行当前（子模块）项目文件夹中的标准Maven测试目标，*并* 启用**test**配置文件。当然，仅仅执行也可以达到相同的效果，**\$mvn test -P test**但这个目标定义的主要原因是用作其他目标的依赖目标（见下文）。                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 测试数据库，产品数据库                                                             | 执行这些目标之一将（重新）创建测试或生产数据库（模式），使用**jetspeed-mvn-settings.xml**文件中的数据库配置属性。*注意：这个目标可以在项目中的任何（子）模块文件夹中执行。*                                                                                                                                                                                                                                                                                                                    |
| **ui-seed**、min-ui-seed、demo-seed、min-seed 和 ui-db、min-ui-db、demo-db、min-db | 除了使用目标（重新）创建（生产）数据库**proddb**外，Jetspeed数据库还需要首先播种一些初始数据才能运行 Jetspeed 门户。目标将**ui-seed, min-ui-seed, demo-seed, min-seed**使用特定**j2-seed.xml**文件来处理。这些种子文件是从先前构建和安装或下载**jetspeed-portal-resouces:jar**的工件中动态检索的，其中配置的种子文件是相对于该资源工件中特定文件夹的引用。由于**proddb**目标和**\*-seed**目标通常一起执行，因此**ui-db, min-ui-db, demo-db, min-db**还定义了目标以允许将它们作为单个目标执行。 |
| 演示安装                                                                           | 该目标将简单地针对模块pom.xml调用默认的 Maven 目标（即*install*） 。**applications/jetspeed-demo**                                                                                                                                                                                                                                                                                                                                                                                             |
| **ui, min-ui, demo, min**                                                          | 这些目标将执行Jetspeed Portal实际部署到 Tomcat 安装以及所有数据库配置和种子设定。使用基于 XML 文件系统的 PSML 实现，默认情况下（重新）部署其页面。*注意：直接执行这些目标假定所有必需的**Jetspeed**工件都已构建和安装。*                                                                                                                                                                                                                                                                       |
| **ui-nodb**，min-ui-nodb，demo-nodb，min-nodb                                      | 这些目标仅执行Jetspeed门户的部署。数据库保持不变，（基于 XML 文件系统的 PSML 页面被重新部署）。                                                                                                                                                                                                                                                                                                                                                                                                |
| **ui-dbpsml**、min-ui-dbpsml、demo-dbpsml、min-dbpsml                              | 这些目标是**ui, min-ui, demo, min**数据库PSML配置目标的变体（其页面被播种到数据库中）；                                                                                                                                                                                                                                                                                                                                                                                                        |
| **ui-dbpsml-nodb**，min-ui-dbpsml-nodb，demo-dbpsml-nodb，min-dbpsml-nodb          | 这些目标是**ui-nodb, min-ui-nodb, demo-nodb, min-nodb**数据库PSML配置目标的变体（其页面未播种到数据库中）；                                                                                                                                                                                                                                                                                                                                                                                    |

##### 2.1.3.1.7. **测试构建 Jetspeed 门户**

###### 2.1.3.1.7.1. **在构建期间运行测试用例**

默认情况下，Jetspeed-2 禁用运行测试用例，因为它非常耗时，并且每次都需要设置和初始化专用测试数据库！

但是，如果您是 Jetspeed 提交者或无论如何都想运行测试用例，则可以使用**testdb** jetspeed:mvn 目标来设置和初始化测试数据库：

$mvn jetspeed:mvn -Dtarget=testdb

或者您可以运行以下命令，在运行测试构建之前先 自动执行**testdb**目标：

$mvn jetspeed:mvn -Dtarget=test-install

注意：运行测试用例需要（并且仅用于此目的）正确配置** jetspeed-mvn-settings.xml **中的 org.apache.jetspeed.test.database.* 属性

附加说明：可能您需要为** maven **配置一些内存设置才能正确运行所有测试，因为某些测试用例需要比默认内存大小更多的内存。您可以通过设置环境变量“MAVEN_OPTS”来配置 maven 的内存设置。例如：

**\$export MAVEN\_OPTS="-Xmx128m -XX:MaxPermSize=128m"**

##### 2.1.3.1.8. **Maven 配置文件**

构建时可以提供以下配置文件。


| **mvn -P**全部   | 指定构建所有模块（API、插件、门户资源、公共资源、组件和应用程序）。                                |
| ---------------- | -------------------------------------------------------------------------------------------------- |
| **mvn -P**初始化 | 指定首先初始化的一些模块（API、插件和门户资源）                                                    |
| **mvn -P**测试   | 指定使用属性设置**-DskipTests=false构建所有模块（API、插件、门户资源、公共资源、组件和应用程序）** |

###### 2.1.3.1.8.1. **补充笔记**

· **mvn -P test**和**mvn -DskipTests=false**是等价的。

· **如果使用 Ant 通配符， mvn -P test -Dtest=MyTest**将执行单个测试或匹配测试。

· 由于 Surefire Maven2 测试运行器插件中的分叉错误，测试输出（例如 System.out.println()）不会回显到构建 shell。如果您希望查看组件测试的控制台输出，请暂时注释掉 components/pom.xml 和组件 pom.xml 中的 <forkMode> 元素并运行单个测试。注意：分叉需要运行多个测试。

· 可以使用此处记录的命令指定 -o 脱机选项，以强制 Maven2 仅使用本地存储库。如果主要 Maven2 存储库已关闭并且构建坚持验证丢失或麻烦的 POM，这可能是无价的。

#### 2.1.3.2. [**Jetspeed 原型**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-archetype.html)

Jetspeed-2.3 提供了一个原型 Maven 插件，允许门户开发人员非常轻松地创建自定义门户项目。在开始新的基于 Jetspeed 的门户项目时，我们强烈建议您通过 jetspeed-archetype Maven 插件创建自定义门户项目，并且不要直接编辑 Jetspeed-2 源和资源。

本文档将指导您如何运行命令以及创建名为**hello**的示例门户的步骤。

您需要以下先决条件：

· Java 开发工具包 1.5

· [Apache Maven](http://maven.apache.org/) 3.3.1 或更高版本

· [Apache Tomcat](http://tomcat.apache.org/) 7.0 或更高版本

##### 2.1.3.2.1. **可选：构建和安装 Jetspeed-2 Maven 插件**

由于 Jetspeed Maven 插件和 Archetype 插件将由 Maven-2 自动下载，因此您无需从 Jetspeed-2 源代码构建和安装它们。

注意：在正常情况下，为简单起见，您可以跳过本节。

但是，如果您出于某些原因想要这样做，您可以在 Jetspeed-2 源代码的根目录中使用以下命令从 Jetspeed-2 源代码构建和安装 Jetspeed-2 Maven 插件和 Archetype 插件：

$mvn 安装 -P 初始化

这将确保构建和安装所需的 Jetspeed-2 Maven 插件以及 jetspeed-portal-resources 工件。

##### 2.1.3.2.2. **使用 jetspeed-archetype Maven 插件**

要使用 jetspeed-archetype Maven 插件，您可以运行如下命令：

**mvn org.apache.maven.plugins:maven-archetype-plugin:2.0-alpha-4:generate \\**

**    -DarchetypeGroupId=org.apache.portals.jetspeed-2 \\**

**    -DarchetypeArtifactId=jetspeed-archetype \\**

**    -DarchetypeVersion=2.3.0 \\**

**    -DartifactId=hello \\**

**    -Dpackage=org.example \\**

**    -DgroupId=org.example -Dversion=1.0.0**

在上述命令中，变量“artifactId”、“package”和“groupId”是项目特定的变量。所以你应该为你的项目提供变量。

顺便说一句，上述命令中的其他变量来自 Maven Archetype Plugin Specification。详情请参考[Maven Archetype Plugin](http://maven.apache.org/plugins/maven-archetype-plugin/)主页。

##### 2.1.3.2.3. **生成 Hello Portal 应用示例**

要构建名为“hello”的自定义门户项目，您可能需要移动到项目文件夹所在的文件夹。例如，

**\$ cd \~/projects**

**\$ mvn org.apache.maven.plugins:maven-archetype-plugin:2.0-alpha-4:generate \\**

**-DarchetypeGroupId=org.apache.portals.jetspeed-2 \\**

**-DarchetypeArtifactId=jetspeed-archetype \\**

**-DarchetypeVersion=2.3.0 \\**

**-DartifactId=hello \\**

**-Dpackage=org.example \\**

**-DgroupId=org.example -Dversion=1.0.0**

---

注意：运行上述命令后，您将遇到确认提示。通过按回车键，它将继续生成自定义门户项目。

使用上述命令，**jetspeed-archetype**生成一个完整的 Maven-2 项目目录结构，用于开发自定义门户和 portlet 应用程序。以下是由 jetspeed-archetype 创建的目录的概述（目录与自定义门户根目录相关）：


| **目录**                                        | **描述**                      |
| ----------------------------------------------- | ----------------------------- |
| 你好                                            | 项目根目录                    |
| 你好/你好门户                                   | 自定义门户Web应用程序根目录   |
| 你好/你好门户/ src                              | 自定义门户的源目录            |
| 你好/hello-portal/src/main/webapp/WEB-INF/pages | 自定义PSML页面源的源目录      |
| 你好/hello-portal/src/sql/min                   | 播种初始数据库的源目录        |
| 你好/你好-pa                                    | 自定义portlet应用程序根目录   |
| 你好/你好-pa/src                                | 自定义portlet应用程序的源目录 |

##### 2.1.3.2.4. **构建 Hello Portal 应用示例**

要配置生成的门户项目，您需要编辑**jetspeed-mvn-settings.xml**项目根目录中的文件并更改以下内容：


| **财产**                                              | **描述**                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| org.apache.jetspeed.server.home                       | 作为自定义门户部署目标的Tomcat服务器目录。                                                                                                                                                                                                                                                                                                   |
| org.apache.jetspeed.catalina.version.major            | Tomcat的主要版本号。支持的值为 6 和 7。默认值为 6。                                                                                                                                                                                                                                                                                          |
| org.apache.jetspeed.production.jdbc.driver.groupId    | JDBC驱动程序的 groupdId。例如，对于 Apache Derby JDBC 驱动程序，这可以是“org.apache.derby”。                                                                                                                                                                                                                                               |
| org.apache.jetspeed.production.jdbc.driver.artifactId | JDBC驱动程序的 artifactId。例如，这可以是 Apache Derby JDBC 驱动程序的“derby”。                                                                                                                                                                                                                                                            |
| org.apache.jetspeed.production.jdbc.driver.version    | JDBC驱动程序的版本。                                                                                                                                                                                                                                                                                                                         |
| org.apache.jetspeed.production.database.default.name  | DDLUtils用于为您的特定数据库生成数据库模式 SQL 脚本的数据库名称。根据您的数据库平台，这必须是以下之一：“db2”、“db2v8”、“derby”、“mssql”、“mysql”、“mysql5”、“oracle9”、“oracle10”、“postgresql”、 “sapdb”等等。（有关数据库支持的详细信息，您可以参考[Apache DB项目 - DdlUtils 主页](http://db.apache.org/ddlutils/)。） |
| org.apache.jetspeed.production.database.url           | 用于数据库访问的JDBC URL。                                                                                                                                                                                                                                                                                                                   |
| org.apache.jetspeed.production.database.driver        | 用于数据库访问的JDBC驱动程序类名称。                                                                                                                                                                                                                                                                                                         |
| org.apache.jetspeed.production.database.user          | 用于数据库访问的数据库用户名。                                                                                                                                                                                                                                                                                                               |
| org.apache.jetspeed.production.database.password      | 用于访问数据库的数据库用户密码。                                                                                                                                                                                                                                                                                                             |

最初，**jetspeed-archetype**生成一个**jetspeed-mvn-settings.xml**以使用 Apache Derby，如下例所示：

**<settings xmlns="http://maven.apache.org/POM/4.0.0">**

**  <profiles>**

**    <profile>**

---

**      ...**

---

**      <properties>**

**        <org.apache.jetspeed.server.home>/change/this/apache-tomcat-6.0.33/</org.apache.jetspeed.server.home>**

**        <org.apache.jetspeed.catalina.version.major>6</org.apache.jetspeed.catalina.version.major>**

**        <org.apache.jetspeed.production.jdbc.driver.groupId>org.apache.derby</org.apache.jetspeed.production.jdbc.driver.groupId>**

**        <org.apache.jetspeed.production.jdbc.driver.artifactId>derby</org.apache.jetspeed.production.jdbc.driver.artifactId>**

**        <org.apache.jetspeed.production.jdbc.driver.version>10.3.2.1</org.apache.jetspeed.production.jdbc.driver.version>**

**        <org.apache.jetspeed.production.database.default.name>derby</org.apache.jetspeed.production.database.default.name>**

**        <org.apache.jetspeed.production.database.url>jdbc:derby:/tmp/jetspeed/derby/productiondb;create=true</org.apache.jetspeed.production.database.url>**

**        <org.apache.jetspeed.production.database.driver>org.apache.derby.jdbc.EmbeddedDriver</org.apache.jetspeed.production.database.driver>**

**        <org.apache.jetspeed.production.database.user></org.apache.jetspeed.production.database.user>**

**        <org.apache.jetspeed.production.database.password></org.apache.jetspeed.production.database.password>**

**      </properties>**

**    </profile>**

**  </profiles>**

**</settings>**

---

因此，如果您想将自定义门户部署到其他 Tomcat 位置并使用其他数据库，您应该更改“org.apache.jetspeed.server.home”属性和其他与数据库相关的属性。例如，以下显示了 MySQL 数据库的一种用法：

**<settings xmlns="http://maven.apache.org/POM/4.0.0">**

**  <profiles>**

**    <profile>**

---

**      ...**

---

**      <properties>**

**        <org.apache.jetspeed.server.home>C:/apache-tomcat-6.0.33/</org.apache.jetspeed.server.home>**

**        <org.apache.jetspeed.catalina.version.major>6</org.apache.jetspeed.catalina.version.major>**

**        <org.apache.jetspeed.production.jdbc.driver.groupId>mysql</org.apache.jetspeed.production.jdbc.driver.groupId>**

**        <org.apache.jetspeed.production.jdbc.driver.artifactId>mysql-connector-java</org.apache.jetspeed.production.jdbc.driver.artifactId>**

**        <org.apache.jetspeed.production.jdbc.driver.version>5.1.6</org.apache.jetspeed.production.jdbc.driver.version>**

**        <org.apache.jetspeed.production.database.default.name>mysql5</org.apache.jetspeed.production.database.default.name>**

**        <org.apache.jetspeed.production.database.url>jdbc:mysql://127.0.0.1/jetspeed?useServerPrepStmts=false&jdbcCompliantTruncation=false</org.apache.jetspeed.production.database.url>**

**        <org.apache.jetspeed.production.database.driver>com.mysql.jdbc.Driver</org.apache.jetspeed.production.database.driver>**

**        <org.apache.jetspeed.production.database.user>username</org.apache.jetspeed.production.database.user>**

**        <org.apache.jetspeed.production.database.password>password</org.apache.jetspeed.production.database.password>**

**      </properties>**

**    </profile>**

**  </profiles>**

**</settings>**

---

您可以使用以下命令构建自定义门户并将其部署到 Tomcat 安装：

$mvn org.apache.portals.jetspeed-2:jetspeed-mvn-maven-plugin:mvn -Dtarget=all

您可以通过将 Jetspeed Maven 插件的 groupId 添加到默认搜索的 groupId 列表中来缩短上述命令。为此，您需要将以下内容添加到您的 ${user.home}/.m2/settings.xml 文件中：

<settings xmlns="http://maven.apache.org/POM/4.0.0">

<插件组>

<!-- 添加以下行以缩短调用 Jetspeed Maven 插件的命令。-->

<pluginGroup>org.apache.portals.jetspeed-2</pluginGroup>

</pluginGroups>

</设置>

现在您可以使用更短的命令，如下所示：

$mvn jetspeed:mvn -Dtarget=all

启动您的 Tomcat：

请注意，CATALINA\_OPTS 的设置在以下示例中是可选的。（有关详细信息，请参阅[有关** JVM **的永久生成大小的注释](#Note_on_Permanent_Generation_Size_of_Your_JVM)。）

$ cd $TOMCAT_HOME/bin

$ 出口 CATALINA_OPTS="-Xmx256m -XX:MaxPermSize=128m"

$ ./catalina.sh 运行

使用您的自定义门户： [http://localhost:8080/hello](http://localhost:8080/hello)

##### 2.1.3.2.5. **关于 JVM 的永久生成大小的注意事项**

注意：当有很多 Servlet、JSP 或使用脚本 portlet 时，您可能需要增加 JVM 的永久生成大小，以避免**OutOfMemoryError**错误。默认情况下，它是 64MB。增加它**-XX:MaxPermSize=128m**可能是一个好的开始。有关详细信息，请参阅[http://wiki.apache.org/tomcat/FAQ/Memory](http://wiki.apache.org/tomcat/FAQ/Memory)。

##### 2.1.3.2.6. **高级构建选项**

通过命令 \`\$mvn jetspeed:mvn -Dtarget=all'，**jetspeed-archtype**将构建并安装您的自定义门户项目，初始化您的数据库，最后将您的门户和 portlet 应用程序部署到您的 Tomcat。但是，在您不断的开发过程中，通过上述命令完成所有任务可能会被认为是低效的。

因此，**jetspeed-archetype**提供了更高级的构建选项来满足各种需求。您可以通过在下表中设置所需的适当目标来构建：


| **目标**        | **示例命令**                                       | **描述**                                                              |
| --------------- | -------------------------------------------------- | --------------------------------------------------------------------- |
| 安装-pa         | **mvn jetspeed:mvn -Dtarget=install-pa**           | 清理并构建portlet应用程序子项目。                                     |
| 安装门户        | **mvn jetspeed:mvn -Dtarget=install-portal**       | 清理并构建门户应用程序子项目                                          |
| 安装            | **mvn jetspeed:mvn -Dtarget=install**              | 执行“install-pa”和“install-portal”。                              |
| D b             | **mvn jetspeed:mvn -Dtarget=db**                   | 初始化数据库并为您的自定义门户播种初始数据。                          |
| 门户种子        | **mvn jetspeed:mvn -Dtarget=portal-seed**          | 只需为您的自定义门户播种初始数据，无需初始化数据库。                  |
| 部署-pa         | **mvn jetspeed:mvn -Dtarget=deploy-pa**            | 部署您的自定义portlet应用程序。                                       |
| 部署门户        | **mvn jetspeed:mvn -Dtarget=deploy-portal**        | 部署您的自定义门户。                                                  |
| 门户种子dbpsml  | **mvn jetspeed:mvn -Dtarget=portal-seed-dbpsml**   | 为您的自定义门户应用程序播种基于数据库的页面数据。                    |
| 部署门户-dbpsml | **mvn jetspeed:mvn -Dtarget=deploy-portal-dbpsml** | 使用播种基于数据库的页面数据部署您的自定义门户。                      |
| 全部            | **mvn jetspeed:mvn -Dtarget=all**                  | 安装和部署您的自定义门户和自定义portlet应用程序，初始化和植入数据库。 |

### 2.1.4. **插件**

#### 2.1.4.1. [**插件概述**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-maven-plugins.html)

Jetspeed-2 提供的[Maven 2.0](http://maven.apache.org/)插件用于三个不同的目的：

· 添加对标准工件（主要是：战争）构建的支持：

o jetspeed-unpack : [unpack](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-unpack-plugin.html)插件

o jetspeed-deploy : [deploy](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-deploy-plugin.html)插件

· 执行在标准工件构建生命周期之外执行的目标环境集成任务：

o [jetspeed-db:](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html) init插件

o jetspeed-deploy : [deploy](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-deploy-plugin.html)插件

· 自动化和协调要在标准工件构建生命周期之外执行的集成任务：

o [jetspeed:](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html) mvn插件

· Jetspeed 门户项目（内部）构建支持从 ddl 模式定义生成数据库 ddl 脚本：

o [jetspeed-db:](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-ddl-plugin.html) ddl插件

此外，Jetspeed-2 提供了一个项目原型，用于与 [Maven 2 Archetype 插件](http://maven.apache.org/plugins/maven-archetype-plugin/)一起使用，即[jetspeed-archetype](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-archetype.html)。

jetspeed-archetype 是 Maven Archetype 插件的资源，用于生成具有基本配置的新自定义[Jetspeed Portal 项目布局](https://portals.apache.org/jetspeed-2/buildguide/project-layout.html) ，以有效利用 Jetspeed-2 Maven 插件。

**推荐阅读**

使用 jetspeed:mvn Maven 插件自动化 Maven 2 并在标准工件构建生命周期之外协调执行集成任务的基本原理如下所述：

   [需要自定义** Maven 生命周期**](https://portals.apache.org/jetspeed-2/buildguide/the-need-for-a-custom-lifecycle.html)

#### 2.1.4.2. [**Mvn 插件**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html)

jetspeed:mvn Maven 插件是一个通用插件，用于使用 Maven 构建环境本身自动化和协调特定的集成任务。此插件支持使用预定义的一组目标、配置文件、Maven 设置和运行时属性“运行”一个或多个自定义 Maven 项目构建定义。

除了标准 Maven 项目定义和构建生命周期之外 ，运行自定义 Maven 项目构建定义的基本原理在自[定义** Maven **生命周期的需要中进行了](https://portals.apache.org/jetspeed-2/buildguide/the-need-for-a-custom-lifecycle.html)描述。

jetspeed:mvn 插件基于并改编自标准[Maven Invoker 插件](http://maven.apache.org/plugins/maven-invoker-plugin/)，该插件（仅）针对运行附加到集成测试生命周期阶段的集成测试项目。

jetspeed:mvn 扩展了 Invoker 插件，允许直接从命令行调用，并提供更通用和可配置的执行目标链，类似于[Apache Ant](http://ant.apache.org/)构建脚本，但完全使用并委托给标准 Maven-2 项目为各个目标任务的实际执行构建生命周期处理。

除了允许从命令行执行和增强的配置选项之外，jetspeed:mvn 与标准 Maven Invoker 插件相比并没有真正提供新的行为，并且使用相同的 Maven API 和组件（共享的 maven-invoker 组件）。

这个插件不以任何方式依赖于 Jetspeed-2 本身，因此同样可用于除了正常的 Maven 构建生命周期之外需要执行任务的其他类型的项目。此外，该插件还可用于使用 Apache Ant 之类的链式目标定义配置“仅”自动化跨多个项目的标准 Maven 构建任务。

##### 2.1.4.2.1. **快速概览**

jetspeed:mvn 插件在调用时将执行其插件配置中定义的单个目标任务。但是，因为一个目标本身可以有一个“依赖”配置，这实际上可能导致一个目标链被执行到最初指定的目标本身。

这是可以为 jetspeed:mvn 插件配置的所有元素的列表：

<插件>

<groupId>org.apache.portals.jetspeed-2</groupId>

<artifactId>jetspeed-mvn-maven-plugin</artifactId>

<version>${org.apache.portals.jetspeed.version}</version>

<配置>

<targets combine.children="append">

  ...

  <目标>

    <id>...</id>

    <依赖>...</依赖>

    <名称>...</名称>

    <目录>...</目录>

    <目标>...</目标>

    <profiles>...</profiles>

    <属性>

      ...

    </属性>

    <settingsFile>...</settingsFile>

    <mavenOpts>...</mavenOpts>

  </目标>

  ...

</目标>

<defaultTarget>...</defaultTarget>

<useSettings>...</useSettings>

<属性>

  ...

</属性>

<mavenOpts>...</mavenOpts>
</配置>

</插件>

##### 2.1.4.2.2. **默认插件配置**

从上面的配置概述可以看出，主要的配置元素是目标列表和目标元素本身。

###### 2.1.4.2.2.1. **<targets combine.children="append">**

配置的一个重要且**必不可少**的部分是为元素 **combine.children="append"**指定的属性。**targets**

如果未定义，Maven 2 插件配置解析（使用 Xpp3）默认合并子元素的配置元素！此默认行为仅允许为某个配置元素 定义**覆盖属性。**

但是，对于目标配置，这不是很方便，因为它需要为元素指定所有可选属性，**task**以防止从不相关的先前定义的目标元素中“合并”属性值。

为了解决这个不便，**combine.children="append"**可以在父元素上指定一个属性，以便在解析子元素时 使用追加 而不是合并。

因此，请确保始终使用**<targets combine.children="append">**以确保实际按照指定解析目标配置！

###### 2.1.4.2.2.2. **常规选项**

除了目标之外，还可以指定一些额外的（所有可选的）配置元素：


| **元素** | **描述**                                                                                                                                                                                                     |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 默认目标   | jetspeed:mvn的预期用途是在命令行上使用**\$mvn jetspeed:mvn -Dtarget=<target id>**.如果确实需要默认（因此非常常见）目标，则可以在此处指定其**id**属性，如果未指定命令行参数，则将使用该属性。                 |
| 使用设置   | **default: true**用于执行特定目标的自定义Maven设置的可选用法将在下面进一步解释，但是**jetspeed-mvn-settings.xml**如果没有为目标配置特定**settingsFile**本身，则此设置决定了文件的默认查找和使用。            |
| 特性       | 提供给特定目标的Maven执行环境的运行时属性的使用将在下面进一步解释，但可以在此处配置要用于所有目标的**全局**属性（可以覆盖）。定义属性的格式与标准Maven项目属性的格式相同： <property-name>值</property-name> |
| mavenOpts  | **default: none**可以在此处指定为目标执行环境设置的默认Maven运行时选项。对于特定目标，可以使用其自己的**mavenOpts**配置覆盖这些目标。                                                                        |

##### 2.1.4.2.3. **目标配置**

在单独的 Maven 环境中执行目标需要三组不同的参数：

· 目标本身及其可能依赖的其他目标

· 要调用的（自定义）Maven 项目文件

· 要使用的目标、配置文件、设置和运行时属性

###### 2.1.4.2.3.1. **目标识别及其依赖**

目标由其所需**<id/>**元素唯一标识（在当前项目范围内）：

<目标>

<id>目标</id>

...

</目标>

**<depends/>**或者，可以使用逗号分隔的其他目标值列表的元素 指定对其他目标的依赖关系**id**：

<目标>

<id>目标1</id>

<依赖/>

...

</目标>

<目标>

<id>目标2</id>

<depends>target1</depends>

...

</目标>

<目标>

<id>目标3</id>

<depends>target1,target2</depends>

...

</目标>

上面的示例指定**target2**依赖**target1**和**target3**依赖于 **target1**和**target2**。

这表示何时**target3**执行，**target1**并且**target2**需要首先执行（并按该顺序）。

当一个目标依赖链被解析时，依赖将按照定义的顺序被调用，因此单个目标只会被执行 一次，即使多个依赖目标定义了对同一个目标的依赖。

对于上面的例子，实际的执行顺序将是：**target1,target2,target3**， 而不是：**target1,target1,target2,target3**

这意味着对于上面的示例，**target3**实际上可以更简单地定义，因为**target2**已经依赖于**target1**：

<目标>

<id>目标3</id>

<depends>target2</depends>

...

</目标>

###### 2.1.4.2.3.2. **目标 Maven 项目文件**

为目标调用哪个（自定义）Maven 项目文件由（可选）**name**和**dir** 元素确定：

<目标>

<id>dbInit</id>

<名称>数据库</名称>

<dir>@rootdir@/my-portal</dir>

...

</目标>

该**name**元素用于解析名为：jetspeed-mvn- **\${name} -pom.xml 的**自定义Maven 项目文件。

该**dir**元素用于解析确定的目标Maven项目文件的位置。

2.1.4.2.3.2.1. **名称和目录未定义**

如果两者**name**和**dir**都没有定义，jetspeed:mvn 不会对此目标执行任何操作，但会执行它所**depends**在的目标，例如执行：

$mvn jetspeed:mvn -Dtarget=target3

使用以下配置：

<目标>

<id>目标1</id>

<依赖/>

<name>pomA</name>

...

</目标>

<目标>

<id>目标2</id>

<depends>target1</depends>

<name>pomB</name>

...

</目标>

<目标>

<id>目标3</id>

<depends>target2</depends>

</目标>

仍将导致**pomA**并被**pomB**调用。

2.1.4.2.3.2.2. **只有 dir 定义**

如果 only**dir**被定义，jetspeed:mvn 将在指定目录中查找标准的 Maven pom.xml。

文件查找是相对于当前工作目录完成的，例如调用 jetspeed:mvn 的 Maven 项目。

或者，也可以指定一个绝对目录，或者可以使用特殊的@rootdir@ 变量（见下文）。

提示：要调用当前目录中的默认** Maven pom.xml**，请指定 <dir>./</dir>。

2.1.4.2.3.2.3. **仅定义名称**

如果仅定义，jetspeed:mvn 将首先在当前**name**Maven 项目目录中查找名为 jetspeed-mvn- **\${name}** -pom.xml 的自定义 Maven 项目文件，如果未找到，则在父项目中向上搜索（ s) 当前的 Maven 项目。

2.1.4.2.3.2.4. **name 和 dir 都定义了**

当同时定义**name**和时，名为 jetspeed-mvn- **\${name}**dir -pom.xml的自定义 Maven 项目文件必须存在于指定的. **dir**

2.1.4.2.3.2.5. **@根目录@**

特殊变量**@rootdir@**可用于引用当前项目的最顶层 Maven 项目的（绝对）路径。

但是，如果已经为当前 Maven 项目（或其父项目之一）定义了属性**rootdir**，则将使用其值。

2.1.4.2.3.2.6. **执行工作目录**

需要注意的是，在调用已解析（自定义）的 Maven 项目文件之前，当前工作目录将（临时）更改为包含项目文件的目录。因此，所有相关文件和资源引用也将相对于该目录进行解析！

###### 2.1.4.2.3.3. **目标执行参数和环境**

一旦确定了目标，其目标 Maven 项目文件，其执行环境和运行时参数将根据以下（所有可选）元素和为所有目标定义的默认/全局元素（见上文）确定：

<目标>

<id>目标</id>

<名称>数据库</名称>

<dir>@rootdir@</dir>

<goals>流程资源</goals>

<profiles>proddb</profiles>

<属性>

<!-- （默认）生产目标特定属性-->
</属性>

<settingsFile>@rootdir@/prod-settings.xml</settingsFile>

<mavenOpts>-Xms128m -Xmx256m</mavenOpts>

</目标>

2.1.4.2.3.3.1. **目标**

可以使用一个或多个配置文件甚至特定的 Maven 设置文件调用（自定义）目标 Maven 项目文件以运行或多个目标。

**goals**可以选择定义 该元素以指定以逗号分隔的要运行的目标列表：

<目标>目标1，目标2，目标3</目标>

. 如果**goals**未定义该元素，则目标 Maven 项目文件必须具有**defaultGoal**构建元素：

<构建>

<defaultGoal>流程资源</defaultGoal>

</build>

2.1.4.2.3.3.2. **简介**

与目标一样，可以将要使用的一个或多个配置文件（由所有要运行的目标）指定为逗号分隔列表：

<profiles>profile1,profile2,profile3</profiles>

2.1.4.2.3.3.3. **特性**

执行目标的一个非常重要的要求是为 Maven 执行环境提供正确的运行时参数集。

jetspeed:mvn 插件将按以下顺序 为每个目标执行单独 累积要作为运行时（例如 -D）参数提供的一组属性：


| **命令** | **来源**                                       | **抬头**                                                                                                                |
| -------- | ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 1        | <配置><属性/></配置                            | jetspeed:mvn默认配置属性                                                                                                |
| 2        | <目标><属性/></目标>                           | 目标特定属性                                                                                                            |
| 3        | 当前的Maven项目属性                            | 注意：这包括在当前项目的父项目中定义的属性，甚至是默认的Maven设置                                                       |
| 4        | jetspeed-mvn.properties                        | 该文件在当前Maven项目目录中搜索，或者在其父项目目录中向上搜索。找到的属性文件将使用\${}变量替换 **插入已解析的属性。** |
| 5        | jetspeed-mvn-\${目标名称}.properties           | 该文件在当前Maven项目目录中搜索，或者在其父项目目录中向上搜索。找到的属性文件将使用\${}变量替换 **插入已解析的属性。** |
| 6        | jetspeed-mvn-\${目标名称}-${目标id}.properties | 该文件在当前Maven项目目录中搜索，或者在其父项目目录中向上搜索。找到的属性文件将使用\${}变量替换 **插入已解析的属性。** |

jetspeed:mvn 特定的属性文件是单独查找的，例如一个的位置不描述另一个的位置。

警告：请注意从当前** Maven **项目解析的属性，因为这些属性可能会有所不同，具体取决于调用 jetspeed:mvn 的项目文件夹。

2.1.4.2.3.3.4. **使用设置和设置文件**

某些 Maven 配置元素和属性可以或应该只在[Maven 设置](http://maven.apache.org/settings.html)文件中指定，例如安全敏感的服务器参数（用户名、密码等）。

虽然 Maven 默认会从用户的主目录中查找 settings.xml 文件: **\${user.home}/.m2/settings.xml**，但这并不总是很不方便，尤其是当涉及到许多不同的项目时，每个项目都有自己的特定设置要求。

有时，使用项目源（控制）环境本身或在项目源（控制）环境中维护项目特定设置会更方便甚至需要。

jetspeed:mvn 插件可以使用自定义设置文件（默认情况下），该文件由可选配置**useSettings**元素、目标特定**settingsFile**元素或特定属性控制**jetspeed.mvn.settings.xml**。

当 jetspeed:mvn 配置元素 <useSettings>true</useSettings> 被指定（默认情况下）时，jetspeed:mvn 将首先在当前Maven 项目中查找名为 jetspeed-mvn-settings.xml 的自定义 Maven 设置文件目录，如果找不到，则在当前 Maven 项目的父项目中向上搜索。

或者，**settingsFile**可以使用目标元素来使用特定于目标的设置文件，如上面的完整示例目标配置所示。

最后，（特定于目标的）设置文件也可以定义为当前 Maven 项目或其父项目之一的属性，或者使用属性名称在已解析的目标特定属性（确实包含当前 Maven 项目属性）中定义：**jetspeed.mvn.settings.xml**.

指定为**jetspeed.mvn.settings.xml**属性的自定义 Maven 设置文件会否决特定的目标**settingsFile**，并且这些都会否决 jetspeed:mvn 默认**useSettings**配置和查找。

2.1.4.2.3.3.5. **进阶：Maven项目和设置文件变量插值**

进一步配置目标 Maven 项目和/或设置文件的高级功能继承自 [Maven Invoker 插件](http://maven.apache.org/plugins/maven-invoker-plugin/advance-usage.html)，jetspeed:mvn 插件是从该插件派生的。

在实际执行和使用已解析的 Maven 项目和可选设置文件之前，这些文件的插值版本会临时写入磁盘，其中**@**使用已解析的目标属性过滤标记之间的变量（见上文）。

Jetspeed-2 Portal 项目本身在其 jetspeed-mvn-db-init-pom.xml 中使用此功能来初始化测试或生产数据库。

Jetspeed 使用的实际数据库配置属性有一个共同的前缀：要么**org.apache.jetspeed.test.database** 或**org.apache.jetspeed.production.database**。

对于两个不同目标（测试|生产）数据库的初始化，jetspeed-mvn-db-init-pom.xml 使用以下前缀引用这些配置参数**org.apache.jetspeed.@database.type@.database**：

<插件>

<groupId>${pom.groupId}</groupId>

<artifactId>jetspeed-db-maven-plugin</artifactId>

<version>${pom.version}</version>

<配置>

<连接>

  <用户名>${org.apache.jetspeed.@database.type@.database.user}</username>

  <密码>${org.apache.jetspeed.@database.type@.database.password}</password>

  <url>${org.apache.jetspeed.@database.type@.database.url}</url>

  <driver>${org.apache.jetspeed.@database.type@.database.driver}</driver>

</连接>
</配置>

...

用于初始化的单独的 jetspeed-mvn 目标分别为 property 定义了不同的值**database.type**：

<目标>

<id>测试数据库</id>

<name>db-init</name>

<属性>

<database.type>测试</database.type>
</属性>

</目标>

<目标>

<id>产品数据库</id>

<name>db-init</name>

<属性>

<database.type>生产</database.type>
</属性>

</目标>

由于目标项目（和设置）文件的自动插值，只需一个 jetspeed-db:init 插件定义即可处理初始化测试和生产数据库。

此功能还使得以后添加更多目标数据库变得非常容易，例如用于登台目的：只需为 database.type 属性添加另一个值为“staging”的目标（当然还需要提供相应的 org.apache.jetspeed.staging。数据库。* jetspeed-mvn-settings.xml 中的属性）。

2.1.4.2.3.3.6. **mavenOpts**

最后，还可以使用元素为特定目标指定特殊的覆盖 Maven MAVEN\_OPTS 环境变量**mavenOpts**，或者如果未定义，也可以作为所有目标的默认值作为 jetspeed:mvn 配置元素（见上文）。

###### 2.1.4.2.3.4. **目标配置摘要**

下表总结了目标的配置元素：


| **元素** | **描述**                                                                                                                                                                                                                                                   |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ID         | 唯一标识目标的唯一必需元素。                                                                                                                                                                                                                               |
| 依靠       | 此目标所依赖的其他目标id的可选逗号分隔列表，并将预先自动执行                                                                                                                                                                                               |
| 姓名       | 用于查找名为jetspeed-mvn-\${name}-pom.xml的*自定义**Maven**项目文件的目标的可选名称。*如果只定义了元素， 则将使用 **dir**来自的标准Maven pom.xml项目文件。**dir**                                                                                         |
| 目录       | 查找目标的自定义Maven项目文件（使用**name**）的可选目录。如果**name**未定义，则将从该目录使用标准Maven pom.xml项目文件。                                                                                                                                   |
| 目标       | 要在已解析（自定义）Maven项目文件上调用的 Maven 目标的可选逗号分隔列表。如果未定义，则目标Maven项目文件必须**<defaultGoal/>**配置构建元素。                                                                                                                |
| 简介       | 执行解析的（自定义）Maven项目文件时提供的可选的逗号分隔配置文件列表。                                                                                                                                                                                      |
| 特性       | 作为运行时(-D)参数提供的可选目标特定属性。这些属性可以被jetspeed:mvn特定属性文件否决，请参阅上一节。                                                                                                                                                       |
| 设置文件   | 执行此目标时要使用的可选自定义Maven设置文件的位置。如果未定义，则默认的<useSettings/>配置元素值（默认为 true）确定是否改为查找 jetspeed-mvn-settings.xml 文件。注意：这个 settingsFile 也可以用 property 否决**jetspeed.mvn.settings.xml**，请参阅上一节。 |
| mavenOpts  | 要使用的特殊Maven MAVEN\_OPTS Maven环境变量的可选值。如果未定义，将使用（也是可选的）默认<mavenOpts/>配置元素值。                                                                                                                                          |

##### 2.1.4.2.4. **用法**

###### 2.1.4.2.4.1. **显示可用目标**

jetspeed:mvn 插件的一个非常有用的特性是，它可以使用可选的命令行参数显示当前 Maven（子）项目范围内的当前可用目标**-Dlist**：

$mvn jetspeed:mvn -Dlist

例如，对于 Jetspeed 项目本身（2.3.0 版本），将显示以下输出：

[信息] [喷气机速度：MVN]

可用的 jetspeed:mvn 目标：

测试数据库 [测试数据库]

测试一下]

产品数据库 [产品数据库]

演示安装 [演示安装]

演示种子 [演示种子]

最小种子 [最小种子]

演示部署 [演示部署]

演示部署分钟 [演示部署分钟]

演示-部署-dbpsml [演示-部署-dbpsml]

测试安装 [测试数据库，测试安装]

demo-seed-dbpsml [proddb，demo-seed，demo-db，demo-seed-dbpsml]

min-seed-dbpsml [proddb，demo-seed，demo-db，min-seed-dbpsml]

demo-db [proddb，demo-seed，demo-db]

min-db [proddb, min-seed, min-db]

demo-db-psml [proddb，demo-seed，demo-db，demo-seed-dbpsml，demo-db-psml]

演示 [演示安装、proddb、演示种子、演示数据库、演示部署、演示]

min [demo-install, proddb, demo-seed, demo-db, demo-deploy-min, min]

min-dbpsml [demo-install，proddb，demo-seed，demo-db，demo-deploy-min，demo-deploy-dbpsml，min-seed-dbpsml，min-dbpsml]

demo-dbpsml [proddb，demo-seed，demo-db，demo-seed-dbpsml，demo-db-psml，demo-deploy，demo-deploy-dbpsml，demo-dbpsml]

上面的左列显示了使用**-Dtarget=<target id>**命令行参数执行的可用目标。

右列显示了实际的链式目标集，这些目标将作为结果按顺序执行。

关于这些实际 jetspeed 项目目标定义的完整文档在“[从源代码构建](https://portals.apache.org/jetspeed-2/buildguide/maven-2-build.html)”页面上提供。

最后，实际使用 jetspeed:mvn 插件并调用特定目标将非常简单：

$mvn jetspeed:mvn -Dtarget=<目标 ID>

或者，如果还**defaultTarget**为 jetspeed:mvn 插件配置了 a，则即使以下内容也可以使用：

$mvn 喷气机速度:mvn

但通常一个特定的（Jetspeed Portal）项目需要多个目标，在这种情况下， **defaultTarget**不建议定义和使用 a。

##### 2.1.4.2.5. **执行目标**

#### 2.1.4.3. [**解压插件**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-unpack-plugin.html)

Jetspeed Unpack Maven 插件提供了一个目标：**jetspeed-unpack:unpack**可用于从（远程）Maven 工件或本地（存档）文件中提取选定的资源。

在编写此插件时，其他（标准）Maven 插件没有完全提供所需的功能。

[现在，使用标准** Maven **依赖插件dependency:unpack](http://maven.apache.org/plugins/maven-dependency-plugin/unpack-mojo.html)目标或远程资源插件 [remote-resources:process](http://maven.apache.org/plugins/maven-remote-resources-plugin/process-mojo.html)目标 也可以实现其中一些功能 。

但是，最初情况并非如此，jetspeed-unpack 插件仍然更易于配置和使用。此外，该插件提供的相同功能也可以使用完全相同的配置

嵌入到[jetspeed-db:iniit插件中。](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html)

此插件旨在用作附加到 Maven**process-resources**或可能的**generate-resources** 生命周期阶段，用于将预定义的资源嵌入到最终的 Maven 工件（如 war 文件）中，或将此类资源用于集成任务，例如将（可能过滤的）配置文件部署到目标环境应用服务器。

##### 2.1.4.3.1. **支线：jetspeed-portal-resources 工件**

**jetspeed-portal-resources**虽然这个插件无论如何 都不依赖于工件（也不依赖于 Jetspeed-2 的任何其他部分），但它主要用于解压特定的预打包 Jetspeed-2 Portal 资源。

[Jetspeed 门户资源](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-portal-resources.html)页面进一步描述 了jetspeed-portal-resources 工件及其预期用途。

##### 2.1.4.3.2. **快速概览**

这是可以为 jetspeed:unpack 插件配置的所有元素的列表：

<插件>

<groupId>org.apache.portals.jetspeed-2</groupId>

<artifactId>jetspeed-unpack-maven-plugin</artifactId>

<version>${org.apache.portals.jetspeed.version}</version>

<配置>

<解包>

  <神器>...</神器>

  <文件>...</文件>

  <目标目录>...</目标目录>

  <覆盖>...</覆盖>            

  <resources combine.children="append">

    <资源>

      <路径>...</路径>

      <目的地>...</目的地>

      <覆盖>...</覆盖>

      <平面>...</平面>

      <include>...</include>

      <排除>...</排除>

      <名称>...</名称>

    </资源>

    ...

  </资源>

</解包>

<跳过>...</跳过>

<详细>...</详细>
</配置>

</插件>

##### 2.1.4.3.3. **配置**

###### 2.1.4.3.3.1. **资源归档规范和参考**

2.1.4.3.3.1.1. **使用 Maven 工件作为资源存档**

与[jetspeed-db:init](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html)插件和[jetspeed-deploy:deploy](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-deploy-plugin.html)插件一样，jetspeed-unpack 插件可以（并且主要用于）使用从本地 Maven 存储库检索的 Maven 工件作为资源（存档）。

要将 Maven 工件用作资源存档，需要将它们指定为插件依赖项：

<插件>

<groupId>org.apache.portals.jetspeed-2</groupId>

<artifactId>jetspeed-unpack-maven-plugin</artifactId>

<version>${org.apache.portals.jetspeed.version}</version>

...

<依赖项>

<依赖>

  <groupId>org.apache.portals.jetspeed-2</groupId>

  <artifactId>jetspeed-portal-resources</artifactId>

  <version>${org.apache.portals.jetspeed.version}</version>

</依赖>
</依赖>

</插件>

注意：**Maven 2.0**（截至目前，版本 2.0.9）**要求**为插件依赖项定义其** <version/>**，即使在项目 <dependencyManagement/> 部分为同一工件配置了默认版本也是如此。

作为标准的 Maven 功能，如果本地 Maven 存储库还没有这样的依赖项，它将自动（尝试）从远程 Maven 存储库下载它。

2.1.4.3.3.1.2. **将插件依赖项引用为资源存档**

要实际使用指定为插件依赖项的特定资源存档，可以通过以下方式引用它：

<artifact>${groupId}:${artifactId}:${packaging}</artifact>

注意：依赖项的默认打包是**jar**

以**jetspeed-portal-resources**工件为例，其工件参考配置将是：

<artifact>org.apache.portals.jetspeed-2:jetspeed-portal-resources:jar</artifact>

[注意：** jetspeed-db:init**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html)和 [jetspeed-deploy:deploy](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-deploy-plugin.html)插件 也使用相同类型的（远程）Maven 存储库工件的定义和使用。

2.1.4.3.3.1.3. **使用本地文件存档**

或者，也可以直接使用本地存档文件，在这种情况下，**file** 应该指定一个元素而不是一个**artifact**元素：

<file>localArchiveFilePath</file>

###### 2.1.4.3.3.2. **插件配置**

jetspeed-unpack 插件除了特定配置外，还允许配置两个通用选项**unpack**：


| **元素** | **描述**                                                                                                                                                                                                                                                                               |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 跳过       | **default: false**此可选元素主要用于允许在某些条件下跳过插件执行，例如*不*提取仅在实际执行单元测试时才需要的资源：<phase>流程测试资源</phase> <配置 <skip>${maven.test.skip}</skip> ... </配置>Maven总是调用附加到**process-test-resources**阶段的插件，不管它是否真的要执行单元测试。 |
| 冗长的     | **default: false**解压资源时，该**verbose**设置控制是否执行详细日志记录提取哪些文件。                                                                                                                                                                                                  |

###### 2.1.4.3.3.3. **解压配置**

如上所述，要解压的实际资源存档必须指定为**artifact**reference 或 local **file**。

此外，还可以指定另外两个可选的解包配置元素：


| **元素** | **描述**                                                                                                                                                                                                                                                |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 目标目录   | **default:\${project.build.directory}**targetDirectory用作从资源存档中提取选定资源的*基本目录。*如果此目录尚不存在，它将由插件在（可能）提取资源之前自动创建。                                                                                          |
| 覆盖       | **default: true**当资源存档中的选定资源已存在于其目标目录中时，覆盖设置将确定现有资源是否被覆盖，即使它具有比存档资源更新的时间戳。注意：如果存档资源具有更新的时间戳，则现有资源将*始终*被覆盖。此设置也可以针对特定**resource**配置被否决（见下文）。 |

###### 2.1.4.3.3.4. **<resources combine.children="append">**

配置中一个可能非常重要的部分是为元素 **combine.children="append"**指定的属性。**resources**

如果未定义，Maven 2 插件配置解析（使用 Xpp3）默认合并子元素的配置元素！此默认行为仅允许为某个配置元素 定义**覆盖属性。**

但是，对于资源配置，这不是很方便，因为它需要为元素指定所有可选属性，**resource**以防止从不相关的先前定义的资源元素中“合并”属性值。

为了解决这个不便，**combine.children="append"**可以在父元素上指定一个属性，以便在解析子元素时 使用追加 而不是合并。

对于 jetspeed-unpack 插件，建议定义此属性，**除非**仅配置了一个或完全相同的资源子元素（例如，使用所有相同的元素集）。

###### 2.1.4.3.3.5. **资源配置**

jetspeed-unpack 插件配置的最后一部分涉及解包的实际资源：

<资源>

<路径>/conf/tomcat</路径>

<destination>tomcat</destination>

<include>context.xml</include>

</资源>

上面的示例将从资源存档中的 conf/tomcat 文件夹中提取 context.xml 资源，并将其写入项目构建目录的子目录 tomcat 或以其他方式指定的（基本）targetDirectory。

注意：不需要指定任何资源配置。如果没有指定，将提取资源档案中的 所有资源！

可以为特定**resource**配置定义以下（所有可选）元素：


| **元素** | **描述**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 小路       | **default: /**该路径将资源存档中的子文件夹指定为搜索要提取的资源的（基本）路径。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 目的地     | **default: \${configuration.targetDirectory}**如果定义，目标指定默认项目构建目录的子目录或**targetDirectory** 插件的其他指定的子目录，匹配的资源将被解包。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 覆盖       | **default: \${unpack.overwrite}** 如果已定义，overwrite 将覆盖 unpack 元素的默认覆盖设置（见上文）。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 平坦的     | **default: false**默认情况下，要从资源存档中提取的资源使用它们在资源存档中的（基本）路径的相对位置被写出到目标目标目录的子目录（见上文）。例如，使用以下（可能不正确）资源配置：<资源> <路径>配置</路径> <destination>tomcat</destination> <include>tomcat/context.xml</include></资源>匹配的context.xml资源将被写入： ${targetDirectory}/tomcat/tomcat/context.xml 对于这种配置（有时需要这些配置），定义<flat>true<flat>将“删除”资源的相对位置。然后，只使用它的条目名称，结果（可能需要）：\${targetDirectory}/tomcat/context.xml 当然，同样的结果也可以（甚至更简单）使用：<资源> <路径>配置</路径> <include>tomcat/context.xml</include></资源> |
| 包括       | **default:\${resource.path}/\*\***include元素可以定义要提取的资源的逗号分隔列表。这些可能包含（标准Ant类）通配符和相对于资源存档中的（基本）路径子文件夹的子文件夹引用：<include>profile.xml,security*.xml,boot/*.xml</include>                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 排除       | **default:***none*可以使用exclude元素从提取中排除可能要提取的经过加工的资源（请参见上面的 include）。与include元素一样，exclude 元素可以定义以逗号分隔的要*排除*的资源列表。这些也可能包含（标准Ant类）通配符和相对于资源存档中的（基本）路径子文件夹的子文件夹引用：<exclude>security-spi*.xml,security-managers.xml</exclude>                                                                                                                                                                                                                                                                                                                        |
| 姓名       | **default:***none*从资源档案中提取的单个资源的新文件名：<name>j2-seed.xml</name>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

从上面可以确定，由于所有资源配置元素都是可选的，指定一个空的 <resource/> 定义将简单地将所有资源从存档中提取到 targetDirectory。

##### 2.1.4.3.4. **例子**

###### 2.1.4.3.4.1. **解压jetspeed单元测试资源**

以下示例取自 jetspeed-profiler 组件的 Maven 项目文件，根据需要提取了几个 Spring 程序集文件、db-ojb 文件夹中的所有文件和 seed/min/j2-seed.xml 文件到项目 testOutputDirectory 以运行单元测试：

<插件>

<groupId>${pom.groupId}</groupId>

<artifactId>jetspeed-unpack-maven-plugin</artifactId>

<version>${pom.version}</version>

<执行>

<执行>

  <id>解压测试资源</id>

  <目标>

    <goal>解压</goal>

  </目标>

  <phase>流程测试资源</phase>

  <配置>

    <skip>${maven.test.skip}</skip>

    <解包>

      <artifact>org.apache.portals.jetspeed-2:jetspeed-portal-resources:jar</artifact>

      <targetDirectory>${project.build.testOutputDirectory}</targetDirectory>

      <资源>

        <资源>

          <路径>程序集</路径>

          <include>profiler.xml,transaction.xml,cache.xml,security-*.xml,boot/datasource.xml</include>

        </资源>

        <资源>

          <path>db-ojb</path>

        </资源>

        <资源>

          <路径>种子/分钟</路径>

          <include>j2-seed.xml</include>

        </资源>

      </资源>

    </解包>

  </配置>

</执行>
</执行>

</插件

这个例子的有趣部分是**没有**指定资源存档！

但上面的示例确实有效，因为 Jetspeed-2 Portal 项目的根 Maven 项目文件已经在其 dependencyManagement 部分中将 jetspeed-portal-resources 工件定义为 jetspeed-unpack 插件的默认依赖项：

<插件>

<groupId>org.apache.portals.jetspeed-2</groupId>

<artifactId>jetspeed-unpack-maven-plugin</artifactId>

<version>${pom.version}</version>

<依赖项>

<依赖>

  <groupId>${groupId}</groupId>

  <artifactId>jetspeed-portal-resources</artifactId>

  <version>${pom.version}</version>

</依赖>
</依赖>

</插件>

但请注意：这是一个特殊的用例，仅在（预）配置了一个依赖项时才有效。

##### 2.1.4.3.5. **部署前解压要过滤的tomcat context.xml**

一个更复杂和常见的用例是在 generate-resources 生命周期阶段提取特定资源，以便对其进行过滤（使用标准 Maven 资源插件）：

<插件>

<插件>

<groupId>org.apache.portals.jetspeed-2</groupId>

<artifactId>jetspeed-unpack-maven-plugin</artifactId>

<version>${org.apache.portals.jetspeed.version}</version>

<执行>

  <执行>

    <id>解压应用服务器</id>

    <目标>

      <goal>解压</goal>

    </目标>

    <phase>生成资源</phase>

    <配置>

      <解包>

        <artifact>org.apache.portals.jetspeed-2:jetspeed-portal-resources:jar</artifact>

        <资源>

          <资源>

            <路径>配置</路径>

            <include>tomcat/context.xml</include>

          </资源>

        </资源>

      </解包>

    </配置>

  </执行>

</执行>
<依赖项>

<依赖>

  <groupId>org.apache.portals.jetspeed-2</groupId>

  <artifactId>jetspeed-portal-resources</artifactId>

  <version>${org.apache.portals.jetspeed.version}</version>

</依赖>
</依赖>

</插件>

<插件>

<groupId>org.apache.maven.plugins</groupId>

<artifactId>maven-resources-plugin</artifactId>

<执行>

  <执行>

    <id>资源</id>

    <目标>

      <目标>资源</目标>

    </目标>

    <phase>流程资源</phase>

  </执行>

</执行>
</插件>

</插件>

...

<资源>

<资源>

<目录>${project.build.directory}/tomcat</directory>

<targetPath>../resources</targetPath>

<过滤>真</过滤>
</资源>

</资源>

此示例取自使用[jetspeed-mvn](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-mvn-plugin.html)插件调用的自定义 Maven 项目文件，用于在 Tomcat 服务器上部署自定义 Jetspeed-2 门户。

本示例中还配置了标准 Maven 资源插件，因为自定义 jetspeed-mvn Maven 项目文件通常使用 <packaging>pom</packaging> 进行配置。

这种自定义的 jetspeed-mvn 项目文件用于执行特定的集成任务，而不是用于生成像 jar 或 war 文件这样的“正常”工件。

但是由于 pom 项目没有附加到其生命周期的 maven-resources-plugin，因此需要直接对其进行配置，以使其在流程资源阶段执行所需的资源过滤。

#### 2.1.4.4. [**数据库初始化插件**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-init-plugin.html)

jetspeed-db:init Maven 插件能够执行许多与数据库相关的任务以初始化（Jetspeed 门户）生产数据库，但也可用于在（集成）测试构建期间设置单元测试所需的数据库数据。

可以配置 以下独立任务：

· （远程）资源档案的解包，如数据库（ddl）sql脚本

· 针对数据库执行选定的 sql 脚本

· 执行 jetspeed-serializer 组件以初始化 Jetspeed Portal 数据库

· 执行 jetspeed-serializer 组件以将 Jetspeed PSML 加载到数据库中

[待定]

#### 2.1.4.5. [**数据库 ddl 插件**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-db-ddl-plugin.html)

[待定]

#### 2.1.4.6. [**部署插件**](https://portals.apache.org/jetspeed-2/buildguide/jetspeed-deploy-plugin.html)

[待定]

## 2.2. [**条件弹簧**](https://portals.apache.org/jetspeed-2/devguide/spring-config.html)

Jetspeed 为特定的配置设置提供了非常灵活的方法。

Jetspeed 组件最初是从**/WEB-INF/assembly/**文件夹加载的，而默认配置属性是从文件夹加载的**/WEB-INF/conf/jetspeed.properties.**

初始/默认配置可以通过**/WEB-INF/assembly/override/**文件夹覆盖，而覆盖/附加值可以通过**/WEB-INF/conf/override.properties.**

另一个新特性是有条件的 Spring 程序集加载。Jetspeed 提供了一个扩展的 BeanFactory，它根据预定义的配置检查加载的 Spring BeanDefinition 是否有一些额外的元数据（在 Spring 配置本身中定义），可以“阻止”在 Spring 中注册 BeanDefinition，从而有效地过滤掉某些定义。

### 2.2.1. **条件弹簧组件加载**

#### 2.2.1.1. **Jetspeed 类别元数据**

在 Jetspeed 程序集文件中，bean 定义应具有**j2:cat**如下示例的元数据：

<bean name="xmlPageManager" class="org.apache.jetspeed.page.psml.CastorXmlPageManager">

<meta key="j2:cat" value="xmlPageManager 或 pageSerializer" />

...
</豆>

在上面的示例中，**xmlPageManager**bean 定义包含在两个类别中：**xmlPageManager**和**pageSerializer**. 如果 Jetspeed 的 Spring 过滤器键设置包含其中一个类别，则**xmlPageManager**bean 定义将被注册。否则，bean 定义将被忽略。通过 Spring 过滤键设置，程序集文件中的 bean 定义将根据它们的类别进行过滤。

#### 2.2.1.2. **Spring过滤器键和类别设置**

Jetspeed 的 Spring 过滤器设置在**/WEB-INF/conf/spring-filter.properties**.

在该文件中，默认提供以下类别定义：


| **筛选键**                  | **映射类别**                                                                                                                  | **描述**                                                                                                   |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| 默认                        | 默认                                                                                                                          | 大多数常见组件的默认类别                                                                                   |
| 基地门户                    | \${默认}, jndiDS, xmlPageManager                                                                                              | 门户实例的基本类别，用于其他类别定义。在这个类别中，提供了数据源组件和基于xml的页面管理器。                |
| 门户网站                    | \${basePortal}, dbSecurity                                                                                                    | 门户实例的默认类别。通过basePortal类的组件，提供了基于数据库的安全组件。                                   |
| 门户网站.ldap               | \${basePortal}，ldapSecurity                                                                                                  | 门户实例的类别。通过basePortal类别的组件，提供了基于 LDAP 的安全组件。                                     |
| 门户网站.dbPageManager      | \${默认}, jndiDS, dbPageManager, dbSecurity                                                                                   | 门户实例的类别。在此类别中，提供了默认组件、数据源组件和基于数据库的页面管理器和基于数据库的安全组件。     |
| 门户网站.dbPageManager.ldap | \${default}、jndiDS、dbPageManager、ldapSecurity                                                                              | 门户实例的类别。在此类别中，提供了默认组件、数据源组件和基于数据库的页面管理器以及基于LDAP的安全组件。     |
| baseSerializer              | jdbcDS、序列化程序、功能、安全性、分析器、注册表、搜索、事务、缓存、首选项、springProperties、noRequestContext、noPageManager | Jetspeed串行器的基本类别，用于其他串行器类别定义。在此类别中，提供了播种和序列化 Jetspeed 数据的必要组件。 |
| 串行器                      | \${baseSerializer}, dbSecurity                                                                                                | 序列化程序的默认类别。在此类别中，提供了基于数据库的安全组件。                                             |
| 序列化程序.ldap             | \${baseSerializer}, ldapSecurity                                                                                              | 序列化程序的类别。在此类别中，提供了基于LDAP的安全组件。                                                   |
| 页面序列化器                | jdbcDS、基础、pageSerializer、事务、springProperties、安全、dbSecurity、缓存                                                  | 页面序列化程序的类别。                                                                                     |

注意：**\${} **括起来的表达式将被引用的属性值扩展。

默认情况下，门户实例的过滤器键设置为**portal**。要更改这一点，您可以**spring.filter.key**在以下属性文件之一中 定义一个属性**/WEB-INF/conf/spring-filter-key.properties**：**/WEB-INF/conf/override.properties**或**/WEB-INF/conf/jetspeed.properties**. 例如，您可以将 Jetspeed Portal 与基于 LDAP 的安全组件一起使用：

spring.filter.key = 门户.ldap

#### 2.2.1.3. **Spring 过滤器键和动态 Bean 别名**

因为每个 bean 的 id 在 bean 所在的 BeanFactory 或 ApplicationContext 中必须是唯一的，所以我们不能对多个不同的 bean 使用相同的 bean id。

例如，可以有两个选项来选择页面管理器 bean 组件：基于 xml 的页面管理器或基于数据库的页面管理器。如果其他一些 bean 应该引用过滤页面管理器，则它们应该与过滤页面管理器分组在同一类别中。因此，应该有许多冗余的 bean 定义，这使得维护非常困难。

因此，Jetspeed 提供了一种使用 spring bean 过滤解决方案动态别名 bean 的方法。在以下示例中，前两个 bean 定义没有 id，但它们具有相同的**j2:alias**元数据值。Jetspeed 自定义 BeanFactory 根据此元数据动态注册别名。最后，最后一个 bean 定义可以使用别名来引用选定的 bean **org.apache.jetspeed.page.PageManager**，。

<bean class="org.springframework.beans.factory.config.BeanReferenceFactoryBean">

<meta key="j2:cat" value="xmlPageManager" />

<meta key="j2:alias" value="org.apache.jetspeed.page.PageManager" />

<property name="targetBeanName" value="xmlPageManager" />

</豆>

<bean class="org.springframework.beans.factory.config.BeanReferenceFactoryBean">

<meta key="j2:cat" value="dbPageManager" />

<meta key="j2:alias" value="org.apache.jetspeed.page.PageManager" />

<property name="targetBeanName" value="dbPageManager" />

</豆>

<bean id="org.apache.jetspeed.portalsite.PortalSite" name="portalSite"

class="org.apache.jetspeed.portalsite.impl.PortalSiteImpl">

<meta key="j2:cat" value="default" />

<constructor-arg index="0">

<ref bean="org.apache.jetspeed.page.PageManager" />
</constructor-arg>

</豆>

注意：多个别名可以通过逗号或空格分隔的字符串设置为** j2:alias **元数据值。

# 3. **Jetspeed 组件**

## 3.1. [**安全架构**](https://portals.apache.org/jetspeed-2/devguide/guide-security.html)

[此处 ](https://portals.apache.org/jetspeed-2/devguide/arch.html)提供了 Jetspeed-2 安全架构的概述 。

**认证配置指南**

Jetspeed-2 提供了一个 [LoginModule 实现 ](https://portals.apache.org/jetspeed-2/devguide/login-module.html)，它利用安全 SPI 模型与多种身份验证机制进行交互。

Jetspeed 身份验证配置由位于[门户应用程序组合目录中的](https://portals.apache.org/jetspeed-2/deployguide/config-overrides.html)*security-spi-atn.xml*管理。Jetspeed-2 支持针对以下各项的身份验证：

· [关系数据库](#security-spi-atn_xml)（默认身份验证实现）。

· [LDAP 身份验证](https://portals.apache.org/jetspeed-2/deployguide/ldap.html)实现。

**授权配置指南**

Jetspeed-2 提供了一个[关系数据库支持的** JAAS **策略实现](https://portals.apache.org/jetspeed-2/devguide/atz-jaas.html)。

Jetspeed-2 授权实现也依赖于 SPI 模型，并通过**security-spi-atz.xml**. 配置详细信息可[在此处](https://portals.apache.org/jetspeed-2/deployguide/security-config.html)获得。

### 3.1.1. [**安全概念**](https://portals.apache.org/jetspeed-2/devguide/dev-security.html)

Jetspeed 2 安全架构提供了一套全面的安全服务，可用于保护各种类型的门户资源。安全服务实现完全独立于其他门户服务，并且可以在门户应用程序之外重用。Jetspeed 2 安全服务的核心是完全依赖 JAAS 向门户提供身份验证和授权服务：

· 身份验证服务是通过使用 JAAS 登录模块来实现的。

· 授权服务是通过使用自定义 JAAS 策略来实现的。

已实现身份验证和授权服务，目的是为底层应用程序服务器安全框架提供直接插件。Jetspeed 2 可以利用底层应用服务器登录模块以及通过使用 JACC，即 J2EE 1.4 中可用的应用服务器策略管理功能（请参阅 [API 规范](http://java.sun.com/j2ee/javaacc/) ）。

#### 3.1.1.1. **Jetspeed 2 安全服务**

JAAS 定义了身份验证和授权合同，但没有指定任何安全资源管理指南。Jetspeed 2 提供了一组模块化组件，旨在为门户安全组件提供管理功能。

利用 Jetspeed 2 组件、架构，安全服务提供了一组松散耦合的组件，提供专门的服务：

· UserManager：提供用户管理能力的服务。

· GroupManager：提供组管理能力的服务。

· RoleManager：提供角色管理能力的服务。

· PermissionManager：提供权限管理能力的服务。

#### 3.1.1.2. **模块化和可插拔架构**

Jetspeed 2 安全组件使用 [依赖注入](http://martinfowler.com/articles/injection.html)进行组装 。默认情况下，Jetspeed 使用 [Spring Framework](http://www.springframework.org/) 作为其默认 IoC 容器。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps1.png) Jetspeed 2 安全服务建立在一组通过 SPI 模型公开的模块化和可扩展安全模块之上。SPI 模型提供了通过修改和配置专用处理程序来修改 Jetspeed 粗化安全服务（UserManager、RoleManager、GroupManager）行为的能力。例如，Jetspeed 安全服务可以配置为通过默认的 Jetspeed 存储或通过 LDAP 存储或两者来检索用户安全主体。

一种 **SecurityProvider** 向安全服务公开配置的 SPI 处理程序。Jetspeed 组件组装（基于 Spring）架构提供了一种重新配置安全服务以满足特定实现需求的简单方法。

#### 3.1.1.3. **基于角色的访问控制**

Jetspeed 2 中的基于角色的访问控制 (RBAC) 支持多种层次结构解析策略，如 [访问控制中层次结构的使用中](http://www.doc.ic.ac.uk/~ecl1/wiki/lib/exe/fetch.php?id=emil:researchthemes:pubbytheme&cache=cache&media=research:papers:1999rbac.pdf)定义的那样 。有关详细信息，请参阅[层次结构管理概述](https://portals.apache.org/jetspeed-2/devguide/hierarchy.html)。

### 3.1.2. [**安全 2.3 框架**](https://portals.apache.org/jetspeed-2/devguide/new-security.html)

在 2.3 版中，Jetspeed 引入了一个新的安全框架。2.3 安全基于安全关联引擎，使您能够引入自己的安全组件并与其他现有或新的安全组件建立关联。

#### 3.1.2.1. **关键概念：科目、校长、证书**

Jetspeed 支持 JAAS（Java 身份验证和授权服务）定义的基于主题的安全性。主题是安全实体（如人）的安全信息的集合。一个主体可以有多个身份，也称为主体。例如，登录到 Jetspeed 门户的用户与一个主题相关联，该主题包含一个用户主体、零个或多个角色主体、零个或多个组主体等。每个主体都可以与一组权限相关联，允许用户执行某些操作，如访问页面、更新受保护对象等。最后，Jetspeed 中的用户主体可以与凭据相关联。简单地说，凭证就是用户名/密码组合。

#### 3.1.2.2. **Jetspeed 安全组件**

上述所有安全身份信息均由 Jetspeed 安全组件管理。Jetspeed 安全组件提供了一种访问和更新主体、凭证和权限数据的机制。当用户在 Jetspeed 中进行身份验证时，会根据用户在登录时提供的凭据为该用户解析用户主体。然后一个用户主体可以与其他几个主体相关联，这些主体可以是相同的（用户主体）或不同的类型（例如角色、组、..）。主体以嵌套方式解析，这意味着与用户主体关联的每个主体也可以与其他主体关联，而其他主体又可以与其他主体关联等。以这种方式找到的最终主体集合被聚合并附加到为经过身份验证的用户解析的主题。主题在整个 Jetspeed 中用于安全目的，也可以由 portlet 应用程序使用，以使用标准 JAAS API 保护自定义对象。

#### 3.1.2.3. **可插拔安全架构：适应不同的安全模型**

每个项目通常都需要不同的安全模型，安全主体之间的有意义的关系对该项目有意义。大多数项目都可以使用标准的主体类型，例如用户、角色和组，并在这些主体类型之间定期关联，例如用户是角色或组的成员，组是角色的成员等。有然而，也有项目，它超越了这一点，需要新的主体类型和主体类型之间的自定义关联。这些项目需要一个可插入的安全架构，可以轻松添加新的主体类型和主体关联。这正是 Jetspeed 安全组件所提供的。最好通过说明自定义安全模型来解释这一点，其中用户与组织相关。Jetspeed 包含对用户、组和角色以及它们之间的关联的内置支持，但不支持组织以及用户和组织之间的关联。但是，为了实现这一点，可以对插件组织进行以下更改：

· 创建一个新类“组织”，实现 JetspeedPrincipal

· 基于 BaseJetspeedPrincipalManager 实现一个 OrganizationManager。

· 在用户和组织主体类型之间配置“isMemberOf”关联处理程序

OrganizationManager 是一个强类型管理器，具有访问和存储组织的方法。然而，BaseJetspeedPrincipalManager 类是一个弱类型管理器，它只对抽象主体进行操作。这意味着在大多数情况下，OrganizationManager 类可以委托回基类，除了一些特定的组织处理和将抽象主体类型转换回组织实例。

在这种情况下，配置用户和组织之间的关联非常简单，因为 Jetspeed 默认提供了“isMemberOf”关联处理程序。配置它是指定该处理程序的新实例并将其连接到 UserManager 和 OrganizationManager 的问题。自定义安全模型设置如图 1 所示。![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps2.png)*图 1：与组织一起扩展安全模型*

#### 3.1.2.4. **主体和属性**

Jetspeed 主体基本上只是一组描述主体的安全属性。这些属性是自定义的，并且可能因项目而异。例如，用户主体可以具有联系信息属性。组织负责人（来自上面的示例）可以将办公室的地理坐标作为属性。可以通过 Spring 为每个主体类型配置允许的属性集。除了属性之外，主体在其使用和访问方面也有一些可以配置的约束，例如主体是否为只读、是否可以删除、是否启用等。

#### 3.1.2.5. **主要协会**

主体关联是两个主体之间的关系，其中关系总是有一个方向：它从一个主体到另一个主体。例如，在“用户是组的一部分”关系中，用户是关系的起点（从主体），组是关系的终点（到主体）。Jetspeed Security API 中使用了使用“to”和“from”的命名约定。一个示例是 JetspeedPrincipalManager 接口中名为 getAssociatedTo(..) 的方法，该方法在给定代表关联“到”端的主体名称和关联类型的情况下获取关联主体列表。返回的委托人列表代表关联中的“来自”委托人。协会有几个特点，影响关联中主体的创建和删除，或影响主体之间建立关联的方式。以下列表包含这些特征的概述：


| **特征** | **描述**                                   |
| -------- | ------------------------------------------ |
| 必需的   | 没有此关联就无法创建“来自”主体           |
| 依赖的   | 当“to”主体被删除时，“from”主体将被删除 |
| 单数     | “from”主体最多可以关联一次               |
| 主导的   | “to”主体最多可以关联一次                 |

所有这些特性都是通过 Spring 为关联配置的。

Jetspeed 关联的内置实现（并且应该）独立于特定的主体类型。这样做的好处是关联是可插入的，并且可以在不同的主体类型对之间重复使用。

#### 3.1.2.6. **主体和关联的存储**

Jetspeed 安全组件的存储引擎使用数据库来存储和检索安全数据。通过只允许一种类型的数据存储，Jetspeed 内部使用的存储和检索方法可以得到优化和微调。另一个优点是可以对安全数据进行更复杂的查询，如果存储引擎以可以支持任何数据存储的方式进行抽象，这将很难实现。

如果 Jetspeed 中的安全模型使用新的主体和/或关联进行扩展，则无需更改数据库脚本或与数据库相关的其他代码。Jetspeed 的通用存储引擎将负责存储和检索数据。尽管存储引擎在内部运行在数据库之上，但您可以从另一个数据存储同步数据。这将在下一节中讨论。

#### 3.1.2.7. **同步和复制**

安全数据可以从外部数据存储同步，并映射到 Jetspeed 内部使用的数据库。目前，LDAP 是 Jetspeed 支持的唯一外部数据存储类型。LDAP 数据可以在启动时或用户身份验证时定期同步。同步用户认证时，仅同步与该用户相关的数据。复制是指每当数据库中的安全数据更新时，将安全数据写回外部存储。同步是一种确保外部数据存储的内容与内部数据库相同的机制，其中外部数据存储具有最高优先级。LDAP 同步和复制在 LDAP 映射指南中有更详细的讨论。

#### 3.1.2.8. **证书**

#### 3.1.2.9. **权限**

### 3.1.3. [**架构概述**](https://portals.apache.org/jetspeed-2/devguide/arch.html)

在 2.3 版中，Jetspeed 引入了一个新的安全框架。2.3 安全基于安全关联引擎，使您能够引入自己的安全组件并与其他现有或新的安全组件建立关联。

#### 3.1.3.1. **关键概念：科目、校长、证书**

Jetspeed 支持 JAAS（Java 身份验证和授权服务）定义的基于主题的安全性。主题是安全实体（如人）的安全信息的集合。一个主体可以有多个身份，也称为主体。例如，登录到 Jetspeed 门户的用户与一个主题相关联，该主题包含一个用户主体、零个或多个角色主体、零个或多个组主体等。每个主体都可以与一组权限相关联，允许用户执行某些操作，如访问页面、更新受保护对象等。最后，Jetspeed 中的用户主体可以与凭据相关联。简单地说，凭证就是用户名/密码组合。

#### 3.1.3.2. **Jetspeed 安全组件**

上述所有安全身份信息均由 Jetspeed 安全组件管理。Jetspeed 安全组件提供了一种访问和更新主体、凭证和权限数据的机制。当用户在 Jetspeed 中进行身份验证时，会根据用户在登录时提供的凭据为该用户解析用户主体。然后一个用户主体可以与其他几个主体相关联，这些主体可以是相同的（用户主体）或不同的类型（例如角色、组、..）。主体以嵌套方式解析，这意味着与用户主体关联的每个主体也可以与其他主体关联，而其他主体又可以与其他主体关联等。以这种方式找到的最终主体集合被聚合并附加到为经过身份验证的用户解析的主题。主题在整个 Jetspeed 中用于安全目的，也可以由 portlet 应用程序使用，以使用标准 JAAS API 保护自定义对象。

#### 3.1.3.3. **可插拔安全架构：适应不同的安全模型**

每个项目通常都需要不同的安全模型，安全主体之间的有意义的关系对该项目有意义。大多数项目都可以使用标准的主体类型，例如用户、角色和组，并在这些主体类型之间定期关联，例如用户是角色或组的成员，组是角色的成员等。有然而，也有项目，它超越了这一点，需要新的主体类型和主体类型之间的自定义关联。这些项目需要一个可插入的安全架构，可以轻松添加新的主体类型和主体关联。这正是 Jetspeed 安全组件所提供的。最好通过说明自定义安全模型来解释这一点，其中用户与组织相关。Jetspeed 包含对用户、组和角色以及它们之间的关联的内置支持，但不支持组织以及用户和组织之间的关联。但是，为了实现这一点，可以对插件组织进行以下更改：

· 创建一个新类“组织”，实现 JetspeedPrincipal

· 基于 BaseJetspeedPrincipalManager 实现一个 OrganizationManager。

· 在用户和组织主体类型之间配置“isMemberOf”关联处理程序

OrganizationManager 是一个强类型管理器，具有访问和存储组织的方法。然而，BaseJetspeedPrincipalManager 类是一个弱类型管理器，它只对抽象主体进行操作。这意味着在大多数情况下，OrganizationManager 类可以委托回基类，除了一些特定的组织处理和将抽象主体类型转换回组织实例。

在这种情况下，配置用户和组织之间的关联非常简单，因为 Jetspeed 默认提供了“isMemberOf”关联处理程序。配置它是指定该处理程序的新实例并将其连接到 UserManager 和 OrganizationManager 的问题。自定义安全模型设置如图 1 所示。![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps3.png)*图 1：与组织一起扩展安全模型*

#### 3.1.3.4. **主体和属性**

Jetspeed 主体基本上只是一组描述主体的安全属性。这些属性是自定义的，并且可能因项目而异。例如，用户主体可以具有联系信息属性。组织负责人（来自上面的示例）可以将办公室的地理坐标作为属性。可以通过 Spring 为每个主体类型配置允许的属性集。除了属性之外，主体在其使用和访问方面也有一些可以配置的约束，例如主体是否为只读、是否可以删除、是否启用等。

#### 3.1.3.5. **主要协会**

主体关联是两个主体之间的关系，其中关系总是有一个方向：它从一个主体到另一个主体。例如，在“用户是组的一部分”关系中，用户是关系的起点（从主体），组是关系的终点（到主体）。Jetspeed Security API 中使用了使用“to”和“from”的命名约定。一个示例是 JetspeedPrincipalManager 接口中名为 getAssociatedTo(..) 的方法，该方法在给定代表关联“到”端的主体名称和关联类型的情况下获取关联主体列表。返回的委托人列表代表关联中的“来自”委托人。协会有几个特点，影响关联中主体的创建和删除，或影响主体之间建立关联的方式。以下列表包含这些特征的概述：


| **特征** | **描述**                                   |
| -------- | ------------------------------------------ |
| 必需的   | 没有此关联就无法创建“来自”主体           |
| 依赖的   | 当“to”主体被删除时，“from”主体将被删除 |
| 单数     | “from”主体最多可以关联一次               |
| 主导的   | “to”主体最多可以关联一次                 |

所有这些特性都是通过 Spring 为关联配置的。

Jetspeed 关联的内置实现（并且应该）独立于特定的主体类型。这样做的好处是关联是可插入的，并且可以在不同的主体类型对之间重复使用。

#### 3.1.3.6. **主体和关联的存储**

Jetspeed 安全组件的存储引擎使用数据库来存储和检索安全数据。通过只允许一种类型的数据存储，Jetspeed 内部使用的存储和检索方法可以得到优化和微调。另一个优点是可以对安全数据进行更复杂的查询，如果存储引擎以可以支持任何数据存储的方式进行抽象，这将很难实现。

如果 Jetspeed 中的安全模型使用新的主体和/或关联进行扩展，则无需更改数据库脚本或与数据库相关的其他代码。Jetspeed 的通用存储引擎将负责存储和检索数据。尽管存储引擎在内部运行在数据库之上，但您可以从另一个数据存储同步数据。这将在下一节中讨论。

#### 3.1.3.7. **同步和复制**

安全数据可以从外部数据存储同步，并映射到 Jetspeed 内部使用的数据库。目前，LDAP 是 Jetspeed 支持的唯一外部数据存储类型。LDAP 数据可以在启动时或用户身份验证时定期同步。同步用户认证时，仅同步与该用户相关的数据。复制是指每当数据库中的安全数据更新时，将安全数据写回外部存储。同步是一种确保外部数据存储的内容与内部数据库相同的机制，其中外部数据存储具有最高优先级。LDAP 同步和复制在 LDAP 映射指南中有更详细的讨论。

#### 3.1.3.8. **证书**

#### 3.1.3.9. **权限**

### 3.1.4. [**验证**](https://portals.apache.org/jetspeed-2/devguide/atn.html)

对于身份验证，Jetspeed 2 利用 Java [LoginModule](http://java.sun.com/j2se/1.4.2/docs/api/javax/security/auth/spi/LoginModule.html) 架构。它提供了[DefaultLoginModule](https://portals.apache.org/jetspeed-2/devguide/login-module.html)实现和灵活的架构，能够针对多个用户存储库对用户进行身份验证，并提供跨这些存储库的用户管理功能。A**UserManager**提供了一组粗化的服务来验证和管理用户。下面的类图说明了如何 向 Authentication**UserManager**提供身份验证**DefaultLoginModule**并利用[Authentication SPI](https://portals.apache.org/jetspeed-2/devguide/atn-spi.html)与各种实现和用户存储进行交互。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps4.png)

上述各种组件实现以下功能：


| **零件**                        | **描述**                                                                                                                                                                                                        |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DefaultLoginModule**          | Jetspeed 2默认[LoginModule](https://portals.apache.org/jetspeed-2/devguide/login-module.html)实现，它利用 的**authenticate()**方法针对当前配置**UserManager**的各种实现提供身份验证。**AuthenticationProvider** |
| **UserManager**                 | 提供身份验证和用户管理的粗略服务。**UserManager**code >**AuthenticationProvider**利用通过**AuthenticationProviderProxy**.**SecurityProvider**                                                                   |
| **SecurityProvider**            | 提供对将SPI实现暴露给粗化安全服务的安全提供程序的访问。                                                                                                                                                         |
| **AuthenticationProviderProxy** | 各种**AuthenticationProvider**实现的代理。**AuthenticationProviderProxy** 负责调用正确的**AuthenticationProvider**方法来针对特定数据存储对特定用户进行身份验证或管理。                                          |

#### 3.1.4.1. [**登录模块**](https://portals.apache.org/jetspeed-2/devguide/login-module.html)

出于验证目的，Jetspeed 2 提供了一个默认的登录模块实现。登录模块为 Java 应用程序提供了一种公开身份验证服务的标准方法。有关登录模块的更多信息可以在 JDK [LoginModule 接口](http://java.sun.com/j2se/1.4.2/docs/api/javax/security/auth/spi/LoginModule.html) 文档中找到。

##### 3.1.4.1.1. **登录模块配置**

配置是 JAAS 身份验证的核心。默认情况下，Jetspeed 2 配置为使用其 **DefaultLoginModule** 实现。登录模块的配置文件 (login.conf) 随 **jetspeed2-security-{version}.jar** 组件一起提供并提供以下配置：

喷气式飞机{

需要 org.apache.jetspeed.security.impl.DefaultLoginModule；

};

为了覆盖此配置，您可以将自己的 login.conf 文件放置在 WEB-INF/classes 下的 Web 应用程序类路径中。login.conf 文件的位置配置 **security-providers.xml** 如下所述。有关如何配置安全提供程序的更多信息，请参阅 [配置部分](https://portals.apache.org/jetspeed-2/deployguide/security-config.html)。

<!-- 安全性：默认身份验证提供程序 -->

<bean id="org.apache.jetspeed.security.AuthenticationProvider"

  class="org.apache.jetspeed.security.impl.AuthenticationProviderImpl"
<constructor-arg index="0"><value>DefaultAuthenticator</value></constructor-arg>

<constructor-arg index="1"><value>默认验证器</value></constructor-arg>

<constructor-arg index="2"><value>login.conf</value></constructor-arg>

<constructor-arg index="3">

    <ref bean="org.apache.jetspeed.security.spi.CredentialHandler"/>

</constructor-arg>

<constructor-arg index="4">

    <ref bean="org.apache.jetspeed.security.spi.UserSecurityHandler"/>

</constructor-arg>
</豆>

通过将 System 属性设置为组件配置 中指定的属性来 **AuthenticationProvider**配置应用程序使用的 。**LoginModulejava.security.auth.login.configlogin.conf**

##### 3.1.4.1.2. **登录模块实现**

下面 **DefaultLoginModule** 的类图说明了实现：


| ![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps5.png) |
| ---------------------------------------------------------------------- |

用于实现 DefaultLoginModule 的类的角色是：


| **班级**                                                 | **描述**                                                                                                                                                                                                                                                                                                                                                             |
| -------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **org.apache.jetspeed.security.impl.DefaultLoginModule** | **javax.security.auth.spi.LoginModule** 实施 。 **DefaultLoginModule** 身份验证决策封装在接口后面，该 接口 **UserManager** 利用 SPI 实现来决定应该使用哪个身份验证器，以便根据特定的记录系统对用户进行身份验证。有关如何实现您自己的身份验证器的更多信息，请参阅 [身份验证SPI文档](https://portals.apache.org/jetspeed-2/devguide/atn-spi.html)。               |
| **org.apache.jetspeed.security.LoginModuleProxy**        | 一个实用组件，用于**UserManager** 将 **DefaultLoginModule**.                                                                                                                                                                                                                                                                                                        |
| **org.apache.jetspeed.security.User**                    | The**User** 是一个包含 the **javax.security.auth.Subject** 和 his/her 的接口**java.util.prefs.Preferences**。用户身份验证使用 **UserManager** 所有用户填充用户主题 **java.security.Principal**。Jetspeed 2实现了 3 种类型的主体：· UserPrincipal：持有应用程序的用户唯一标识符的主体。· RolePrincipal：代表系统角色的主体。· GroupPrincipal：代表系统组的主体。 |
| **org.apache.jetspeed.security.UserManager**             | 暴露所有用户操作的界面。该接口位于聚合各种SPI的前端，为开发人员提供将用户映射到其特定记录系统的能力。                                                                                                                                                                                                                                                                |

#### 3.1.4.2. [**认证 SPI**](https://portals.apache.org/jetspeed-2/devguide/atn-spi.html)

身份验证 SPI 提供用于管理用户主体及其凭据的实现，并提供底层 **UserManager** 粗化服务实现。

身份验证 SPI 还提供了一种跨多个数据存储管理用户的机制。下面的类图描述了身份验证 SPI 如何与 **UserManager** .

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps6.png)

##### 3.1.4.2.1. **认证 SPI 组件**

身份验证 SPI 实现以下组件：


| **零件**                        | **描述**                                                                                                                                                                                |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AuthenticationProviderProxy** | 各种**AuthenticationProvider** 实现的代理。**AuthenticationProviderProxy** 负责调用正确 的 **AuthenticationProvider** 方法来针对特定数据存储对特定用户进行身份验证或管理。            |
| **AuthenticationProvider**      | 公开特定的身份验证和用户管理服务实现。Jetspeed 2提供了 2 种实现：RDBMS 和 LDAP。可以通过配置提供多个身份验证提供程序。有关详细信息，请参阅[安全提供程序](#security-providers_xml)配置。 |
| **CredentialHandler**           | 请参阅[security-spi-atn.xml](#security-spi-atn_xml)配置。                                                                                                                               |
| **UserSecurityHandler**         | 请参阅[security-spi-atn.xml](#security-spi-atn_xml)配置。                                                                                                                               |

#### 3.1.4.3. [**凭证管理**](https://portals.apache.org/jetspeed-2/devguide/credentials.html)

##### 3.1.4.3.1. **DefaultCredentialHandler 功能**

使用 Jetspeed[DefaultCredentialHandler](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/DefaultCredentialHandler.html)可以轻松配置密码凭证的特殊管理。通过提供的 [PasswordCredentialProvider](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/PasswordCredentialProvider.html)和 [InternalPasswordCredentialInterceptor](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/InternalPasswordCredentialInterceptor.html)组件自定义逻辑可以插入：

· 提供自定义 [PasswordCredential](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/PasswordCredential.html)实现

· 密码编码

· 如果 [CredentialPasswordEncoder](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/CredentialPasswordEncoder.html)可以从 **PasswordCredentialProvider**密码中获得一个，则在它们被持久化之前将对其进行编码。提供 的密码加密[MessageDigestCredentialPasswordEncoder](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/MessageDigestCredentialPasswordEncoder.html)使用 [MessageDigest](http://java.sun.com/j2se/1.4.2/docs/api/java/security/MessageDigest.html)哈希算法，例如可以配置为使用**SHA-1**和**Base64**。

· 强制执行密码值规则

· 如果 [CredentialPasswordValidator](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/CredentialPasswordValidator.html)可从 中获取 **PasswordCredentialProvider**密码，则将在保留密码之前对其进行验证。例如 [DefaultCredentialPasswordValidator](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/DefaultCredentialPasswordValidator.html)强制执行非空密码。并且 [SimpleCredentialPasswordValidator](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/SimpleCredentialPasswordValidator.html)可以强制执行最小长度和最小数量的数字字符。

· 拦截 [InternalCredential](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/om/InternalCredential.html)生命周期事件

· 如果**DefaultCredentialHandler**提供了 **InternalPasswordCredentialInterceptor**，它将在以下位置调用此拦截器（或任意集 [InternalPasswordCredentialInterceptorsProxy](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/InternalPasswordCredentialInterceptorsProxy.html)）：

o 从持久存储加载凭据后

o 验证用户后

o 在将新凭据保存到持久存储之前

o 在为凭证保存新密码之前

Jetspeed 已经提供了一套基本的拦截器，可以随时使用：

o [ValidatePasswordOnLoadInterceptor](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/ValidatePasswordOnLoadInterceptor.html)

o 此拦截器可用于验证（预）在持久存储中设置的密码，并在无效时强制用户进行所需的更改。它使用 的配置**CredentialPasswordValidator** ，**PasswordCredentialProvider**与更改密码时使用的相同。

o [EncodePasswordOnFirstLoadInterceptor](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/EncodePasswordOnFirstLoadInterceptor.html)

o 如果需要在持久存储中预设密码或从其他存储未编码迁移，则可以使用此拦截器。使用此拦截器，这些明文密码将在首次从数据库加载时自动编码，使用 **CredentialPasswordEncoder**from**PasswordCredentialProvider**

o [PasswordExpirationInterceptor](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/PasswordExpirationInterceptor.html)

o 此拦截器可用于强制密码的最大寿命。它管理**expiration\_date**和的**is\_expired**成员， **InternalCredential**并在对用户进行身份验证时，其（有效）密码过期时设置过期标志。然后身份验证将失败。

o 注意：Jetspeed 管道阀，**PasswordCredentialValveImpl**可用于请求甚至强制用户及时更改密码以防止密码过期（下文进一步描述）。

o [MaxPasswordAuthenticationFailuresInterceptor](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/MaxPasswordAuthenticationFailuresInterceptor.html)

o 此拦截器可用于通过强制连续尝试最大次数的无效密码来防止密码黑客攻击。达到此身份验证失败次数后，将禁用凭据。但是，在成功验证后，此计数将由**DefaultCredentialHandler**.

o [PasswordHistoryInterceptor](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/PasswordHistoryInterceptor.html)

o 此拦截器可用于针对一定数量的先前使用的密码强制使用唯一的新密码。设置新密码后，当前密码将保存在已使用密码的 FIFO 堆栈中。当用户自己更改密码时，它必须与保存的所有一次不同，否则 [PasswordAlreadyUsedException](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/PasswordAlreadyUsedException.html)会抛出a。但是通过管理界面设置新密码仍然允许设置任何密码（如果其他密码有效）。

**DefaultCredentialHandler**仅支持配置一个拦截器 。但是，使用 [InternalPasswordCredentialInterceptorsProxy](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/spi/impl/InternalPasswordCredentialInterceptorsProxy.html)，可以配置一个拦截器列表，然后依次调用这些拦截器。

Jetspeed 开箱即用，配置了几个拦截器，并且非常容易更改和扩展。有关默认配置的描述，请参阅[安全服务配置文档中的](https://portals.apache.org/jetspeed-2/deployguide/security-config.html)[security-spi-atn.xml](#security-spi-atn_xml) 部分。还提供了一个示例，如何设置拦截器以恢复 2.0-M3 版本及更早版本提供的“旧”（以及更多限制）配置。

##### 3.1.4.3.2. **凭证管理实施**

下面的类图描述了用于 **DefaultCredentialHandler** 实现的组件。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps7.png)

默认凭据实现的 OJB 映射在以下内容中进行了描述 **security\_repository.xml**：

· **InternalCredential**: 映射到 SECURITY_CREDENTIAL 表。

以下数据库架构用于存储凭据及其与主体的关联。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps8.png)

### 3.1.5. [**授权**](https://portals.apache.org/jetspeed-2/devguide/atz.html)

对于授权，Jetspeed 2使用关系数据库存储 实现自己的 [java.security.Policy来管理主体和权限之间的关联。](http://java.sun.com/j2se/1.4.2/docs/api/java/security/Policy.html)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps9.png)

**PermissionManager**提供对与给定主体关联的权限 的访问。

· [JAAS 授权](https://portals.apache.org/jetspeed-2/devguide/atz-jaas.html)概述了 JAAS 的授权方面。

· [PermissionManager 概述](https://portals.apache.org/jetspeed-2/devguide/permission.html)记录了**PermissionManager**实现。

#### 3.1.5.1. [**JAAS 授权**](https://portals.apache.org/jetspeed-2/devguide/atz-jaas.html)

[Sun 的网站上](http://java.sun.com/j2se/1.4.2/docs/guide/security/spec/security-spec.doc2.html) 提供了一个很好的 JAAS 授权概述 。在高层次上，JAAS 授权利用：

· [将操作与资源相关联的权限](http://java.sun.com/j2se/1.4.2/docs/api/java/security/Permission.html) 。

· 代表系统中实体的主体[。](http://java.sun.com/j2se/1.4.2/docs/api/java/security/Principal.html)在 Jetspeed 2 中，使用 3 个主体来表示用户、角色和组。

· [将主体与权限相关联的策略](http://java.sun.com/j2se/1.4.2/docs/api/java/security/Policy.html) 。

Jetspeed 2 提供了一个自定义策略实现，允许门户保护资源，如下所示：

授予主体 oajsecurity.UserPrincipal "theUserPrincipal" {

权限 oajsecurity.PagePermission "mypage", "view";

权限 oajsecurity.PortletPermission "myportlet", "查看、编辑、最小化、最大化";

权限 oajsecurity.TabPermission "mytab", "view";

};

授予委托人 oajsecurity.RolePrincipal "theRolePrincipal" {

权限 oajsecurity.PagePermission "mypage", "view";

权限 oajsecurity.PortletPermission "myportlet", "查看、编辑、最小化、最大化";

权限 oajsecurity.TabPermission "mytab", "view";

};   

授予主体 oajsecurity.GroupPrincipal "theGroupPrincipal" {

权限 oajsecurity.PagePermission "mypage", "view";

权限 oajsecurity.PortletPermission "myportlet", "查看、编辑、最小化、最大化";

权限 oajsecurity.TabPermission "mytab", "view";

};

自定义安全策略提供了一种 **java.security.Policy** 实现，该实现将主体和权限之间的关联存储在关系数据库中，而不是利用默认的 JDK 策略。对于 Sun 的 JDK，默认策略是 [sun.security.provider.PolicyFile](#DefaultImpl) 一个基于文件的策略。

在上面的代码示例中， **UserPrincipal** 具有“theUserPrincipal”的标识 **Principal.getName()** 有权“查看”名为“mypage”的页面，“查看、编辑、最小化、最大化”名为“myportlet”的 portlet portlet

[AccessController](http://java.sun.com/j2se/1.4.2/docs/api/java/security/AccessController.html) 验证 **Subject** 权限 。 例如，页面权限检查将执行以下检查：

PagePermission 权限 = new PagePermission(path, actions);

AccessController.checkPermission(权限);                

##### 3.1.5.1.1. **Jetspeed JAAS 政策**

**RdbmsPolicy** 工具 **java.security.Policy** 。 _ 它利用 **PermissionManager** 获取与给定 **Subject** 主体关联的权限。

pms.getPermissions(user.getPrincipals());

下面的类图说明了 **RdbmsPolicy** 和 之间的关联**PermissionManager** 。

[IBM 网站上](http://www-106.ibm.com/developerworks/library/j-jaas/?n-j-442) 提供了一篇关于自定义策略实施的好文章 。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps10.png)

要获得有关实现的更多详细信息 **PermissionManager** ，请参阅 [PermissionManager 概述](https://portals.apache.org/jetspeed-2/devguide/permission.html) 。

注意： 当前 **RdbmsPolicy** 管理要应用的策略。它 **RdbmsPolicy** 与运行时环境中配置的默认策略一起应用。Jetspeed 2 应该探索为特定应用服务器的自定义策略提供 [JACC](http://java.sun.com/j2ee/javaacc/index.html) 适配器。

##### 3.1.5.1.2. **授权提供者和策略配置**

配置 Jetspeed 2 使用的 **AuthorizationProvider** 授权策略，并将此类策略列表保存在 **SecurityPolicies** 单例中。当 **RdbmsPolicy** 获得访问控制的权限时，将执行其策略以及在 中配置的所有策略 **SecurityPolicies** 。如果 **AuthorizationProvider** 设置 **useDefaultPolicy** 为 true，则在获取权限时将应用默认的 JDK 或应用程序服务器策略。

注意： 权限 **RbmsPolicy** 检查涉及与 关联的主体 **Subject**，因此在执行访问控制检查时，应使用以下调用执行检查： **doAsPrivileged(theSubject, anAction, null)**。通过传递一个 null **AccessContolContext**，调用者本质上是在说：“我不在乎是谁给我打电话，唯一重要的是当我与给定的主题相关联时是否有权限”。

#### 3.1.5.2. [**权限管理器概述**](https://portals.apache.org/jetspeed-2/devguide/permission.html)

**PermissionManager**用于**RdbmsPolicy**获取给定用户主体的权限，如文档的Jetspeed [JAAS 策略](#Jetspeed_JAAS_Policy)部分中所述。

**PermissionManager**管理权限和主体之间的关联 。每个权限或主体映射到一个通用对象模型，并且反射用于实例化正确的权限或主体类型。下面的类图表示表示通用权限 ( **InternalPermission**) 和通用主体 ( **InternalPrincipal**) 的接口以及它们与**PermissionManager**.

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps11.png)

每个**InternalPermission**映射到一个或多个**InternalPrincipal**，并且每个都 **InternalPrincipal**可以有一个或多个**InternalPermission**。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps12.png)

**模式和 OJB 映射**

安全组件的 OJB 映射在以下内容中进行了描述**security\_repository.xml**：

· **InternalPrincipal**: 映射到**SECURITY\_PRINCIPAL**表格。

· **InternalPermission**: 映射到**SECURITY\_PERMISSION**表格。

· **InternalPrincipal**和之间的关联**InternalPermission**是通过间接表维护的**PRINCIPAL\_PERMISSION**。

<类描述符

    class="org.apache.jetspeed.security.om.impl.InternalPrincipalImpl"

    代理=“动态”

    表="SECURITY_PRINCIPAL"

>...</class-descriptor>
<类描述符

    class="org.apache.jetspeed.security.om.impl.InternalPermissionImpl"

    代理=“动态”

    表="SECURITY_PERMISSION"

>...</class-descriptor>      
下面提供了维护权限关联主体的关系模式：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps13.png)

#### 3.1.5.3. [**授权/安全映射 SPI**](https://portals.apache.org/jetspeed-2/devguide/atz-spi.html)

授权 SPI 提供支持 Jetspeed 2 用户、角色和组关联以及角色/组层次结构策略的实现。它提供了底层机制来支持 和 的 **RoleManager** 实现 **GroupManager** 。

如 [安全概述](https://portals.apache.org/jetspeed-2/devguide/index.html)中所述 ，Jetspeed 通过可配置的层次策略支持基于层次角色的访问控制。

首先我们来看一个授权SPI的类图：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps14.png)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps15.png)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps16.png)

**授权 SPI 组件**

授权 SPI 实现以下组件：


| **零件**                                                | **描述**                                                                          |
| ------------------------------------------------------- | --------------------------------------------------------------------------------- |
| org.apache.jetspeed.security.spi.SecurityMappingHandler | 请参阅[security-spi-atz.xml](#security-spi-atz_xml)配置。                         |
| org.apache.jetspeed.security.HierarchyResolver          | 请参阅[层次管理](https://portals.apache.org/jetspeed-2/devguide/hierarchy.html)。 |
| org.apache.jetspeed.security.spi.RoleSecurityHandler    | 请参阅[security-spi-atz.xml](#security-spi-atz_xml)配置。                         |
| org.apache.jetspeed.security.spi.GroupSecurityHandler   | 请参阅[security-spi-atz.xml](#security-spi-atz_xml)配置。                         |

#### 3.1.5.4. [**层次管理**](https://portals.apache.org/jetspeed-2/devguide/hierarchy.html)

授权决策支持两种层次结构解析策略：

· 泛化的层次结构分辨率：这是 Jetspeed 中的默认层次结构分辨率。如果层次结构使用泛化策略，则每个角色都比前一个角色更通用。例如，如果用户具有角色 [roleA.roleB.roleC]，则 **user.getSubject().getPrincipals()** 返回：

o /角色/角色A

o /角色/角色A/角色B

o /角色/角色A/角色B/角色C

· 通过聚合解决层次结构：如果层次结构使用聚合策略，则较高角色负责较低角色的活动的超集。例如，如果以下角色可用：

o 角色A

o 角色A.角色B

o 角色A.角色B.角色C

如果用户具有角色 [roleA]，则 **user.getSubject().getPrincipals()** 返回：

o /角色/角色A

o /角色/角色A/角色B

o /角色/角色A/角色B/角色C

如 [授权** SPI **部分](https://portals.apache.org/jetspeed-2/devguide/atz-spi.html) 所述， **SecurityMappingHandler** 为组和角色层次结构管理配置了特定的层次结构策略。有关配置示例，请参阅 [授权** SPI **配置](#security-spi-atz_xml) 。

**利用首选项来管理层次结构**

默认层次管理实现通过利用 Jetspeed 2 的 [java.util.prefs.Preferences](http://java.sun.com/j2se/1.4.2/docs/api/java/util/prefs/Preferences.html) 实现来解决层次策略。该 **Preferences** 实现提供了 Jetspeed 中的底层结构来存储用户属性、角色和组定义。该 **Preferences** 模型提供了一个层次模型，用于存储可以应用各种解析策略（通过泛化或聚合的解析）的基本角色和组层次结构。

有关详细信息，请参阅 Jetspeed 2 [首选项实施部分](https://portals.apache.org/jetspeed-2/devguide/dev-prefs.html) 。

**这是如何运作的？**

该 **SecurityMappingHandler** 实现解决了角色和组之间的映射。假设我们想要找出映射到特定组名的角色。为此， **SecurityMappingHandler** 实现了一个 **getRolePrincipalsInGroup(String groupFullPathName)** 方法。在此方法中，组名映射到特定 **Preferences** 节点。根据给定的层次结构解析策略（参见 [概述部分](#Hierarchy_Management_Overview) ），在 [组 A] 中可能意味着属于一组组；HierarchyResolver 用于执行此操作，如下所示：

公共设置 getRolePrincipalsInGroup(String groupFullPathName)

{

...

首选项首选项 = Preferences.userRoot().node(

   GroupPrincipalImpl.getFullPathFromPrincipalName(groupFullPathName));
String[] fullPaths = groupHierarchyResolver.resolve(preferences);

...

}

然后使用生成的组来查找所有关联的角色。

作为此实现的结果，安全层中角色主体的名称 ( **Principal**[getName()](#getName()) ) 应与首选项层中该用户首选项根的完整路径匹配 ( **Preference**[absolutePath()](#absolutePath())；例如：) **/role/theRolePrincipal** 。

组和角色层次结构存储在 **Preferences** 层中，如下所示（ [Jetspeed 的 RBMS Preferences实现的](https://portals.apache.org/jetspeed-2/devguide/dev-prefs.html)[ exportNode()](#exportNode(java.io.OutputStream))的输出）：

<首选项EXTERNAL_XML_VERSION="1.0">

<root type="用户">

<地图/>

<节点名称="组1">

<地图/>

    <节点名称="groupid1.1">

    <地图/>

    <节点名称="groupid1.1.1">

        <地图/>

        </节点>

    </节点>

</节点>

<节点名称="角色1">

<地图/>

    <节点名称="roleid1.1">

    <地图/>

    <节点名称="roleid1.1.1">

        <地图/>

        </节点>

    </节点>

</节点>
</root>

此结构将定义以下组和角色层次结构：

· **/group1/groupid1.1/groupid1.1.1**

· **/role1/roleid1.1/roleid1.1.1**

此外，在此模型中， **map** 元素可以定义组或角色自定义属性。例如，角色可以具有规则自定义属性（或指向规则的指针），允许基于规则的角色定义绑定到某些规则引擎（例如 Drools），并在调用 isInRole 方法时进行验证。对于组，门户可以使用组来描述组织并具有与组织/组关联的地址、城市等自定义属性。

### 3.1.6. [**高级安全服务**](https://portals.apache.org/jetspeed-2/devguide/high-level-services.html)

Jetspeed 2 提供以下四种高级安全服务：

· **UserManager** ：提供用户管理能力的服务。

· **GroupManager** ：提供组管理能力的服务。

· **RoleManager** ：提供角色管理能力的服务。

· **PermissionManager** ：提供权限管理能力的服务。

**在 Portlet 中使用高级安全服务**

为了在您的 portlet 中访问 Jetspeed 高级安全服务，Jetspeed 为**portlet.xml**元数据提供了一个自定义扩展。所有 Jetspeed 自定义元数据都位于 portlet 应用程序文件夹中的**jetspeed-portlet.xml**配置文件中。**WEB-INF**自定义**js:services**标记提供了通过**javax.portlet.PortletContext**.

Jetspeed 门户服务在位于门户 **WEB-INF/assembly/jetspeed-services**配置文件中的 spring 程序集文件中进行配置。以 UserManager 为例，配置如下：

<!-- Portlet 服务 -->

<bean id="门户服务"

 类="org.apache.jetspeed.services.JetspeedPortletServices" >
<构造函数参数>

  <地图>

     ...

     <entry key="用户管理器">

   	    <ref bean="org.apache.jetspeed.security.UserManager"/>

   	 </entry>

   	 ...

  </地图>
</constructor-arg>

</豆>

然后可以将这些**UserManager**服务加载到特定的 portlet **PortletContext**中。Portlet 开发人员需要指定他们想要使用的门户服务。以下示例显示如何将门户公开**UserManager** 给 portlet 应用程序：

<js:服务>

<js:service name='UserManager'/>

[/js:服务](/js:%E6%9C%8D%E5%8A%A1)

在 portlet 上下文中加载门户服务后，portlet 实现（通常为 extends **javax.portlet.GenericPortlet**）可以访问该服务，如下所示：

PortletContext 上下文 = getPortletContext();

userManager = (UserManager) context.getAttribute(CommonPortletServices.CPS_USER_MANAGER_COMPONENT);

在哪里**CommonPortletServices.CPS\_USER\_MANAGER\_COMPONENT = "cps:UserManager"**

### 3.1.7. [**安全服务配置**](https://portals.apache.org/jetspeed-2/deployguide/security-config.html)

本指南的这一部分为部署人员提供了几个 Jetspeed Security 的快速部署配置选项。

#### 3.1.7.1. **授权：权限与约束**

Jetspeed 支持两种不同的授权策略：

1. 权限 - 使用标准的 Java 安全策略。Jetspeed 将此策略存储在关系数据库中
2. 约束 - Jetspeed 特定的基于约束的安全性

默认情况下，Jetspeed 使用 Spring 配置文件中安全访问控制器 bean 的服务配置中所示的约束**administration.xml**。约束通常在 Jetspeed 站点中的资源本身上定义，例如在页面或文件夹上。请参阅[约束指南](https://portals.apache.org/jetspeed-2/deployguide/guide-security-declarative-psml.html)以及有关基于约束的安全性的更多信息。

Java 安全策略更高级一些。有关在关系数据库中配置 Jetspeed 的 JAAS 安全策略的更多信息，请参阅[JAAS 安全策略指南](https://portals.apache.org/jetspeed-2/devguide/atz-jaas.html)

<bean id="org.apache.jetspeed.security.SecurityAccessController"

  类='org.apache.jetspeed.security.impl.SecurityAccessControllerImpl'>

	<构造函数参数索引='0'>

		<ref bean="org.apache.jetspeed.page.PageManager"/>

	</constructor-arg>

	<!--

	   安全模式：

	      1 = 权限 = 使用 Jetspeed Java 安全策略

	      2 = 约束 = 使用 Jetspeed (PageManager) 基于约束的安全性  

	 -->

	 <constructor-arg index="1">

        <值>2</值>

    </constructor-arg>
</豆>

#### 3.1.7.2. **登录和授权选项**

Jetspeed 提供了一些通用的登录和授权选项来帮助您自定义门户的行为。下面显示的 Portal Authentication Configuration bean 的服务配置，来自 Spring 配置文件**administration.xml**，用于自定义门户的两个关键行为。

1. 登录时创建新会话 - 默认情况下，当用户使用 Jetspeed 登录 portlet 之一进行身份验证（登录）时，不会创建新会话。来宾用户的会话被传递给经过身份验证的用户。如果要更改此行为以创建新会话，请将此值设置为 true。此设置为假的原因是模拟一个在线商店，您在其中购买东西然后最后登录。
2. 硬会话超时 - 对于需要以秒为单位设置硬会话超时限制的配置，无论（在）活动如何。设置为 0 会关闭此功能。注意：此功能应与“身份验证时创建新会话”功能一起使用

<bean id='org.apache.jetspeed.administration.PortalAuthenticationConfiguration'

类='org.apache.jetspeed.administration.PortalAuthenticationConfigurationImpl'>
<!-- 认证时创建新会话-->

<构造函数参数索引='0'>

	<值>假</值>
</constructor-arg>

<!-- 以秒为单位的硬会话超时限制，无论（不）活动如何，设置为 0 将关闭此功能

   		 注意：此功能应与“身份验证时创建新会话”功能一起使用

   -->

<构造函数参数索引='1'>

	<值>0</值>
</constructor-arg>

<!-- 硬会话过期的重定向位置 -->

<构造函数参数索引='2'>

	<value>/登录/注销</value>
</constructor-arg>

</豆>    

#### 3.1.7.3. **Jetspeed 安全弹簧配置**

配置 Jetspeed 安全性时涉及的文件位于 *\${jetspeed-source-home}/portal/src/webapp/WEB-INF/assembly/*下。本节向您介绍这些部署描述符文件。在正常使用中，您不需要修改这些文件。本文档用于 Jetpeed 安全性的高级使用，例如用您自己的替换默认的安全性实现。

##### 3.1.7.3.1. **安全-atn.xml**

该配置文件提供登录模块配置。不是每个人都需要这个，因为某些应用程序可能决定使用提供的登录模块以外的另一个登录模块。

##### 3.1.7.3.2. **安全-atz.xml**

这个配置文件配置了授权策略，在 J2 的例子中是 [RdbmsPolicy](https://portals.apache.org/jetspeed-2/devguide/atz-jaas.html) 。

##### 3.1.7.3.3. **安全管理器.xml**

出于安全目的，此配置文件配置所有管理器。

##### 3.1.7.3.4. **安全提供者.xml**

此配置文件配置各种提供程序并将 SPI 编织在一起。

· **AuthenticationProviderProxy** ：配置列表 **AuthenticationProvider** 和默认验证器。

<bean id="org.apache.jetspeed.security.AuthenticationProviderProxy"

class="org.apache.jetspeed.security.impl.AuthenticationProviderProxyImpl">  

<构造函数参数>

  <列表>

     <ref bean="org.apache.jetspeed.security.AuthenticationProvider"/>

  </列表>
</constructor-arg>

<constructor-arg><value>DefaultAuthenticator</value></constructor-arg>

</豆>

·

· **AuthenticationProvider** ：为当前门户实现配置身份验证提供程序。下面的示例配置使用 RDBMS 管理/存储用户信息的默认身份验证器。

<bean id="org.apache.jetspeed.security.AuthenticationProvider"

   class="org.apache.jetspeed.security.impl.AuthenticationProviderImpl">  	   
<constructor-arg index="0"><value>DefaultAuthenticator</value></constructor-arg>

<constructor-arg index="1"><value>默认验证器</value></constructor-arg>

<constructor-arg index="2"><value>login.conf</value></constructor-arg>

<constructor-arg index="3">

  <ref bean="org.apache.jetspeed.security.spi.CredentialHandler"/>
</constructor-arg>

<constructor-arg index="4">

  <ref bean="org.apache.jetspeed.security.spi.UserSecurityHandler"/>
</constructor-arg>

</豆>

·

· **AuthorizationProvider** ：配置策略并实例化 **SecurityPolicies** 用于强制执行权限的策略。默认情况下，Jetspeed 2 不加载任何其他可能已配置的安全策略。为了使用默认策略，设置 **useDefaultPolicy**为**true**

<bean id="org.apache.jetspeed.security.AuthorizationProvider"

  class="org.apache.jetspeed.security.impl.AuthorizationProviderImpl">  	   

<constructor-arg index="0">

    <ref bean="org.apache.jetspeed.security.impl.RdbmsPolicy"/>

</constructor-arg>

<!-- 不使用默认策略作为默认行为 -->

<constructor-arg index="1"><value>false</value></constructor-arg>   
</豆>

·

##### 3.1.7.3.5. **安全-spi.xml**

此配置文件包含身份验证和授权 SPI 通用的配置。


| **豆**                                          | **描述**                                                                                                                                         |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| org.apache.jetspeed.security.spi.SecurityAccess | 由默认的基于OJB的 SPI 在内部使用。提供对各种 SPI 实现的通用操作/方法的访问。 Authentication 和 Authorization SPI 都使用 SecurityAccess*bean。* |

##### 3.1.7.3.6. **安全-spi-atn.xml**

此配置文件包含配置身份验证 SPI 的所有配置。


| **豆**                                               | **描述**                                                                                                                                                                                                                                                                                                  |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| org.apache.jetspeed.security.spi.CredentialHandler   | *CredentialHandler* 封装了涉及凭据操作的操作 。 *默认实现为PasswordCredentialProvider定义的密码*保护提供支持 ；以及通过 *InternalPasswordCredentialInterceptor对凭证进行生命周期管理* 它可以配置为管理参数，例如最大身份验证失败次数、凭证的最长生命周期（以天为单位）以及为给定凭证保留多少历史记录。 |
| org.apache.jetspeed.security.spi.UserSecurityHandler | *UserSecurityHandler* 封装了围绕用户主体的所有操作 。                                                                                                                                                                                                                                                    |

**CredentialHandler**Jetspeed 目前默认提供 以下简单配置：

<!-- 需要一个非空密码 -->

<bean id="org.apache.jetspeed.security.spi.CredentialPasswordValidator"

 class="org.apache.jetspeed.security.spi.impl.DefaultCredentialPasswordValidator"/>
<!-- MessageDigest 使用 SHA-1 编码密码 -->

<bean id="org.apache.jetspeed.security.spi.CredentialPasswordEncoder"

 class="org.apache.jetspeed.security.spi.impl.MessageDigestCredentialPasswordEncoder">

 <constructor-arg index="0"><value>SHA-1</value></constructor-arg>       
</豆>       

<!-- 允许多个 InternalPasswordCredentialInterceptor 用于 DefaultCredentialHandler -->

<bean id="org.apache.jetspeed.security.spi.InternalPasswordCredentialInterceptor"

 class="org.apache.jetspeed.security.spi.impl.InternalPasswordCredentialInterceptorsProxy">

 <constructor-arg index="0">

   <列表>

     <!-- 强制要求更改持久存储中的无效预设密码值 -->

     <bean class="org.apache.jetspeed.security.spi.impl.ValidatePasswordOnLoadInterceptor"/>

     <!-- 确保持久存储中的预设明文密码将在首次使用时进行编码-->

     <bean class="org.apache.jetspeed.security.spi.impl.EncodePasswordOnFirstLoadInterceptor"/>

   </列表>

 </constructor-arg>
</豆>

<bean id="org.apache.jetspeed.security.spi.PasswordCredentialProvider"

 class="org.apache.jetspeed.security.spi.impl.DefaultPasswordCredentialProvider">

 <constructor-arg index="0">

   <ref bean="org.apache.jetspeed.security.spi.CredentialPasswordValidator"/>

 </constructor-arg>       

 <constructor-arg index="1">

   <ref bean="org.apache.jetspeed.security.spi.CredentialPasswordEncoder"/>

 </constructor-arg>       
</豆>       

<bean id="org.apache.jetspeed.security.spi.CredentialHandler"

 class="org.apache.jetspeed.security.spi.impl.DefaultCredentialHandler">       

 <constructor-arg index="0">

   <ref bean="org.apache.jetspeed.security.spi.SecurityAccess"/>

 </constructor-arg>       

 <constructor-arg index="1">

   <ref bean="org.apache.jetspeed.security.spi.PasswordCredentialProvider"/>

 </constructor-arg>       

 <constructor-arg index="2">

   <ref bean="org.apache.jetspeed.security.spi.InternalPasswordCredentialInterceptor"/>

 </constructor-arg>
</豆>

上面的配置要求密码不能为空，MessageDigest 使用 SHA-1 对其进行编码。

并且，确保在 pipelines.xml 中为安全相关的阀门设置了类似以下的配置：

<bean id="passwordCredentialValve"

  class="org.apache.jetspeed.security.impl.PasswordCredentialValveImpl"

  初始化方法="初始化">
<构造函数参数>

<!-- expirationWarningDays -->

<列表>

 <值>2</值>

 <值>3</值>

 <值>7</值>
</列表>

</constructor-arg>

</豆>

<bean id="loginValidationValve"

  class="org.apache.jetspeed.security.impl.LoginValidationValveImpl"

  初始化方法="初始化">
<!-- maxNumberOfAuthenticationFailures

       此值应与值同步

       org.apache.jetspeed.security.spi.impl.MaxPasswordAuthenticationFailuresInterceptor

       （如果使用）有意义。

       任何值 < 2 将抑制 LoginConststants.ERROR_FINAL_LOGIN_ATTEMPT

       在凭证之前只能进行最后一次尝试时的错误代码

       将在下一次身份验证失败后禁用。

  -->

<constructor-arg index="0"><value>3</value></constructor-arg>  

</豆>

另外，确保在**jetspeed-pipeline**bean 中配置了上述阀门。

有关这些阀门的描述及其与拦截器配置的关系， 请参阅[凭证管理文档。](https://portals.apache.org/jetspeed-2/deployguide/credentials.html)

##### 3.1.7.3.7. **安全-spi-atz.xml**

该配置文件包含配置授权 SPI 的所有配置。


| **豆**                                                  | **描述**                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| org.apache.jetspeed.security.spi.RoleSecurityHandler    | *RoleSecurityHandler* 封装了围绕角色主体的所有操作 。                                                                                                                                                                                                                                                       |
| org.apache.jetspeed.security.spi.GroupSecurityHandler   | *GroupSecurityHandler* 封装了围绕组主体的所有操作 。                                                                                                                                                                                                                                                        |
| org.apache.jetspeed.security.spi.SecurityMappingHandler | *SecurityMappingHandler* 封装了所有涉及主体之间映射的操作 。 它包含管理分层主体（角色或组）的层次结构解析的逻辑。提供的默认层次结构解析是按泛化的层次结构（请参阅定义概述）。可以将 *contructor-arg* 添加到 *SecurityMappingHandler* 以更改层次结构解析策略。Jetspeed 2 还支持通过聚合进行层次结构解析。 |

示例 **SecurityMappingHandler** 配置可能是：

<!-- 安全 SPI: SecurityMappingHandler -->

<bean id="org.apache.jetspeed.security.spi.SecurityMappingHandler"

  class="org.apache.jetspeed.security.spi.impl.DefaultSecurityMappingHandler">  	   
<构造函数参数>

  <ref bean="org.apache.jetspeed.security.spi.SecurityAccess"/>
</constructor-arg>

<!-- 默认角色层级策略是泛化。  

        添加constructor-arg来改变策略。-->

<!-- 默认组层次结构策略是泛化。  

        添加constructor-arg来改变策略。-->

</豆>

### 3.1.8. **证书**

尽管**DefaultCredentialHandler**提供了对凭据的细粒度管理，但它无法向用户提供直接反馈，例如显示当前密码即将过期的警告。但是，配备 jetspeed 的特殊要求处理管道阀可以做到这一点。

这些阀门的配置可以在**pipelines.xml**弹簧配置文件中找到并设置。

**LoginValidationValveImpl**

[LoginValidationValveImpl](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/impl/LoginValidationValveImpl.html)向用户提供有关登录尝试失败的原因的反馈 。

它检索指定用户名的**UserPrincipal**及其当前**PasswordCredential**，并（如果找到）根据其状态确定特定的错误代码。此错误代码通过会话传回，因此可以向用户呈现适当的错误消息。

可以返回以下可能的错误代码（均在 [LoginConstants](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/login/LoginConstants.html)接口中定义）：

1. ERROR\_UNKNOWN\_USER
2. ERROR\_INVALID\_PASSWORD
3. ERROR\_USER\_DISABLED
4. ERROR\_FINAL\_LOGIN\_ATTEMPT
5. ERROR\_CREDENTIAL\_DISABLED
6. ERROR\_CREDENTIAL\_EXPIRED

在上述错误代码中，只有在阀门配置为与上述相关的相同值**ERROR\_FINAL\_LOGIN\_ATTEMPT**时才会报告：**maxNumberOfAuthenticationFailuresMaxPasswordAuthenticationFailuresInterceptor**

<bean id="loginValidationValve"

    class="org.apache.jetspeed.security.impl.LoginValidationValveImpl"

    初始化方法="初始化">

<!-- maxNumberOfAuthenticationFailures

     此值应与值同步

     org.apache.jetspeed.security.spi.impl.MaxPasswordAuthenticationFailuresInterceptor

     （如果使用）有意义。

     任何值 < 2 将抑制 LoginConststants.ERROR_FINAL_LOGIN_ATTEMPT

     在凭证之前只能进行最后一次尝试时的错误代码

     将在下一次身份验证失败后禁用。

-->

<constructor-arg index="0"><value>3</value></constructor-arg>

<constructor-arg index="1">

  <列表>

    <value>org.apache.jetspeed.powertool.actions</value>

  </列表>

</constructor-arg>
</豆>

除了启用登录验证阀外，请确保将 MaxPasswordAuthenticationFailuresInterceptor 添加到凭据策略管理器并确保登录尝试值同步。开箱即用，未配置 MaxPasswordAuthenticationFailuresInterceptor。

<bean id="org.apache.jetspeed.security.spi.impl.UserPasswordCredentialPolicyManagerImpl"

class="org.apache.jetspeed.security.spi.impl.UserPasswordCredentialPolicyManagerImpl">

<meta key="j2:cat" value="默认或安全" />

<constructor-arg index="0" ref="org.apache.jetspeed.security.CredentialPasswordEncoder" />

<constructor-arg index="1" ref="org.apache.jetspeed.security.CredentialPasswordValidator" />

<constructor-arg index="2">

  <列表>

    <!-- 强制要求更改持久存储中的无效预设密码值 -->

    <bean class="org.apache.jetspeed.security.spi.impl.ValidatePasswordOnLoadInterceptor" />

    <!-- 确保持久存储中的预设明文密码将在首次使用时进行编码-->

    <bean class="org.apache.jetspeed.security.spi.impl.EncodePasswordOnFirstLoadInterceptor" />

    <bean class="org.apache.jetspeed.security.spi.impl.MaxPasswordAuthenticationFailuresInterceptor">

         <constructor-arg index="0"><value>3</value></constructor-arg>

    </豆>

    <!-- 密码过期拦截器。启用密码过期时需要。本例设置为 30 天 -->

    <bean class="org.apache.jetspeed.security.spi.impl.PasswordExpirationInterceptor">

                <constructor-arg index="0"><value>30</value></constructor-arg>

            </豆>

  </列表>

</constructor-arg>
</豆>

**PasswordCredentialValveImpl**

它[PasswordCredentialValveImpl](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/impl/PasswordCredentialValveImpl.html)旨在与特殊门户页面 (PSML) 上的特殊 Portlet 一起使用，以自动请求甚至要求用户更改其密码。

此阀门评估**PasswordCredential.isUpdateRequired()**和可选的 **expirationDate**,**lastAuthenticationDate**和**previousAuthenticationDate** 字段以确定是否需要用户或仅要求用户更改其密码。

这个阀门可以选择 **expirationWarningDays**在其构造函数中配置一个数字列表：

<bean id="passwordCredentialValve"

  class="org.apache.jetspeed.security.impl.PasswordCredentialValveImpl"

  初始化方法="初始化">
<构造函数参数>

<!-- expirationWarningDays -->

<列表>

 <值>2</值>

 <值>3</值>

 <值>7</值>
</列表>

</constructor-arg>

</豆>

这些数字中的每一个都代表当前密码凭证的前一天，**expirationDate**当用户应该被警告其密码即将到期并被要求更改它时。和 **lastAuthenticationDate**用于**previousAuthenticationDate**确定何时应该发生这种情况。对于每个配置的**expirationWarningDay**. 如果用户使用上述示例配置首次登录（几天后），在密码过期前 6 天，他或她将收到警告。再过 3 或 2 天。

当用户在密码到期前的最后一天或何时登录**updateRequired** 时**true**，无论是否配置了 expireWarningDays，都将要求用户更改密码。

为了能够自动向用户提供此信息并允许或要求在登录后直接更改密码，使用了特殊**ProfileLocator**[SECURITY\_LOCATOR](#SECURITY_LOCATOR)功能。然后**PageProfilerValve**（应该 在管道中的这个阀门之后配置）将使用这个强制定位器来查找相关的门户页面以呈现给用户。

为此，**"security"**必须像 Jetspeed 提供的默认规则一样设置 Profiler 规则：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps17.png)

从上图中可以看出，将呈现给用户的默认页面 **/my-account.psml**位于根目录中。

此默认页面仅包含一个 portlet，即**ChangePasswordPortlet**来自安全 Portlet 应用程序的 portlet。

与as 它**ChangePasswordPortlet**一起**PasswordCredentialValveImpl** 检查 [PASSWORD\_CREDENTIAL\_DAYS\_VALID\_REQUEST\_ATTR\_KEY](#PASSWORD_CREDENTIAL_DAYS_VALID_REQUEST_ATTR_KEY)请求参数，该参数将由该阀门设置，密码仍然有效的天数。对于所需的密码更改，这将设置为 Integer(0)。

默认**my-account.psml**页面仅包含**ChangePasswordPortlet** 以确保需要更改密码的用户在更改密码后不能以任何其他方式与门户网站交互。

尽管用户可能会尝试选择指向不同页面的链接（例如，从门户菜单中），但如果需要，此阀门将确保仅返回配置的“安全”定位器页面。但是，一旦更改密码，URL 中的目标页面将自动导航到。

### 3.1.9. [**LDAP 配置**](https://portals.apache.org/jetspeed-2/deployguide/ldap.html)

Jetspeed 支持多个 LDAP 服务器：

· [阿帕奇** DS**](http://directory.apache.org/)

· [打开** LDAP**](http://www.openldap.org/)

· [骨牌](http://www-306.ibm.com/software/lotus/)

· [孙德](http://www.sun.com/software/products/directory_srvr_ee/dir_srvr/index.xml)

本入门部分仅涵盖 Apache DS 入门

#### 3.1.9.1. **阿帕奇 DS 1.0.2**

开始使用 Apache DS 的第一步是下载并安装它。一旦启动并运行，您需要将 Jetspeed LDAP 模式添加到 Apache DS 服务器配置。对于 ApacheDS 1.0.2 版本，此处记录了添加自定义模式的一般说明。但是，从 2.2.0 开始，Jetspeed 预构建仅适用于 0.9.3 版本。从 Jetspeed 2.2.0 开始，我们建议使用此处描述的 1.0.2 版指南而不是 Jetspeed 版本，因为我们已弃用 Jetspeed 2.2 版的所有 0.9.3 支持。

[http://directory.apache.org/apacheds/1.0/custom-schema.html](http://directory.apache.org/apacheds/1.0/custom-schema.html)

Apache DS 1.0 不支持通过 LDAP 协议进行动态模式更新。将来会添加此功能，但您仍然可以更改 Apache DS 使用的模式。它只需要重新启动。*要在 Apache DS 中包含其他模式，只需将模式定义添加到 Apache DS 发行版中/conf*目录下的 Apache DS server.xml 配置文件。找到名为“bootstrapSchemas”的属性配置。由于我们对添加 Jetspeed 模式特别感兴趣，因此我们想添加一个适合 Jetspeed 的 bean 定义。这看起来像：

<property name="bootstrapSchemas">

  <设置>

    <bean class="org.apache.directory.server.core.schema.bootstrap.AutofsSchema"/>

    <bean class="org.apache.directory.server.core.schema.bootstrap.CorbaSchema"/>

...

<bean class="org.apache.jetspeed.security.ldap.JetspeedSchema"/>	

  </set>
</属性>

对于 Apache LDAP 0.9.3 版本（我从未尝试过），使用相同的：

<bean class="org.apache.jetspeed.security.ldap.JetspeedSchema"/>
我们只是在 bean 定义列表的末尾添加了 Jetspeed 模式定义。bean 引用了一个名为*org.apache.jetspeed.security.ldap.JetspeedSchema*的类。此类包含在 Jetspeed 为您提供的 JAR 文件中，见下文。

接下来，我们需要为 jetspeed 模式创建一个名为**SevenSeas**的新域。以下步骤将在 Apache DS 中创建 SevenSeas 域。

要添加后缀为**"o=sevenSeas"**和 ID 为**"sevenSeasPartitionConfiguration"**的分区，请在 Apache DS 中编辑 conf/server.xml 文件。在您喜欢的编辑器中打开它，然后查找名为 contextPartitionConfigurations 的以下元素。为 SevenSeas 分区添加第二个 ref 元素：

<property name="contextPartitionConfigurations">

<设置>

<ref bean="examplePartitionConfiguration"/>

<ref bean="sevenSeasPartitionConfiguration"/>
</set>

</属性>

接下来，通过将此代码粘贴到 examplePartitionConfiguration 之后为七大洋创建实际分区（您也可以删除示例分区并根据需要引用）：

<bean id="sevenSeasPartitionConfiguration" class="org.apache.directory.server.core.partition.impl.btree.MutableBTreePartitionConfiguration">    

<!-- 优化器默认启用，但可能并不总是这样 -->

<!-- 如果你的查询真的很简单，你会想要 -->

<!--<property name="optimizerEnabled" value="true" />-->



<property name="name" value="七大洋" />

<property name="cacheSize" value="100" />

<property name="suffix" value="o=sevenSeas" />

<property name="optimizerEnabled" value="true" />

<property name="synchOnWrite" value="true" />

<!--

  写入同步不等待同步操作

  刷新脏页。写入立即持续到磁盘

  提高数据完整性的性能成本。除此以外

  周期性同步操作将使用

  主配置中的 synchPeriodMillis 参数。

-->



<property name="indexedAttributes">

  <设置>

    <bean class="org.apache.directory.server.core.partition.impl.btree.MutableIndexConfiguration">

      <property name="attributeId" value="dc" />

      <property name="cacheSize" value="100" />

    </豆>

    <bean class="org.apache.directory.server.core.partition.impl.btree.MutableIndexConfiguration">

      <property name="attributeId" value="ou" />

      <property name="cacheSize" value="100" />

    </豆>

    <bean class="org.apache.directory.server.core.partition.impl.btree.MutableIndexConfiguration">

      <property name="attributeId" value="krb5PrincipalName" />

      <property name="cacheSize" value="100" />

    </豆>

    <bean class="org.apache.directory.server.core.partition.impl.btree.MutableIndexConfiguration">

      <property name="attributeId" value="uid" />

      <property name="cacheSize" value="100" />

    </豆>

    <bean class="org.apache.directory.server.core.partition.impl.btree.MutableIndexConfiguration">

      <property name="attributeId" value="objectClass" />

      <property name="cacheSize" value="100" />

    </豆>

  </set>

</属性>

<property name="contextEntry">

  <值>

    对象类：顶部

    对象类：域

    对象类：可扩展对象

	o：七海

  </值>

</属性>
</豆>

</豆>

请注意，如果您需要自定义分区，则可能需要更改的重要区域是分区的名称：

<bean id="sevenSeasPartitionConfiguration"

后缀：

<property name="suffix" value="o=sevenSeas" />

现在剩下的最后一个属性是上下文条目。对象类 top 和 extensibleObject 是通用的，因此它们仍然存在。但是对象类域被对象类组织所取代，因为我们的分区不应该代表一个域而是一个组织：

<property name="contextEntry">

+ <值>
+ 对象类：顶部
+ objectClass：组织
+ 对象类：可扩展对象
+ o: 七海
+ </值>

+</属性>

保存 server.xml 后，您需要下载 jar 文件并将其放入Apache DS 发行版的*/lib目录中。*JAR 包含 LDAP 的 Jetspeed 模式的 Java 实现。对于 ApacheDS 版本 1.0.2，请从此处下载 Jetspeed LDAP 模式 JAR 文件：

[Apache DS 1.0.2 - Jetspeed 模式文件](http://people.apache.org/~taylor/LDAP/jetspeed-security-schema-2.1.3.jar)

对于 ApacheDS 0.9.3 版，请从此处下载 Jetspeed LDAP 模式 JAR 文件：

[Apache DS 0.9.3 - Jetspeed 模式文件](http://people.apache.org/~taylor/LDAP/jetspeed-security-schema-2.1.3-0.9.3.jar)

放入jar文件后，重新启动服务器。Apache DS 现在应该可以支持 Jetspeed 模式了。当服务器启动时，确保控制台上没有打印出与此配置相关的错误消息

#### 3.1.9.2. **Jetspeed 配置**

那么，既然 ApacheDS 具有所需的模式，那么您如何将 Jetspeed 与 ApacheDS 联系起来呢？有两个步骤。

首先，您需要修改 Jetspeed 中 LDAP 安全性的 Spring 配置文件。

其次，您需要在 LDAP 目录中设置一个有效的管理员帐户，以便您能够登录到 Jetspeed。

在我们开始之前，Jetspeed 中的 LDAP 代码直到最近才被破坏，因此如果不手动更改 Java 代码就无法使用（根据我们的测试，至少使用 Apache DS）。因此，您应该确保您使用的是 Jetspeed 2.1.3 或更高版本。

第一步，您需要下载三个 Spring 配置文件。Jetspeed 部署到 Tomcat 时，应该放在*WEB-INF/assembly/override/*目录下。从这里下载：

[http://people.apache.org/\~taylor/LDAP/security-spi-ldap.xml](http://people.apache.org/~taylor/LDAP/security-spi-ldap.xml)

[http://people.apache.org/\~taylor/LDAP/security-spi-ldap-atn.xml](http://people.apache.org/~taylor/LDAP/security-spi-ldap-atn.xml)

[http://people.apache.org/\~taylor/LDAP/security-spi-ldap-atz.xml](http://people.apache.org/~taylor/LDAP/security-spi-ldap-atz.xml)

需要修改*security-spi-ldap.xml*文件。其他两个不需要修改。

最后一步是从*WEB-INF/assembly*目录中删除两个文件：


| mv security-spi-atn.xml备用/ |
| ---------------------------- |
| mv security-spi-atz.xml备用/ |

#### 3.1.9.3. **配置 security-spi-ldap.xml**

Jetspeed 中用于LDAP的*security-spi-ldap.xml*配置文件实际上是一个配置Jetspeed LDAP 实现的XML 文件。总共有 36 个参数（真的！）。虽然并非所有这些参数都可能真正被您使用，但必须全部指定，否则 Jetspeed 将无法初始化。这是您需要修改以指向 LDAP 服务器的基本程序集：

<豆类>

<!-- ************** Ldap 配置 ************** -->

<bean id="org.apache.jetspeed.security.spi.impl.ldap.LdapBindingConfig"

  class="org.apache.jetspeed.security.spi.impl.ldap.LdapBindingConfig">

  <!-- LDAP 初始上下文工厂。-->

  <constructor-arg index="0"><value>com.sun.jndi.ldap.LdapCtxFactory</value></constructor-arg>

  <!-- LDAP 服务器名称。-->

  <constructor-arg index="1"><value>localhost</value></constructor-arg>

  <!-- LDAP 服务器端口。-->

  <constructor-arg index="2"><value>10389</value></constructor-arg>

  <!-- LDAP 服务器根上下文。-->

  <constructor-arg index="3"><value>o=sevenSeas</value></constructor-arg>

  <!-- LDAP 服务器根 dn。-->

  <constructor-arg index="4"><value>uid=admin,ou=system</value></constructor-arg>

  <!-- LDAP 服务器根密码。-->

  <constructor-arg index="5"><value>秘密</value></constructor-arg>

  <!-- 角色过滤器。-->

  <constructor-arg index="6"><value>(objectclass=jetspeed-2-role)</value></constructor-arg>

  <!-- 组过滤器。-->

  <constructor-arg index="7"><value>(objectclass=jetspeed-2-group)</value></constructor-arg>

  <!-- 用户过滤器。-->

  <constructor-arg index="8"><value>(objectclass=jetspeed-2-user)</value></constructor-arg>

  <!-- 角色成员属性。-->

  <constructor-arg index="9"><value>j2-role</value></constructor-arg>

  <!-- userRoleMembershipAttributes。-->

  <constructor-arg index="10"><value>j2-role</value></constructor-arg>

  <!-- groupMembershipAttributes。-->

  <constructor-arg index="11"><value>uniqueMember</value></constructor-arg>

  <!-- 用户组成员属性。-->

  <constructor-arg index="12"><value>j2-group</value></constructor-arg>

  <!-- groupMembershipForRoleAttributes。-->

  <constructor-arg index="13"><value>uniqueMember</value></constructor-arg>

  <!-- roleGroupMembershipForRoleAttributes。-->

  <constructor-arg index="14"><value></value></constructor-arg>     

  <!-- 默认搜索库。-->

  <constructor-arg index="15"><value>o=sevenSeas</value></constructor-arg>

  <!-- 角色过滤器基础。-->

  <constructor-arg index="16"><value>ou=Roles,ou=rootOrg</value></constructor-arg>

  <!-- groupFilterBase。-->

  <constructor-arg index="17"><value>ou=Groups,ou=rootOrg</value></constructor-arg>

  <!-- 用户过滤器基础。-->

  <constructor-arg index="18"><value>ou=People,ou=rootOrg</value></constructor-arg>

  <!-- 角色对象类。-->

  <constructor-arg index="19"><value>top,groupOfUniqueNames,jetspeed-2-role</value></constructor-arg>

  <!-- groupObjectClasses。-->

  <constructor-arg index="20"><value>top,groupOfUniqueNames,jetspeed-2-group</value></constructor-arg>

  <!-- 用户对象类。-->

  <constructor-arg index="21"><value>top,person,organizationalPerson,inetorgperson,jetspeed-2-user</value></constructor-arg>

  <!-- 角色标识属性。-->

  <constructor-arg index="22"><value>cn</value></constructor-arg>

  <!-- groupIdAttribute。-->

  <constructor-arg index="23"><value>cn</value></constructor-arg>

  	<!-- userIdAttribute。-->

  <constructor-arg index="24"><value>cn</value></constructor-arg>

  <!-- UidAttribute。-->

  <constructor-arg index="25"><value>uid</value></constructor-arg>

  <!-- MemberShipSearchScope。-->

  <constructor-arg index="26"><value>1</value></constructor-arg>

  <!-- roleUidAttribute。-->

  <constructor-arg index="27"><value>cn</value></constructor-arg>

  <!-- groupUidAttribute。-->

  <constructor-arg index="28"><value>cn</value></constructor-arg>

  <!-- userUidAttribute。-->

  <constructor-arg index="29"><value>uid</value></constructor-arg>

  <!-- roleObjectRequiredAttributeClasses。-->

  <constructor-arg index="30"><value>cn,j2-classname,uid,uniquemember</value></constructor-arg>

  <!-- groupObjectRequiredAttributeClasses。-->

  <constructor-arg index="31"><value>cn,j2-classname,uid,uniqueMember</value></constructor-arg>

  <!-- 用户属性。-->

  <constructor-arg index="32"><value>sn={u},cn={u},uid={u}</value></constructor-arg>

  <!-- 角色属性。-->

  <constructor-arg index="33"><value></value></constructor-arg>

  <!-- 组属性。-->

  <constructor-arg index="34"><value></value></constructor-arg>

  <!-- 用户密码属性。-->

  <constructor-arg index="35"><value>userPassword</value></constructor-arg>

  <!-- knownAttributes。-->

  <constructor-arg index="36"><value>cn,sn,o,uid,ou,objectClass,userPassword,member,uniqueMember,memberOf,j2-role,j2-group</value></constructor-arg>
</豆>

</beans>

让我们介绍最常用的修改。在此页面上的文档中，我们更详细地介绍了每个参数。您可能需要在以下位置进行更改，以使其适用于您的设置。我根据它在 XML 文件中使用的构造函数参数列出了它们。标有**(!)**的可能更改将需要对 LDIF 文件进行相应更改（稍后解释），因此除非您了解您在这两个文件中所做的事情，否则不要更改它们。


| 1. LDAP服务器的主机名。在我们的例子中，它是“localhost”。如果您的 LDAP 服务器位于运行 Jetspeed 的同一台计算机上，您可能希望将其设置为“localhost”。                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2.我们的 LDAP 服务器在 10389 端口上运行。大多数 LDAP 服务器的默认端口是 389。                                                                                                                                                                                                                               |
| 3.（！）我们将组织名称设置为“o=sevenSeas”，就像在 ApacheDS 示例中所做的那样。如果您想使用不同的组织名称，可以将其更改为“o=yourOrganizationName”形式的任何名称。                                                                                                                                         |
| 15.（！）如果您在#3 中更改了组织名称，则需要在此处进行完全相同的更改。                                                                                                                                                                                                                                      |
| 16.（！）我们将所有 Jetspeed 密钥存储在一个名为“ou=rootOrg”的组中。您可以将其名称更改为您想要的任何名称，只要它的格式为“ou=yourOrganizationalUnit”，并且您的更改会反映在#17、#18 和 LDIF 文件中。在“ou=rootOrg”目录中，我们将所有角色存储在一个名为“ou=Roles”的子目录中。您可能也不需要更改该名称。 |
| 17.(!)正如#16 中提到的，如果你改变了“ou=rootOrg”的名字，你需要相应地改变这个值。                                                                                                                                                                                                                          |
| 18.（！）与#17相同。                                                                                                                                                                                                                                                                                        |

除非更改 LDAP 模式本身，否则其他参数不太可能需要更改。现在，我们需要在 LDAP 目录中设置至少一个 Jetspeed 帐户。而且我们不能使用 Jetspeed 管理 portlet 来执行此操作，因为我们需要以管理员身份登录才能执行此操作（此时不存在任何类型的帐户）。幸运的是，我们创建了一个可以导入 ApacheDS 的 LDIF 文件，并且与上面的 Jetspeed 配置完全匹配。

#### 3.1.9.4. **LDIF 导入**

LDAP 数据交换格式 (LDIF) 是一种标准数据交换格式，用于表示 LDAP 目录内容以及目录更新（添加、修改、删除、重命名）请求。以下文本是 LDIF 文件的内容，可帮助您开始使用 Jetspeed LDAP 基本配置。LDIF 示例中的条目包括用于创建基本 Jetspeed 管理员用户的定义以及启动和运行最小门户所需的角色。为方便起见，您可以从此处下载此 LDIF 文件：

[http://people.apache.org/\~taylor/LDAP/jetspeed-apacheds.ldif](http://people.apache.org/~taylor/LDAP/jetspeed-apacheds.ldif)

使用 Apache DS，我们无法使用 LDIF 导入创建根域。相反，我们必须如上所述创建一个分区。另请查看[root.ldif](http://people.apache.org/~taylor/LDAP/root.ldif)文件，因为它包含您在不同 LDAP 服务器上可能需要的 SevenSeas 组织的根定义。

我们建议使用[LDAP Studio](http://directory.apache.org/studio/)通过 File->Import 将 Jetspeed LDIF 文件导入 Apache DS 服务器

dn: ou=rootOrg,o=sevenSeas

对象类：组织单位

对象类：顶部

ou：rootOrg

dn: ou=People,ou=rootOrg,o=sevenSeas

对象类：组织单位

对象类：顶部

ou：人

dn: ou=Groups,ou=rootOrg,o=sevenSeas

对象类：组织单位

对象类：顶部

ou：组

dn: ou=角色,ou=rootOrg,o=sevenSeas

对象类：组织单位

对象类：顶部

ou：角色

dn: cn=accounting,ou=Groups,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-group

对象类：groupOfUniqueNames

对象类：顶部

中文：会计

j2-classname：会计

uid：会计

唯一成员：用户、本地、次本地

dn: cn=engineering,ou=Groups,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-group

对象类：groupOfUniqueNames

对象类：顶部

中文：工程

j2-classname：工程

uid：工程

唯一成员：用户

dn: cn=marketing,ou=Groups,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-group

对象类：groupOfUniqueNames

对象类：顶部

cn: 营销

j2-classname：营销

uid：营销

唯一成员：用户

dn: cn=admin,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn: 管理员

j2-类名：管理员

用户名：管理员

唯一成员：管理员

dn: cn=manager,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn: 经理

j2-类名：经理

uid：经理

uniquemember: admin,jetspeed,manager

dn: cn=user,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn: 用户

j2-类名：用户

uid：用户

唯一成员：用户、管理员、经理、本地

dn: cn=guest,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

中文：客人

j2-类名：来宾

uid：客人

唯一成员：客人

dn: cn=subsite,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn: 子网站

j2-classname：子站点

uid：子站点

唯一成员：子站点

dn: cn=subsite2,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn: subsite2

j2-类名：subsite2

uid：子站点2

唯一成员：子站点

dn: cn=dev,ou=Roles,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn: 开发

j2-类名：dev

uid：开发者

唯一成员：dev

dn: cn=devmgr,ou=角色,ou=rootOrg,o=sevenSeas

objectClass：jetspeed-2-角色

对象类：groupOfUniqueNames

对象类：顶部

cn:devmgr

j2-类名：devmgr

uid：devmgr

唯一成员：devmgr

dn: cn=admin,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 管理员

名字：管理员

j2-角色：管理员

j2-角色：经理

j2-角色：用户

sn: 管理员

用户名：管理员

用户密码:: c2VjcmV0

dn: cn=manager,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 经理

姓名：经理

j2-角色：经理

j2-角色：用户

sn：经理

uid：经理

用户密码:: c2VjcmV0

dn: cn=user,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 用户

名字：用户

j2-角色：用户

sn：用户

uid：用户

用户密码:: c2VjcmV0

dn: cn=local,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 本地

名字：本地

j2-角色：用户

sn：本地

uid：本地

用户密码:: c2VjcmV0

dn: cn=sublocal,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 次本地

名字：次本地

j2-角色：用户

sn：次本地

uid：次本地

用户密码:: c2VjcmV0

dn: cn=tomcat,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

中文：tomcat

名字：tomcat

sn：tomcat

用户名：tomcat

用户密码:: c2VjcmV0

dn: cn=jetspeed,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 喷气机速度

名字：jetspeed

j2-角色：经理

sn：喷气速度

uid：喷气速度

用户密码:: c2VjcmV0

dn: cn=guest,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

中文：客人

名字：客人

sn：客人

uid：客人

用户密码:: c2VjcmV0

dn: cn=subsite,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: 子网站

给定名称：子站点

j2-角色：子站点

j2-角色：子站点2

j2-角色：用户

sn：子站点

uid：子站点

用户密码:: c2VjcmV0

dn: cn=subsite2,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn: subsite2

给定名称：subsite2

j2-角色：子站点

j2-角色：子站点2

j2-角色：用户

sn：子站点2

uid：子站点2

用户密码:: c2VjcmV0

dn: cn=devmgr,ou=People,ou=rootOrg,o=sevenSeas

objectClass: 组织的人

对象类：人

objectClass: jetspeed-2-user

对象类：inetOrgPerson

对象类：顶部

cn:devmgr

名字：devmgr

j2-角色：devmgr

j2-角色：开发

j2-角色：用户

sn：devmgr

uid：devmgr

用户密码:: c2VjcmV0

那么，从 Jetspeed 的角度来看，它究竟产生了什么？


| \* Jetspeed在关系数据库上开箱即用的所有相同角色、用户和组，是 Jetspeed 正常运行所必需的。                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------- |
| \*创建了三个组（会计、工程、营销）。它们不是 Jetspeed 正常操作的严格要求，但它们显示了如何声明组。                                                  |
| \*创建了八个角色（guest、admin、devmgr、jetspeed、local、manager、sublocal、subsite、subsite2、tomcat、user），与 Jetspeed 的演示分发中的角色集相同 |
| \*管理用户名为**admin**。该用户同时具有“admin”和“manager”角色，因此它具有对所有管理 portlet 的完全访问权限。                                    |
| \*所有用户都是使用密码创建**的**。                                                                                                                  |

**警告：**如果您修改了 security-spi-ldap.xml 中解释旁边带有 (!) 的任何参数，则上述 LDIF 文件将不起作用。它会很好地导入您的 LDAP 服务器，但 Jetspeed 将无法使用它。这是您需要对 LDIF 文件进行更改的列表，根据您修改的参数（如果您没有在 XML 文件中更改它，则不需要在 LDIF 文件中更改它）：


| 3.如果您更改了您的组织名称（默认为“o=sevenSeas”），您需要在每次出现在 LDIF 文件中时更改它。一个简单的“查找/替换”（几乎所有现代文本编辑器都支持）应该就可以了，但是如果留下对“o=sevenSeas”的任何引用（即如果你错过了一两个），那么 LDAP 服务器将拒绝 LDIF 文件为格式错误。 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 15.与#3 相同。                                                                                                                                                                                                                                                                  |
| 16.如果您更改了您的组织单位（默认为“ou=rootOrg”），您需要在每次出现在 LDIF 文件中时对其进行更改。您可以使用与#3 相同的“查找/替换”技巧。与 #3 一样，此处的错误将导致 LDIF 文件格式错误。                                                                                     |
| 17.同#16。                                                                                                                                                                                                                                                                      |
| 18.同#16。                                                                                                                                                                                                                                                                      |

#### 3.1.9.5. **LDAP 配置参考**

本节是 Jetspeed 中 LDAP 安全模块配置示例的参考。开箱即用，Jetspeed 在关系数据库中搜索用户、组和角色信息。但是，它也可以在 LDAP 目录中搜索此信息。

Jetspeed 将其 LDAP 配置存储在名为 [security-spi-ldap.xml 的 Spring XML 文件中](http://svn.apache.org/viewcvs.cgi/portals/jetspeed-2/trunk/components/security/etc/security-spi-ldap.xml?content-type=text/plain&view=co)

此 XML 文件描述了一个包含 LDAP 配置参数的对象（Jetspeed 内部使用）。这些配置参数通过构造函数参数传递给对象：

<!-- LDAP 初始上下文工厂。-->

<constructor-arg index="0">

<value>com.sun.jndi.ldap.LdapCtxFactory</value>

</constructor-arg>

每个构造函数参数都包含一个索引来指定正确的顺序。该文件定义了以下参数：


| **指数** | **姓名**                             | **例子**                                                             |
| -------- | ------------------------------------ | -------------------------------------------------------------------- |
| 0        | 初始上下文工厂                       | com.sun.jndi.ldap.LdapCtxFactory                                     |
| 1        | LDAP服务器主机                       | 本地主机                                                             |
| 2        | LDAP服务器端口                       | 389                                                                  |
| 3        | 根上下文                             | o=七海                                                               |
| 4        | LDAP服务器根 dn                      | uid=admin,o=sevenSeas                                                |
| 5        | LDAP服务器根密码                     | 秘密                                                                 |
| 6        | 角色过滤器                           | (objectclass=groupOfUniqueNames))                                    |
| 7        | 组过滤器                             | (objectClass=groupOfNames)                                           |
| 8        | 用户过滤器                           | （对象类=inetorgperson）                                             |
| 9        | 角色会员属性                         | 唯一会员                                                             |
| 10       | userRoleMembershipAttributes         |                                                                      |
| 11       | groupMembershipAttributes            | 成员                                                                 |
| 12       | userGroupMembershipAttributes        |                                                                      |
| 13       | groupMembershipForRoleAttributes     | 唯一会员                                                             |
| 14       | roleGroupMembershipForRoleAttributes |                                                                      |
| 15       | 默认搜索库                           |                                                                      |
| 16       | 角色过滤器库                         | ou=角色，ou=rootOrg                                                  |
| 17       | groupFilterBase                      | ou=组，ou=rootOrg                                                    |
| 18       | 用户过滤器库                         | ou=人，ou=rootOrg                                                    |
| 19       | 角色对象类                           | 顶部，groupOfUniqueNames                                             |
| 20       | 组对象类                             | 顶部，名称组                                                         |
| 21       | 用户对象类                           | 顶部,人,组织人,inetorgperson                                         |
| 22       | 角色标识属性                         | cn                                                                   |
| 23       | groupId属性                          | cn                                                                   |
| 24       | 用户标识属性                         | uid                                                                  |
| 25       | Uid属性                              | uid                                                                  |
| 26       | 会员搜索范围                         | 1                                                                    |
| 27       | 角色Uid属性                          | cn                                                                   |
| 28       | groupUid属性                         | cn                                                                   |
| 29       | userUidAttribute                     | uid                                                                  |
| 30       | roleObjectRequiredAttributeClasses   | 唯一会员                                                             |
| 31       | groupObjectRequiredAttributeClasses  | 成员                                                                 |
| 32       | 用户属性                             | sn={u},cn={u}                                                        |
| 33       | 角色属性                             | sn={u}                                                               |
| 34       | 组属性                               | sn={u}                                                               |
| 35       | 用户密码属性                         | 密码                                                                 |
| 36       | 已知属性                             | cn,sn,o,uid,ou,objectClass,userPassword,member,uniqueMember,memberOf |

#### 3.1.9.6. **将 Jetspeed 2 配置为使用 LDAP**

为 LDAP 使用配置 jetspeed 只需准备好适当的配置文件即可。这些配置文件将放置在**WEB-INF/assembly**扩展的 jetspeed WAR 的文件夹中。

如果要将 Jetspeed2 连接到 LDAP 服务器，需要将以下文件复制到该目录中。

· [*security-spi-ldap.xml *](http://svn.apache.org/viewcvs.cgi/portals/jetspeed-2/trunk/components/security/etc/security-spi-ldap.xml?content-type=text/plain&view=co)*：* 提供 LDAP 绑定的配置信息，下面详细解释。

· [*security-spi-ldap-atn.xml *](http://svn.apache.org/viewcvs.cgi/portals/jetspeed-2/trunk/components/security/etc/security-spi-ldap-atn.xml?content-type=text/plain&view=co)*：* 提供用于身份验证的 SPI 配置。*它将CredentialHandler*和*UserSecurityHandler*的默认实现替换为 LDAP 特定的实现。

· [*security-spi-ldap-atz.xml *](http://svn.apache.org/viewcvs.cgi/portals/jetspeed-2/trunk/components/security/etc/security-spi-ldap-atz.xml?content-type=text/plain&view=co)*：* 为授权提供 SPI 配置。*它将RoleSecurityHandler*、 *GroupSecurityHandler*和*SecurityMappingHandler*的默认实现替换为 LDAP 特定实现。

需要从该程序集目录中删除 默认的身份验证和授权 SPI 配置（称为**security-spi-atn.xml**和的文件）。**security-spi-atz.xml**

在 Jetspeed 源代码树中，可以在以下位置找到示例 ldap 配置文件：

${jetspeed-source-home}/components/security/etc/

如果您的应用程序部署在 Tomcat 中，则目标程序集目录位于：

${tomcat-home}/webapps/jetspeed/WEB-INF/assembly/

此外，Jetspeed 安全组件的源代码树提供了几个使用不同配置的测试以及用于测试 ApacheDS、OpenLDAP、Domino 和 sunDS LDAP 服务器的 ldiff 样本数据。这些位于：

${jetspeed-source-home}/components/security/src/test/JETSPEED-INF/directory/config/

我们将在下面详细讨论 security-spi-ldap.xml 文件。

##### 3.1.9.6.1. **LDAP 连接属性**

Jetspeed 需要知道的第一个问题是它如何连接到目录存储。

这是通过提供以下属性来完成的：

**initialContextFactory**

初始上下文工厂

<constructor-arg index="0">

<value>com.sun.jndi.ldap.LdapCtxFactory</value>

</constructor-arg>

**ldapServerName**

LDAP 服务器的名称

<constructor-arg index="1">

<值>本地主机</值>

</constructor-arg>

**ldapServerPort**

LDAP 服务器的端口

<constructor-arg index="2">

<值>389</值>

</constructor-arg>

**rootContext**

LDAP 服务器的根上下文

<constructor-arg index="3">

<value>o=sevenSeas</value>

</constructor-arg>

**rootDn**

用户名

<constructor-arg index="4">

<value>uid=admin,ou=system</value>

</constructor-arg>

**rootPassword**

密码

<constructor-arg index="5">

<value>秘密</value>

</constructor-arg>

使用 LDAP 浏览器验证连接：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps18.jpg)

##### 3.1.9.6.2. **LDAP 对象过滤器**

目录服务可以在任何地方存储任何类型的对象。由于 Jetspeed 需要使用目录中定义的角色、组和用户，因此需要一些帮助才能找到它们。

以下 3 个属性定义 Jetspeed 如何从目录存储中查找角色、组和用户。

· 角色过滤器

· 组过滤器

· 用户过滤器

属性值必须是在 LDAP 模式中定义的有效对象类。

大多数 LDAP 供应商通常通过定义目录存储中可用的每个属性和对象类的 LDIF 文件公开他们的模式。

基于 Lotus Domino 的配置可能如下所示

RoleFilter=(&(objectclass=groupOfUniqueNames)(!(objectClass=dominoGroup)))

GroupFilter=(objectclass=dominoGroup)

UserFilter=(objectclass=dominoPerson)

Domino 使用**dominoGroup** objectClass 定义组，**使用 dominoPerson**定义用户，使用**groupOfUniqueNames**定义角色。由于 group 也有 groupOfUniqueNames 作为对象类，我们需要为角色定义一个过滤器，以便它只会选择角色。如果我们将 RoleFilter 定义为 (objectclass=groupOfUniqueNames)，那么过滤器也会拾取这些组。

**RoleFilter**

此属性告诉 Jetspeed，可以通过查找值为**groupOfUniqueNames的objectClass**属性 来识别角色。

<constructor-arg index="6">

<value>=(objectclass=groupOfUniqueNames)</value>

</constructor-arg>

**GroupFilter**

该属性告诉 Jetspeed，可以通过查找值为**groupOfNames的objectClass**属性 来识别组。

<constructor-arg index="7">

<value>=(objectclass=groupOfUniqueNames)</value>

</constructor-arg>

**UserFilter**

**该属性告诉 Jetspeed，可以通过查找objectClass**属性值 来识别用户**organizationsPerson**。

<constructor-arg index="8">

<value>=(objectclass=organizationalPerson)</value>

</constructor-arg>

除了这些过滤器，我们还可以为每个对象（角色、组和用户）定义一个过滤器基础。

##### 3.1.9.6.3. **组/角色成员资格**

在 LDAP 中，基本上有 2 种方法来定义组和角色成员身份（用户属于组或角色的事实）：

· 用户对象具有指定他所属的组的属性。这通常通过 memberOf 属性来完成。Microsoft Active Directory 和 Sun Directory Server 在用户对象上使用 memberOf 和 nsrole 属性。

· 组/角色对象通过多值属性包含组成员信息。用户没有属性来指定成员资格。每个组/角色对象都有一个成员列表，其中包含属于该组的用户

Jetspeed 支持这两种型号。

有关 LDAP 成员资格的主要任务是

· 确定用户是否属于特定组/角色

· 获取属于特定组/角色的用户列表

我们刚刚介绍的 2 个模型会影响这些任务的执行方式

· 用户对象的属性

o 确定用户是否属于特定组/角色：

§ 在特定组/角色的用户对象上查找成员资格属性（例如：memberOf）

o 获取属于特定组/角色的用户列表：

§ 遍历所有用户，并检查组的 memberOf 属性值

· 组/角色对象的属性

o 要确定用户是否属于特定组：

§ 在组的成员列表中搜索用户

o 要确定属于特定组的用户：

§ 遍历组上的成员列表

我们现在将详细讨论如何配置组/角色成员资格。

##### 3.1.9.6.4. **角色成员资格**

如前所述，Jetspeed 在角色成员资格方面支持 2 种模型：

1. 将属性放在用户身上
2. 将属性放在角色上

Jetspeed 要求为 2 个属性中的 1 个设置一个值来确定模型：

· RoleMembershipAttributes

· UserRoleMembershipAttributes

**RoleMembershipAttributes**

为了在角色上存储角色成员资格，我们将通过在包含成员资格信息的角色对象上指定属性来设置**RoleMembershipAttributes属性。**我们不为**UserRoleMembershipAttributes**属性提供值。

<constructor-arg index="9">

<value>成员</value>

</constructor-arg>

这将确保在角色对象上设置成员属性，如以下屏幕截图所示。在下一个示例中，RoleMembershipAttribute 将为空白，因此属性将位于用户级别。

在下面的截图中，我们有一个由

**cn=Role3,ou=Roles,ou=rootOrg,o=sevenSeas定义的 Role 对象**

该角色包含一个成员属性，列出属于该角色的所有用户。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps19.jpg)

*一个有 2 个成员的角色*

member 属性的值是用户的完全限定 DN（包括根上下文）。如您所见，用户不包含有关角色成员资格的任何属性。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps20.jpg)

*一个用户*

设置此属性后，Jetspeed 将通过执行以下查询来确定特定用户的角色：

(&(member=cn=user1,ou=people,ou=rootOrg,o=sevenSeas)(objectclass=groupOfNames))

此搜索过滤器将返回目录中任意数量的角色。Jetspeed 的下一步是在内部识别这些角色。为了唯一标识一个角色，它将使用 RoleIdAttribute。

在上面的示例中，cn=Role1 将在搜索结果中。Jetspeed 将使用 RoleIdAttribute 来获取角色名称。

**UserRoleMembershipAttributes**

为了存储用户的角色成员资格，我们将通过在包含成员资格信息的用户对象上指定属性来设置**UserRoleMembershipAttributes属性。**我们不为**RoleMembershipAttributes**属性提供值。

<constructor-arg index="10">

<value>memberOf</value>

</constructor-arg>

这将确保对于用户所属的每个角色，在用户对象上设置 memberOf 属性，如以下屏幕截图所示：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps21.jpg)

*属于 4 个不同角色的用户*

**memberOf**属性 的值是角色的完全限定 DN（包括根上下文）。它是一个多值属性，因此用户可以拥有零个或多个**memberOf**属性值。

如您所见，用户属于

**cn=role1,ou=Roles,rootOrg,o=sevenSeas**定义的角色。

为了解析角色成员资格，Jetspeed 将使用以下过滤器在目录中搜索角色：

# 定义搜索角色/组/用户所需的过滤器

RoleFilter=(objectclass=groupOfUniqueNames)

正如您在屏幕截图中看到的，cn=role1,o=sevenSeas 对应于代表角色的对象。

注意空的 uniqueMember 属性。大多数 LDAP 模式强制您在**groupOfUniqueNames**对象上具有**uniqueMember**属性。由于 Jetspeed 需要能够创建角色（创建时为空），因此需要设置一个空的**uniqueMember属性。**这可由 Jetspeed 通过**RequiredAttributeClasses**属性进行配置。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps22.jpg)

*没有任何成员的角色*

##### 3.1.9.6.5. **组成员**

如前所述，Jetspeed 在群组成员方面支持 2 种模型：

1. 将属性放在用户身上
2. 将属性放在组上

Jetspeed 要求为 2 个属性中的 1 个设置一个值来确定模型：

· GroupMembershipAttributes

· 用户组成员属性

**GroupMembershipAttributes**

为了在组中存储组成员资格，我们将通过在包含成员资格信息的组对象上指定属性来设置**GroupMembershipAttributes属性。**我们不为**UserGroupMembershipAttributes**属性提供值。

<constructor-arg index="11">

<value>uniqueMember</value>

</constructor-arg>

这将确保在组对象上设置了**uniqueMember**属性，如以下屏幕截图所示。在前面的示例中，**GroupMembershipAttributes**是空白的，因此在用户级别上使用 了**UserGroupMembershipAttributes ：**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps23.jpg)

uniquemember 属性的值是用户的完全限定 DN（包括根上下文）。如您所见，用户不包含任何关于组成员身份的属性。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps24.jpg)

**UserGroupMembershipAttributes**

为了在用户上存储组成员资格，我们将通过在包含成员资格信息的用户对象上指定属性来设置**UserGroupMembershipAttributes属性。**我们不为**GroupMembershipAttributes**属性提供值。

<constructor-arg index="12">

<value>memberOf</value>

</constructor-arg>

这将确保在用户对象上设置**memberOf**属性，如以下屏幕截图所示。

只能填写其中一个参数。如果设置了**GroupMemberShipAttributes**，Jetspeed 假定确定组成员身份的属性位于组对象上。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps25.jpg)

*属于 2 个不同角色的用户*

memberOf 属性的值是角色的完全限定 DN（包括根上下文）。它是一个多值属性，因此用户可以拥有零个或多个 memberOf 属性值。在上面的截图中，我们可以看到 user1 属于 2 个角色。

如您所见，角色在**cn=role1,o=sevenSeas**中定义。（注意空的 uniqueMember 属性）。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps26.jpg)

*角色定义*

##### 3.1.9.6.6. **组成员（角色）**

除了将用户存储在一个组中，Jetspeed 还支持将角色存储到组中。

同样，就像用户的基本组成员资格一样，Jetspeed 在角色的组成员资格方面支持 2 种模型：

1. 将属性放在角色上
2. 将属性放在组上

Jetspeed 要求为 2 个属性中的 1 个设置一个值来确定模型：

· GroupMembershipForRoleAttributes

· RoleGroupMembershipForRoleAttributes

**GroupMembershipForRoleAttributes**

为了在组中存储组成员资格，我们将通过在包含成员资格信息的组对象上指定属性来设置 GroupMembershipAttributes 属性。我们不为 UserGroupMembershipAttributes 属性提供值。

<constructor-arg index="13">

<value>uniqueMember</value>

</constructor-arg>

这将确保在组对象上设置了 uniqueMember 属性，如以下屏幕截图所示。在前面的示例中，GroupMembershipAttributes 是空白的，因此在用户级别上使用了 UserGroupMembershipAttributes。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps27.jpg)

uniquemember 属性的值是用户的完全限定 DN（包括根上下文）。如您所见，用户不包含任何关于组成员身份的属性。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps28.jpg)

**RoleGroupMembershipForRoleAttributes**

为了在用户上存储组成员资格，我们将通过在包含成员资格信息的用户对象上指定属性来设置**UserGroupMembershipAttributes属性。**我们不为**GroupMembershipAttributes**属性提供值。

<constructor-arg index="14">

<value>memberOf</value>

</constructor-arg>

这将确保在用户对象上设置**memberOf**属性，如以下屏幕截图所示。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps29.jpg)

uniquemember 属性的值是用户的完全限定 DN（包括根上下文）。如您所见，用户不包含任何关于组成员身份的属性。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps30.jpg)

只能填写其中一个参数。如果设置了**GroupMemberShipAttributes**，Jetspeed 假定确定组成员身份的属性位于组对象上。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps31.jpg)

*属于 2 个不同角色的用户*

memberOf 属性的值是角色的完全限定 DN（包括根上下文）。它是一个多值属性，因此用户可以拥有零个或多个 memberOf 属性值。在上面的截图中，我们可以看到 user1 属于 2 个角色。

如您所见，角色在**cn=role1,o=sevenSeas**中定义。（注意空的 uniqueMember 属性）。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps32.jpg)

*角色定义*

##### 3.1.9.6.7. **默认搜索库**

Jetspeed 允许您定义将用于搜索目录的默认搜索库

<constructor-arg index="15">

<值></值>

</constructor-arg>

##### 3.1.9.6.8. **LDAP 对象过滤器基础**

Jetspeed 允许您定义将应用于角色、组和用户查询的搜索库。

角色、组和用户通常存储在 LDAP 结构内定义明确的容器中。

· 角色可以存储在 ou=Roles,ou=rootOrg

· 组可以存储在 ou=Groups,ou=rootOrg

· 用户可以存储在ou=People,ou=rootOrg

这允许您在 LDAP 模式中具有以下结构。请注意 o=sevenSeas 模式中有许多组织单位。Jetspeed 将其在 LDAP 上的搜索范围限制为上面定义的属性值。这意味着 Jetspeed 将仅使用 rootOrg 中的角色、组和人员。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps33.jpg)

因此，与对象过滤器（RoleFilter、GroupFilter、UserFilter）一起，Jetspeed 将能够在目录中定位角色、组和用户。

使用这些属性，Jetspeed 还将使用提供的 ObjectClasses 创建角色、组和用户。

**RoleFilterBase**

使用下面的属性值，Jetspeed 将在 ou=Roles,ou=OrgUnit 子树中搜索角色。

<constructor-arg index="16">

<value>ou=Roles,ou=rootOrg</value>

</constructor-arg>

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps34.jpg)

**GroupFilterBase**

使用上面的属性值，Jetspeed 将在 ou=Groups,ou=OrgUnit 子树中搜索组。

<constructor-arg index="17">

<value>ou=Groups,ou=rootOrg</value>

</constructor-arg>

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps35.jpg)

**UserFilterBase**

使用上面的属性值，Jetspeed 将在 ou=People,ou=OrgUnit 子树中搜索用户。

<constructor-arg index="18">

<value>ou=People,ou=rootOrg</value>

</constructor-arg>

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps36.jpg)

##### 3.1.9.6.9. **LDAP 对象类**

Jetspeed 允许您通过以下属性定义创建角色、组和用户所需的 ObjectClass

· 角色对象类

· 组对象类

· 用户对象类

通过管理界面，Jetspeed 允许管理员创建角色、组和用户。每个目录服务器都有自己定义角色、组或用户的方式。一些 LDAP 供应商使用专有的 ObjectClasses 来定义这些对象（例如 Domino LDAP 服务器使用 dominoGroup objectClass 来定义组）。

使用这些属性，Jetspeed 将使用提供的 ObjectClasses 创建角色、组和用户。

**RoleObjectClasses**

<constructor-arg index="19">

<value>top,groupOfNames</value>

</constructor-arg>

使用上面的设置，角色将像这样创建

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps37.jpg)

注意由 RoleObjectClasses 属性定义的所有 objectClasses 是如何在 LDAP 中创建的

**GroupObjectClasses**

<constructor-arg index="20">

<value>top,groupOfUniqueNames</value>

</constructor-arg>

使用上面的设置，组将像这样创建

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps38.jpg)

注意由 GroupObjectClasses 属性定义的所有 objectClasses 是如何在 LDAP 中创建的

**UserObjectClasses**

<constructor-arg index="21">

<value>top,groupOfUniqueNames</value>

</constructor-arg>

使用上面的设置，用户将像这样创建

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps39.jpg)

注意由 UserObjectClasses 属性定义的所有 objectClasses 是如何在 LDAP 中创建的

##### 3.1.9.6.10. **命名属性**

· RoleId 属性

· GroupId 属性

· 用户标识属性

上面的属性允许您定义角色/组和用户的命名属性。在目录中创建对象时，需要指定命名属性。命名属性是在其子目录中唯一定义对象的属性。

在下面的屏幕截图中，您可以看到 rootOrg/People 中的 admin 用户由**cn=admin**定义。

**cn**是用户对象的命名属性，因为 rootOrg/People 子目录中不能存在 2 个管理员用户

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps40.jpg)

通过更改属性，您可以控制 Jetspeed 创建用户对象的方式。

**RoleIdAttribute**

<constructor-arg index="22">

<value>cn</value>

</constructor-arg>

**GroupIdAttribute**

<constructor-arg index="23">

<value>cn</value>

</constructor-arg>

**UserIdAttribute**

<constructor-arg index="24">

<value>uid</value>

</constructor-arg>

在下面的屏幕截图中，用户将**uid**属性作为其命名属性

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps41.jpg)

##### 3.1.9.6.11. **UserId 属性**

当 Jetspeed 尝试查找用户时，它会根据用户在登录屏幕中提供的 userId 进行查找。这个 userId 需要通过特定的属性在对象上定义。大多数 LDAP 服务器都有一个 uid 属性，用于定义 LDAP 中用户的用户名。

Jetspeed内部构建userPrincipal时，会使用userUidAttribute的值对应的属性。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps42.jpg)

**userUidAttribute**

<constructor-arg index="25">

<value>cn</value>

</constructor-arg>

此属性与 UidAttribute 结合使用

UserIdAttribute=cn

UidAttribute=uid

##### 3.1.9.6.12. **会员搜索范围**

Jetspeed 允许您在会员资格方面自定义搜索范围

<constructor-arg index="26">

<value>cn</value>

</constructor-arg>

##### 3.1.9.6.13. **必需的属性类**

某些 ObjectClass 强制您在将对象存储到目录之前为其添加特定属性。Jetspeed 允许您通过以下属性为角色和组指定这些属性

· roleObjectRequiredAttributeClasses

· roleObjectRequiredAttributeClasses

例如，大多数 LDAP 模式强制您在**groupOfUniqueNames**对象上具有**uniqueMember**属性。

由于 Jetspeed 需要能够通过管理控制台创建空角色，因此需要在创建角色时设置一个空的**uniqueMember**属性。

这由 Jetspeed 内部处理，可以通过设置**groupObjectRequiredAttributeClasses**属性进行自定义。

**roleObjectRequiredAttributeClasses**

以下属性指定如果创建角色，将在角色对象上创建一个空的**成员**属性，以符合 LDAP 模式。

<constructor-arg index="30">

<value>成员</value>

</constructor-arg>

**groupObjectRequiredAttributeClasses**

以下属性指定如果创建组，将在组对象上创建一个空的**uniqueMember**属性，以符合 LDAP 模式。

<constructor-arg index="31">

<value>uniqueMember</value>

</constructor-arg>

##### 3.1.9.6.14. **LDAP 对象属性**

Jetspeed 有一个管理控制台，允许管理员在目录中创建组、角色和用户。Jetspeed LDAP 配置有 3 个属性可以操纵这些对象的创建

· 用户属性

· 角色属性

· 组属性

每个属性都接受一个逗号分隔的属性列表。占位符可用于属性值。

**userAttributes**

例如，以下**userAttributes**值将确保当 Jetspeed 在目录中创建用户时，将创建包含用户用户名的 **sn、cn 和 uid属性。**

<constructor-arg index="32">

<value>sn={u},cn={u}</value>

</constructor-arg>

**roleAttributes**

例如，以下**roleAttributes**值将确保当 Jetspeed 在目录中创建用户时，将创建包含用户用户名的 **cn属性。**

<constructor-arg index="33">

<value>cn={u}</value>

</constructor-arg>

**groupAttributes**

例如，以下**groupAttributes**值将确保当 Jetspeed 在目录中创建用户时，将创建包含用户用户名的 **cn属性。**

<constructor-arg index="34">

<value>cn={u}</value>

</constructor-arg>

##### 3.1.9.6.15. **LDAP 密码属性**

在运行期间，Jetspeed 需要读取与用户关联的密码。Jetspeed 需要知道包含密码的用户对象的属性。**userPasswordAttribute**属性定义包含用户密码的 LDAP 属性

<constructor-arg index="35">

<value>cn={u}</value>

</constructor-arg>

##### 3.1.9.6.16. **已知属性**

当 Jetspeed 执行 LDAP 查询时，我们需要指定我们想要返回的属性集。这是通过在**knowAttributes**属性 中指定 LDAP 属性的逗号分隔值来完成的

<constructor-arg index="36">

<value>cn,sn,o,uid,ou,objectClass,userPassword,member,uniqueMember,memberOf</value>

</constructor-arg>

## 3.2. [**核心组件**](https://portals.apache.org/jetspeed-2/devguide/dev-cm.html)

### 3.2.1. **功能概述**

Jetspeed-2 功能提供了一种机制，用于将用于访问 Jetspeed-2 的客户端映射到用于页面呈现的媒体类型。

#### 3.2.1.1. **能力定义**

Jetspeed-2 功能引擎将客户端映射到媒体类型到 MIME 类型。以下是一些更详细的定义：

· 客户端：向 Jetspeed-2 门户引擎发起请求的应用程序。Jetspeed-2 使用User-Agent来确定发起请求的客户端。

· 媒体类型：请求内容的媒体类型（HTML、WML 等）。Jetspeed-2 中的内容可以由不同类型的设备通过不同的媒体请求。

· Mime Type：被请求的内容类型。

Jetspeed-2 适用于以下媒体类型：


| **姓名**   | **字符集** | **描述**                          |
| ---------- | ---------- | --------------------------------- |
| html       | UTF-8      | 用于兼容HTML 4.0的浏览器的富 HTML |
| wml        | UTF-8      | 兼容WML 1.1的手机和 PDA 格式      |
| vxml       | UTF-8      | 适用于音频VoiceXML服务器的格式    |
| xml        |            | XML 1.0                           |
| xhtml-基础 | UTF-8      | WAP设备中使用的 XHTML Basic       |

Jetspeed-2 配置为识别以下客户端：


| **客户**      | **用户代理模式**   | **制造商**              | **首选Mime 类型** |
| ------------- | ------------------ | ----------------------- | ----------------- |
| 即5           | .\*MSIE 5.\*       | 微软                    | html              |
| 即6           | .\*MSIE 6.\*       | 微软                    | html              |
| ns4           | .\*Mozilla/4.\*    | 网景                    | html              |
| Mozilla       | .\*Mozilla/5.\*    | Mozilla                 | html              |
| 猞猁          | 猞猁\*             | GNU                     | html              |
| 歌剧7         | .\*歌剧/7.*        | 歌剧                    | html              |
| ie5mac        | .\*MSIE 5.\*Mac.\* | 微软                    | html              |
| 苹果浏览器    | .\*Mac.\*Safari.\* | 苹果                    | html              |
| xhtml-基础    | DoCoMo/2.0.\*      | KDDI-.\*UP\\.Browser.\* | J-PHONE/5.0.\*    |
| 代理xml       | 代理xml/1.0.\*     | 不适用                  | xml               |
| 诺基亚通用    | 诺基亚。\*         | 诺基亚                  | wml               |
| 向上          | UP.\*              | .\*UP\\.Browser.\*      | 联合星球          |
| 索尼爱立信    | Ercis.\*           | 索尼E.*                 | 索尼爱立信        |
| 瓦帕利器      | 瓦帕利器。\*       | 瓦帕利泽                | wml               |
| 克朗代克      | 克朗代克\*         | 克朗代克                | wml               |
| wml\_generic  | .\*WML.\*          | .\*WAP.\*               | .\*Wap.\*         |
| vxml\_generic | .\*VoiceXML.\*     | 不适用                  | vxml              |
| 细微差别      | 细微差别。\*       | 细微差别                | vxml              |

#### 3.2.1.2. **能力和内容渲染**

**media-type**用于定位给定的适当装饰 模板**media-type**。

#### 3.2.1.3. **能力实施**

该**Capabilities**组件从请求标头 **CapabilityMap**提供的信息中派生出一个：**User-Agent**

cm = 能力.getCapabilityMap(代理);

此操作发生在 Jetspeed-2 请求管道处理的最开始。一旦 **CapabilityMap**检索到，它就会被添加到 Jetspeed-2**org.apache.jetspeed.request.RequestContext** 并提供给门户引擎以处理请求。

下面的两张图片描述了**Capabilities**支持实现的接口和关系数据库模型。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps43.png)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps44.png)

### 3.2.2. [**部署**](https://portals.apache.org/jetspeed-2/devguide/dev-deploy.html)

#### 3.2.2.1. **在 Jetspeed-2 中部署 Portlet：最终用户视图**

在 Jetspeed-2 中部署自定义 portlet 很简单。Portlet 与 servlet 非常相似。它们需要一个部署描述符，**portlet.xml**该描述符进入**WEB-INF** 并需要以类似战争的格式打包。**portlet.xml**您可以在 Jetspeed-2 源代码树中找到很多示例文件。对于初学者来说，看看下面的**/portal/src/webapp/WEB-INF**。为了部署 portlet，Jetspeed-2 要求用户遵循以下步骤：

1. 将您的 portlet 构建为一个 portlet 应用程序，就像您构建一个 web 应用程序一样。
2. 将您的 portlet 应用程序打包到一个 .war 文件中。
3. 将 .war 文件复制到 Jetspeed 的部署目录，默认为 .war **WEB-INF/deploy**。Jetspeed 将负责自动将 portlet 部署到 portlet 注册表中，并将 portlet 作为 Web 应用程序部署到部署 Jetspeed 的应用服务器中。
4. 查看您的 portlet 最简单的方法是在**default-page.psml**下面添加一个条目**jetspeed/WEB-INF/pages**。portlet 片段的 id 使用唯一的组合，**\${portlet.application.id}::\${portlet.name}** 其中**\${portlet.application.id}**包含您的 portlet 应用程序的 war 文件的实际名称（减去“.war”），并且 **\${portlet.name}**需要是 portlet 名称标签中的值，**<portlet-name>MyPortlet</portlet-name>**. 对 psml 的更改将自动获取，您现在应该能够查看您的 portlet！

#### 3.2.2.2. **Portlet 部署：它是如何工作的？**

下面的组件层次结构描述了支持 Jetspeed-2 部署功能的组件依赖项。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps45.png)

**DeploymentManager**配置有以下指定的 属性**WEB-INF/conf/jetspeed.properties**：

· **autodeployment.staging.dir**：为自动部署扫描的目录。

· **autodeployment.delay**：部署目录扫描的频率。

**DeploymentManager**还配置了 2 种 类型**DeploymentEventListener**：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps46.png)

· 处理portlet 应用程序的**DeployPortletAppEventListener**热部署。

· :**DeployDecoratorEventListener**处理装饰器的热部署。有关更多信息，请参阅 [装饰器指南。](https://portals.apache.org/jetspeed-2/devguide/guide-decorators.html)

Jetspeed-2 提供了一个**StandardDeploymentManager**. **StandardDeploymentManager**利用 a**FileSystemScanner**扫描要部署的新资产。它利用 Jetspeed-2 [部署工具](https://portals.apache.org/jetspeed-2/deployguide/deploy-tools.html)在部署之前准备 portlet 应用程序。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps47.png)

### 3.2.3. [**搜索**](https://portals.apache.org/jetspeed-2/devguide/dev-search.html)

Jetspeed-2 提供了与流行的[Apache Lucene](http://lucene.apache.org/)的集成，这是一个完全用 Java 编写的高性能、全功能的文本搜索引擎库；适用于几乎所有需要全文搜索的应用程序的技术，尤其是跨平台的..

#### 3.2.3.1. **搜索引擎概述**

Jetspeed-2 提供了一个**SearchEngine**配置为弹簧组件的组件。该**SearchEngine** 组件配置在**WEB-INF/assembly/search.xml**. 基于嵌入式 Lucene 搜索引擎的默认实现必须指定搜索索引文件的位置、分析器类的名称（如果为 null **StandardAnalyzer**则使用默认分析器）、更新后是否优化以及**HandlerFactory**：

<bean id="org.apache.jetspeed.search.SearchEngine"

  class="org.apache.jetspeed.search.lucene.SearchEngineImpl">

  <constructor-arg index="0"><value>${applicationRoot}/WEB-INF/search_index</value></constructor-arg>

  <constructor-arg index="1"><null /></constructor-arg>

  <constructor-arg type="boolean"><value>true</value></constructor-arg>

  <constructor-arg><ref bean="org.apache.jetspeed.search.HandlerFactory"/></constructor-arg>

</豆>
**HandlerFactory**提供了**SearchEngine**一个列表， 该列表**ObjectHandler** 将处理 Jetspeed-2 支持的各种文档类型进行搜索。默认情况下，Jetspeed-2 支持作为可搜索实体的 portlet 实例和 portlet 定义。当 Portlet 注册到门户 **searchEngine.add(pa)**并被**searchEngine.add(pa.getPortletDefinitions())**调用时。此操作会更新 Jetspeed-2 搜索索引。有关如何将 portlet 注册到搜索引擎的更多信息，请参阅**org.apache.jetspeed.tools.pamanager.PortletApplicationManager**。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps48.png)

#### 3.2.3.2. **文档处理程序概述**

文档处理程序负责解析特定文档类型以索引相关文档字段。

Jetspeed-2 提供了 2 个文档处理程序实现，负责将 Jetspeed-2 支持的文档解析为**org.apache.jetspeed.search.ParsedObject**. 指定 Jetspeed-2 支持的字段和文档列表， **ParsedObject**然后可以**org.apache.lucene.document.Document**通过**indexWriter.addDocument(doc)**. [IndexWriter](http://lucene.apache.org/java/docs/api/index.html)

默认情况下，Jetspeed-2 可以通过 **PortletApplicationHandler**和分别索引 portlet 应用程序和 portlet 定义**PortletDefinitionHandler**。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps49.png)

#### 3.2.3.3. **可扩展的框架**

与 Jetspeed-2 中的大多数组件一样，搜索引擎可以轻松扩展以支持其他文档类型。

### 3.2.4. [**统计数据**](https://portals.apache.org/jetspeed-2/devguide/dev-statistics.html)

Jetspeed-2 提供了用于收集各种应用程序事件的门户数据的组件。

#### 3.2.4.1. **收集门户数据**

**PortalStatistics**提供用于收集门户应用程序事件的 API。开箱即用支持以下事件类型：

· Portlet 呈现统计信息。

· 页面渲染统计。

· 用户访问统计。

**PortalStatistics**实现基于 [Apache 通用日志格式 (CLF)](http://httpd.apache.org/docs/logs.html)记录使用数据 ， 其中每个日志条目的格式为：

%h %l %u %t \"%r\" %>s %b
在哪里：

· **%h** - 远程主机

· **%l** - 远程日志名称

· **%u** - 远程用户

· **%t** - 通用日志时间格式的时间

· **%r** - HTTP 请求的第一行

· **%s** - HTTP 状态码

· **%b** - 发送的字节数（如果没有发送字节，则为“-”）。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps50.png)

统计数据存储在 3 个关系表中，如下图所示：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps51.png)

每个事件类型都映射到一个数据持有者，该数据持有者在上面说明的统计表中持久化。 Jetspeed-2 通过组件 

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps52.png)

将收集到的数据分批持久化。**BatchedStatistics**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps53.png)

#### 3.2.4.2. **门户统计配置**

该**PortalStatistics**组件在中配置**WEB-INF/assembly/statistics.xml**，需要以下配置参数：

· **logToCLF**：是否记录到通用日志格式文件。

· **logToDatabase**：是否记录数据库中的统计信息。

· **maxRecordToFlush\_Portlet**：在刷新发生之前可以在 portlet 统计信息 FIFO 中的 portlet 事件的最大数量。

· **maxRecordToFlush\_User**：在刷新发生之前，可以在用户统计信息 FIFO 中的用户事件的最大数量。

· **maxRecordToFlush\_Page**：在刷新发生之前可以在页面统计 FIFO 中的最大页面事件数。

· **maxTimeMsToFlush\_Portlet**：Portlet 统计信息 FIFO 的 FIFO 刷新之间的最大时间长度。

· **maxTimeMsToFlush\_User**：用户统计信息 FIFO 的 FIFO 刷新之间的最大时间长度。

· **maxTimeMsToFlush\_Page**：页面统计信息 FIFO 的 FIFO 刷新之间的最大时间长度。

· **jetspeedDSEntry**：对 Jetspeed 数据源的引用。

FIFO 参数可以根据站点的具体需要进行调整。例如，调整事件和时间可以降低系统在发生故障时丢失事件的可能性，并且还可以使查看统计数据的用户体验对最近的事件更加敏感。另一方面，将它们调高将减少数据库的开销。一般来说，用户较少的较新站点应使用较小的调整参数，而较大的较成熟的站点应使用较大的参数。

下面提供了一个示例配置：

<bean id="门户统计"

  class="org.apache.jetspeed.statistics.impl.PortalStatisticsImpl"

  初始化方法="springInit"

  destroy-method="springDestroy">

  <!-- logToCLF -->

  <constructor-arg index='0' type="boolean"><value>false</value></constructor-arg>

  <!-- logToDatabase -->

  <constructor-arg index='1' type="boolean"><value>true</value></constructor-arg>

  <!-- maxRecordToFlush_Portal -->

  <constructor-arg index='2'><value>300</value></constructor-arg>

  <!-- maxRecordToFlush_User -->

  <constructor-arg index='3'><value>50</value></constructor-arg>

  <!-- maxRecordToFlush_Page -->

  <constructor-arg index='4'><value>100</value></constructor-arg>

  <!-- maxTimeMsToFlush_Portal -->

  <constructor-arg index='5'><value>300000</value></constructor-arg>	

  <!-- maxTimeMsToFlush_User -->

  <constructor-arg index='6'><value>5000</value></constructor-arg>

  <!-- maxTimeMsToFlush_Page -->

  <constructor-arg index='7><value>60000</value></constructor-arg>

  <!-- jetspeedDSEntry -->

  <constructor-arg index='8'><ref bean="JetspeedDS"/></constructor-arg>

</豆>
#### 3.2.4.3. **查看统计信息**

##### 3.2.4.3.1. **事件记录在哪里？**

门户统计事件收集在门户引擎中的多个点注入。下面提供了一些示例。

对于用户事件，将**SecurityValveImpl**用户登录事件记录在**getSubject(RequestContext request)**.

statistics.logUserLogin（请求，0）；
对于 portlet 事件，**RenderingJobImpl**调用的 in**RenderingJobbuildRenderingJob**记录一个 portlet 访问事件。

statistics.logPortletAccess(requestContext, fragment.getName(), PortalStatistics.HTTP_OK, end - start);
#### 3.2.4.4. **数据聚合概述**

Jetspeed-2 提供了一种汇总门户统计数据以进行报告的机制。

##### 3.2.4.4.1. **检索汇总统计信息**

该**PortalStatistics**组件公开了一个**queryStatistics**给定 a **StatisticsQueryCriteria**will return的方法**AggregateStatistics**。

AggregateStatistics queryStatistics(StatisticsQueryCriteria 标准)
然后**AggregateStatistics**可以将其用于报告目的。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps54.png)

##### 3.2.4.4.2. **使用聚合统计**

如[查看统计信息](https://portals.apache.org/jetspeed-2/adminguide/statistics.html)中所示，Jetspeed-2 为查看统计信息提供了一个默认的报告 portlet。要查询统计信息，**StatisticsQueryCriteria**必须设置 a。根据此标准，该**PortalStatisticsqueryStatistics()**方法将返回一个**AggregateStatistics**.

    StatisticsQueryCriteria 标准 = statistics.createStatisticsQueryCriteria();

    ...

    标准.setUser（用户）；

    标准.setListsize("5");

    criteria.setSorttype("count");

    标准.setSortorder("desc");

    标准.setTimePeriod（时间段）；

    条件.setQueryType(queryType);

    AggregateStatistics stats = statistics.getDefaultEmptyAggregateStatistics();

    ...

    统计.forceFlush();

    stats = statistics.queryStatistics（标准）；
### 3.2.5. [**本土化**](https://portals.apache.org/jetspeed-2/devguide/guide-l10n.html)

Jetspeed2 在 Java 属性和 XML 文件中具有可翻译的消息

#### 3.2.5.1. **属性文件**

本文档展示了如何为您的语言创建消息属性文件。

###### 3.2.5.1.0.1. **寻找****\*\_en.properties**

**\*\_en.properties**是英文消息属性文件。您可以将其用作您的语言的基本属性文件。

如果使用 UNIX 系统，可以使用**find**命令查找属性文件：

$ cd ${jetspeed-2-home}

$查找。-类型 f | grep -v CVS | grep _en.properties

###### 3.2.5.1.0.2. **复制****\*\_en.properties****到****\*\_<your language, [country and variant]>.properties.orig**

要翻译消息，请复制您的语言的属性文件。有关语言、国家和变体代码的更多信息，请参阅“ [JavaDoc：语言环境类](http://java.sun.com/j2se/1.4.2/docs/api/java/util/Locale.html)”、“ [ISO 语言代码](http://www.ics.uci.edu/pub/ietf/http/related/iso639.txt)”和“ [ISO 国家代码](http://www.chemie.fu-berlin.de/diverse/doc/ISO_3166.html)”。

例子：

$ cd applications/localeselector/src/java/org/apache/jetspeed/portlets/localeselector/resources/

$ cp LocaleSelectorResources_en.properties LocaleSelectorResources_ja.properties.orig

**\*\_ja.properties**日语消息文件 在哪里。

###### 3.2.5.1.0.3. **将 \*\_<您的语言，[国家和变体]>.properties.orig 翻译成您的语言**

有关属性文件的更多信息，请参阅“ [JavaDoc：属性类](#load(java.io.InputStream))”。

###### 3.2.5.1.0.4. **运行**native2ascii**命令**

由于假定属性文件使用 ISO 8859-1 字符编码，因此使用**native2ascii**命令转换为 ISO 8859-1。有关“ [native2ascii(Solaris)](http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/native2ascii.html) ”或“ [native2ascii(Windows)](http://java.sun.com/j2se/1.4.2/docs/tooldocs/windows/native2ascii.html) ”的更多信息。

例子：

$ native2ascii LocaleSelectorResources_ja.properties.orig LocaleSelectorResources_ja.properties

###### 3.2.5.1.0.5. **Build & Deploy Jetspeed2，看看你的翻译是否显示**

有关 Jetspeed 2 构建和部署步骤的更多信息，请参阅“[入门](https://portals.apache.org/jetspeed-2/getting-started.html)”。

###### 3.2.5.1.0.6. **新建一个JIRA issue，并附上****\*\_<your language, [country and variant]>.properties**

Jetspeed 2 的 JIRA 站点是[http://issues.apache.org/jira/secure/BrowseProject.jspa?id=10492](http://issues.apache.org/jira/secure/BrowseProject.jspa?id=10492)。要创建新的 JIRA 问题，请转到“创建新问题”（选择“l10n”作为组件名称）。

### 3.2.6. [**管道**](https://portals.apache.org/jetspeed-2/devguide/guide-pipeline.html)

如下所述，Jetspeed-2 门户引擎的关键组件之一是其请求管道。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps55.png)

在Jetspeed-2 中，请求是通过一系列**Valve**组装在一起的管道来处理的。

#### 3.2.6.1. **请求管道**

在 Jetspeed-2 中，请求管道对请求执行单独的操作。

##### 3.2.6.1.1. **管道概念**

A**Pipeline**是由**Valves**链式组成的链式责任模式。该**JetspeedPipeline**实现组装了**Valves**按顺序处理的有序列表。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps56.png)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps57.png)

##### 3.2.6.1.2. **Jetspeed-2 阀门**

**Valve**Jetspeed-2 提供如下所示的 各种类型：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps58.png)

上述阀门用于以下用途：


| **阀门名称** | **描述**                                                                              |
| ------------ | ------------------------------------------------------------------------------------- |
| 动作阀       | 检查是否**PortletAction**需要处理并在需要时进行处理。在portlet管道中使用。            |
| 集料阀       | 在渲染模式下调用所有Layout组件来聚合生成的内容并将结果发送给客户端。                  |
| 能力阀       | 标识浏览器并**CapabilityMap**在**RequestContext**.                                    |
| 清理阀       | 查找推送到**org.apache.jetspeed.renderStack** 请求属性的 JSP 页面，并尝试包含它们。   |
| 登录验证阀   | 检查登录尝试是否失败并确定原因。                                                      |
| 密码凭证阀   | 用户登录后检查PasswordCredential（仅一次），并在必要时重定向到更改密码页面。          |
| 安全阀       | 必要时对用户进行身份验证或重定向到登录，将经过身份验证的主题添加到**RequestContext**. |

### 3.2.7. [**优先**](https://portals.apache.org/jetspeed-2/devguide/dev-prefs.html)

[java.util.prefs.Preferences API](http://java.sun.com/j2se/1.4.2/docs/api/java/util/prefs/Preferences.html)提供 了 一种通用机制来存储用户和系统首选项以及配置数据。Jetspeed 2 依靠此 API 为更高级别的服务提供广泛的功能。一些利用 **java.util.prefs.Preferences** API 的 Jetspeed 组件包括：

· Portlet 首选项：Portlet 首选项存储在系统首选项树中。以下路径结构用于确定给定 portlet 首选项在首选项树中的位置： **/portlet\_application/\${Portlet Application Name}/portlets/\${Portlet Name}/preferences/\${Preference Name}/values** . **values** 偏好值作为键/值映射 存储在 节点下。

· 用户属性：用户属性存储在用户偏好树中，如下所示。以下路径结构用于存储用户的属性： **/user/\${User Name}/userinfo** . 用户属性存储为 userinfo 节点下的首选项键/值映射。

· 角色和组层次结构：关于角色和组层次结构如何使用 **Preferences** 模型的文档可以在文档的 [安全部分](#Leveraging_Preferences_to_Manage_Hierarchies) 中找到。

#### 3.2.7.1. **偏好目标**

*Preferences* API 提供了用于组织属性 的通用实现，如下所示：

<首选项EXTERNAL_XML_VERSION="1.0">

<root type="用户">

<地图/>

<节点名称="用户">

<地图/>

<节点名称="principal1">

  <地图/>

<节点名称="propertyset1">

  <地图>

    <entry key="set1prop1" value="256" />

    <entry key="set1prop2" value="314" />

  </地图>

</节点>
</节点>

</root>

可以在[ ONJava.com](http://www.onjava.com/pub/a/onjava/synd/2001/10/17/j2se.html)上找到一篇很好的参考文章。

#### 3.2.7.2. **首选项实施概述**

Jetspeed 2 **Preferences** 实施利用以下类：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps59.png)


| **班级**                   | **描述**                                                                                                                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **PreferencesFactoryImpl** | 实现**java.util.prefs.PreferencesFactory**生成 **Preferences**对象的。它**PreferencesFactoryImpl**通过弹簧组件(**prefs.xml**)配置为使用 **PreferencesProvider**封装后备存储实现的 。                                    |
| **PreferencesImpl**        | **java.util.prefs.AbstractPreferences**通过利用**PreferencesProvider**API扩展和实现 SPI。Jetspeed**Preferences** 实现可以配置为验证是否为预定义的键创建了首选项映射键/值。**PropertyManager**如果启用，A会强制执行检查。 |
| **PreferencesProvider**    | 再次将首选项实现封装到特定的后备存储。在Jetspeed 2中，默认实现由**org.apache.jetspeed.prefs.impl.PersistenceBrokerPreferencesProvider**                                                                                  |

#### 3.2.7.3. **首选项数据库架构**

Jetspeed 2 中使用以下数据库模式来存储**Preferences** 关系数据库模型。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps60.png)

### 3.2.8. [**探查器**](https://portals.apache.org/jetspeed-2/devguide/guide-profiler.html)

Jetspeed Profiler 是一个基于门户资源定位规则的引擎。探查器定位以下类型的门户资源：

· PSML 页面

· 文件夹

· 菜单

· 链接

当门户收到请求时，分析器将计算一个规范化的指令集，称为配置文件定位器。然后将定位器添加到请求上下文中，Jetspeed 管道上的后续组件，尤其是页面管理器和门户站点组件，可以从中获取配置文件定位器并使用它来查找请求的资源。例如，页面管理器使用定位器来查找页面或文件夹。Portal Site 组件使用定位器在菜单上构建选项。

配置文件定位器是分析器的输出。输入是一组标准化的运行时参数和状态。分析器输入在分析规则中定义，并且可以由管道上可用的任何 Java 类组成。Jetspeed 带有相当多的预定义规则，用于从请求参数、HTTP 标头、安全信息、语言和会话属性中获取标准。在分析器阀中的 Jetspeed 请求处理管道期间调用分析器。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps61.png)

所有这些运行时参数都称为*配置文件标准*，分析器使用它来定位门户资源。

#### 3.2.8.1. **定位门户资源：页面**

Profiler 搜索 PSML 页面的目录树，试图找到要显示的 PSML 页面。默认情况下，此目录结构位于 WEB-INF/pages 下。pages 目录也可以存储在数据库中。该目录结构由门户资源（页面、文件夹、菜单、链接）组成，是门户站点的*物理*表示。Jetspeed 团队还计划在未来版本中支持门户网站的*逻辑*视图。

类似于文件系统，门户站点有一个物理根。但是，使用*子*站点的概念，Jetspeed 站点可以支持对其他子站点或主站点不可见的整个子站点。探查器标准化了几个保留（系统）目录：


| **保留文件夹** | **描述**                         |
| -------------- | -------------------------------- |
| \_用户         | 保存所有用户特定的文件夹和页面   |
| \_角色         | 保存所有按角色组织的文件夹和页面 |
| \_团体         | 保存所有按组组织的文件夹和页面   |
| \_subsite-root | 包含完整的子站点树，就像根树一样 |

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps62.png)

通过应用分析规则，分析器在门户网站目录中定位页面。

#### 3.2.8.2. **分析规则**

ProfilingRule 定义了在评估请求以确定特定资源的位置时使用的标准列表。剖析器使用剖析规则根据已知 Portlet 请求数据的解耦标准定位门户资源。规则由应按给定顺序应用的标准的有序列表组成。按照此规则的顺序，分析引擎使用不太具体的算法应用规则的每个标准，直到考虑到最不具体的资源标准。当所有条件都用尽时，规则将失败并且需要备用资源。

规则标准

规则标准指定分析规则标准列表中的一个标准。该规则用于构建规范化分析定位器，然后根据当前用户请求定位门户资源。规则标准是用于定位配置文件属性的模板。标准包括：


| 类型                 | 标准的类型。类型在分析器弹簧配置中配置。每种类型都映射到一个*规则标准解析器*。解析器是一个Java类，它将请求输入映射到规范化的位置指令。下表提供了有效的解析器。 |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 后备顺序             | 在分析规则中应用此标准的顺序。                                                                                                                                 |
| 回退类型             | 在评估此标准后，该规则可以继续处理剩余的标准，或停止处理。回退类型决定如何继续处理。有效值为：                                                                 |
| -------------------- | --------------------------------------------                                                                                                                   |
| FALLBACK\_STOP       | 评估此标准，如果失败则停止此规则的评估标准                                                                                                                     |
| FALLBACK\_LOOP       | 评估此标准，如果失败则继续评估                                                                                                                                 |

|
| 姓名     | 此标准的唯一名称（每个规则）。匹配后，名称将映射到配置文件定位器属性名称。                                                                                                                                                                                                       |
| 价值     | 解析失败时用于此标准的默认值（非必需）。                                                                                                                                                                                                                                         |

更复杂的实现将需要使用其他输入来映射到 Cookie、IP 地址范围、统计资源使用分析或业务规则等资源。

##### 3.2.8.2.1. **规则标准解析器**

下表显示了 Jetspeed 开箱即用的所有默认规则标准解析器。解析器是 Java 类，实现来自 Jetspeed API org.apache.jetspeed.profiler.rules.RuleCriterionResolver的接口。您可以使用这组默认的解析器来构建您自己的分析规则。规则当前存储在 Jetspeed 数据库中。门户管理员可以使用管理 portlet 编辑规则。在演示系统中，以用户“admin”的身份登录以查看 Jetspeed Profiler Administration portlet 的示例。

此外，您可以将自己的解析器添加到 Jetspeed。您需要创建一个包含自定义解析器的 jar 文件，然后将它们放入 Jetspeed webapp 的类路径中。解析器需要有一个唯一的名称。这是通过修改 Spring 程序集中的 profiler.xml 来完成的。请参阅下面有关配置的部分，以了解将解析器添加到 Spring 配置的位置。


| **解析器**      | **描述**                                                                                                                                                                                                                                         |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 要求            | 通过按名称匹配请求参数来解析，返回采用条件名称的定位器属性的请求参数值                                                                                                                                                                           |
| 会议            | 通过按名称匹配会话属性来解析，返回采用标准名称的定位器属性的会话属性值                                                                                                                                                                           |
| 请求会话        | 通过首先按名称匹配请求参数来解决。如果不匹配，请尝试匹配会话属性名称，返回请求参数或会话属性值，以获取采用标准名称的定位器属性                                                                                                                   |
| 小路            | 通过匹配当前请求的PSML页面*路径*值来解决。路径通常是页面的路径和名称，例如名为*default-page*的定位器属性小路                                                                                                                                     |
| 路径.会话       | 通过匹配当前请求的PSML页面*路径*值来解决。路径通常是页面的路径和名称，例如*default-page*。如果未能在请求中找到有效路径，则将在会话中查找页面值。定位器属性将被命名小路                                                                           |
| 硬编码          | 解析为硬编码的默认值，例如，将名为page的定位器属性设置为/my-account.psml                                                                                                                                                                         |
| 用户            | 通过匹配当前经过身份验证的用户的名称来解决。用户名映射到名为的定位器属性用户                                                                                                                                                                     |
| 角色            | 通过匹配当前已验证用户的所有安全角色（在请求上下文的JAAS主题中）并将它们放在逗号分隔的列表中来解决。定位器属性应命名为角色. 角色标准通常与路径标准结合使用，以创建搜索给定用户的所有安全角色的角色回退规则。                                    |
| 团体            | 通过匹配当前已验证用户的所有组（在请求上下文的JAAS主题中）并将它们放在逗号分隔的列表中来解决。定位器属性应命名为团体. 组标准通常与路径标准结合使用，以创建搜索给定用户的所有安全组的组回退规则。                                                |
| 角色组合        | 通过匹配当前已验证用户的所有安全角色（在请求上下文的JAAS主题中）并将它们放在一个破折号分隔的字符串中来解决，例如：(role1-role2-role3)。定位器属性应命名为角色. 角色标准通常与路径标准结合使用，以创建搜索给定用户的所有安全角色的角色回退规则。 |
| 媒体类型        | 通过匹配请求上下文中的媒体类型（HTML、XHTML、WML...）来解决。设置一个名为的定位器属性媒体类型                                                                                                                                                    |
| 语言            | 通过匹配请求上下文语言环境中的浏览器语言（源自HTML标头）来解决。设置一个名为的定位器属性语言                                                                                                                                                     |
| 国家            | 通过匹配来自请求上下文语言环境的浏览器的国家/地区代码（源自 HTML 标头）来解决。设置一个名为的定位器属性国家                                                                                                                                      |
| group.role.user | 通过首先匹配名为的请求参数来解决团体.如果失败，请在名为的请求参数上解析角色. 如果失败，请通过匹配当前经过身份验证的用户的名称来解决。用户名映射到名为的定位器属性用户                                                                           |
| 用户属性        | 通过按名称匹配Portlet API用户属性来解析，返回采用标准名称的定位器属性的用户属性值                                                                                                                                                                |
| 用户代理        | 通过从请求上下文设备功能（源自HTML标头）中匹配浏览器的（客户端）用户代理来解决                                                                                                                                                                   |
| 主机名          | 通过匹配请求中的服务器名中的主机名来解析，返回主机名                                                                                                                                                                                             |
| 领域            | 通过匹配请求中服务器名称的域来解析，返回域                                                                                                                                                                                                       |
| 导航            | 在页面管理器执行的配置文件位置解析期间更改当前导航路径的指令。该值可以是文件夹的位置，例如/pages/免费内容                                                                                                                                        |

*请注意，当没有匹配时，所有条件都将回退到默认值。定位器属性需要一个名为导航*

##### 3.2.8.2.2. **默认规则**

Jetspeed 系统默认提供了几条规则。下表中的规则以最具体到最不具体的顺序显示标准。


| **规则**          | **描述**                                                               |
| ----------------- | ---------------------------------------------------------------------- |
| j1                | 实现Jetspeed-1硬编码分析器后备算法，以最具体到最不具体的算法进行解析： |
| ----------------- | --------------                                                         |
| 国家              | 国家                                                                   |
| 语言              | 语言                                                                   |
| 媒体类型          | 媒体类型                                                               |
| group.role.user   | 用户                                                                   |
| 路径.会话         | 页                                                                     |

                                                                                                                                                                |
| 角色回退           | 基于角色的回退算法，试图通过搜索当前经过身份验证的用户的所有安全角色来找到最具体的资源。| **标准** | **姓名** | **价值** | **倒退** |
| ----------- | ----------- | ----------- | ----------- |
| 路径.会话 | 页        | 默认页面  | 停止      |
| 角色      | 角色      |           | 继续      |

                                                                                                                                                                                                                                              |
| 组回退             | 一种基于组的回退算法，试图通过在所有安全组中搜索当前经过身份验证的用户来找到最具体的资源。| **标准** | **姓名** | **价值** | **倒退** |
| ----------- | ----------- | ----------- | ----------- |
| 路径.会话 | 页        | 默认页面  | 停止      |
| 团体      | 团体      |           | 继续      |

                                                                                                                                                                                                                                            |
| j2                 | 用户和媒体类型减去语言和国家/地区的默认分析规则。| **标准**       | **姓名**    | **价值** | **倒退** |
| ----------------- | -------------- | ----------- | ----------- |
| 媒体类型        | 媒体类型     |           | 继续      |
| group.role.user | 用户|组|角色 |           | 停止      |
| 路径.会话       | 页           | 默认页面  | 停止      |

                                                                                                                                                                                                                                   |
| 安全               | 强制凭证更改要求所需的安全分析规则。| **标准** | **姓名** | **价值**        | **倒退** |
| ----------- | ----------- | ------------------ | ----------- |
| 硬编码    | 页        | /my-account.psml | 停止      |

                                                                                                                                                                                                                                                                                                                    |
| 小路               | 唯一应用的标准是门户URL的路径部分。| **标准** | **姓名** | **价值** | **倒退** |
| ----------- | ----------- | ----------- | ----------- |
| 小路      | 页        | /         | 停止      |

                                                                                                                                                                                                                                                                                                                                      |
| 用户角色回退       | Rule将首先在用户的主文件夹中查找资源。如果在那里找不到，则应用基于角色的回退算法，尝试通过搜索当前经过身份验证的用户的所有安全角色来找到最具体的资源。| **标准** | **姓名** | **价值** | **倒退** |
| ----------- | ----------- | ----------- | ----------- |
| 路径.会话 | 页        | 默认页面  | 继续      |
| 角色      | 角色      |           | 继续      |
| 导航      | 导航      | /         | 环形      |
| 用户      | 用户      |           | 继续      |

                                                                                                                                  |
| 用户角色组合后备   | Rule将首先在用户的主文件夹中查找资源。如果在那里找不到，则应用基于角色的回退算法，尝试通过搜索当前经过身份验证的用户的所有安全角色来找到最具体的资源。创建一个名为的定位器属性角色也就是将所有角色串联成一个字符串，例如*role1-role2-role3*。此组合字符串用作定位器中的角色名称。| **标准** | **姓名** | **价值** | **倒退** |
| ----------- | ----------- | ----------- | ----------- |
| 路径.会话 | 页        | 默认页面  | 继续      |
| 角色组合  | 角色      |           | 继续      |
| 导航      | 导航      | /         | 环形      |
| 用户      | 用户      |           | 继续      |

|
| 子站点角色后备主页 | 具有指定子站点和主页的基于角色回退算法的规则| **标准** | **姓名** | **价值**      | **倒退** |
| ----------- | ----------- | ---------------- | ----------- |
| 小路      | 小路      | 子站点默认页面 | 停止      |
| 角色      | 角色      |                | 继续      |
| 导航      | 导航      | 子站点根       | 环形      |

                                                                                                                                                                                                                                                         |
#### 3.2.8.3. **个人资料定位器**

配置文件定位器用于定位配置文件的门户资源，例如页面、文件夹、菜单和链接。定位器包含一组描述要定位的实际资源的属性（名称值对）。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps63.png)

分析器将运行时信息作为输入，概括为通用配置文件定位器，这些定位器被传递给页面管理器以定位页面或菜单。配置文件定位器被规范化并且不耦合到分析器或页面管理器实现。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps64.png)

#### 3.2.8.4. **主要规则**

每个用户主体都可以映射到特定的分析规则。此关联存储在 Jetspeed 数据库中。关联是三向的，结合了 PRINCIPAL + PROFILING RULE + LOCATOR，其中目前支持的 locator 值为菜单或者页. 因此，我们可以应用两种不同的分析规则来为每个用户定位资源：定位页面和定位菜单。当分析器尝试为当前用户定位页面时，它将为给定用户应用分析规则。Jetspeed 用户管理 portlet 有一个用于编辑用户配置文件信息的选项卡：

通常，在用户注册（或自注册）期间，分析规则由特定于门户的逻辑确定并关联。Jetspeed 特定的自注册 Portlet 可以处理向系统添加用户、授予角色、设置用户属性和为用户分配概要分析规则的注册过程。

### 3.2.9. [**探查器 IP**](https://portals.apache.org/jetspeed-2/devguide/guide-profiling-ip.html)

Jetspeed 有一个内置机制，可以为特定 IP 地址提供自定义内容。此功能使用 Profiler 根据请求的客户端 IP 地址来协商页面。

#### 3.2.9.1. **1. 规则**

该规则由键ip-address标识。使用 IP 标准解析器有一个称为ip解析的标准。此类实现 Rule Criterion Resolver 的 resolve 方法，以便从请求中获取 IP 地址。

公共字符串解析（RequestContext 上下文，RuleCriterion 标准）

{

    // 寻找覆盖

    字符串值 = super.resolve（上下文，标准）；

    if (value != null) { return value.toLowerCase(); }

    // 注意 IP 地址可能因客户端而异

    // Konqueror 3.4.2 返回 IPv6 例如 0:0:0:0:0:0:0:1

    // Firefox 1.0.7 返回 IPv4 例如 127.0.0.1

    // 这是用于解析_ip目录中的页面的值

    // TODO 创建一个将所有 IPv4 地址转换为 IPv6 的选项

    返回 context.getRequest().getRemoteAddr();

}
#### 3.2.9.2. **2.页面定位器**

将此配置文件规则设置为**页面**定位器的用户将获得来自 psml 站点树的 _ip 目录的页面。例如，如果从 81.29.65.234 向 http://www.apache.org/jetspeed/portal/default-page.psml 发出请求，则规则将匹配 /WEB-INF/pages/_ip/81.29.65.234/default -page.psml 在回退到 /WEB-INF/pages/default-page.psml 之前

#### 3.2.9.3. **3. 示例用例**

您在东京有一个位置，提供特定于该位置的内容。您的信息亭配置有固定 IP 地址。匿名用户（默认为访客）使用此配置文件规则。从该信息亭使用门户的任何人都将获得 _ip 目录中的内容。

它也可以用来分析机器人。或将不受欢迎的访客拒之门外。并且可以作为分析 IP 范围或 IP 前缀、网络和子网以及地理位置的基础。

### 3.2.10. [**PSML**](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)

· [页](#Page)

o [布局片段](#Layout_Fragments)

o [Portlet 片段](#Portlet_Fragments)

o [片段参考](#Fragment_References)

o [片段属性](#Fragment_Properties)

o [Portlet 首选项](#Preferences)

· [动态页面](#Dynamic_Page)

· [页面模板](#Page_Template)

o [页面片段](#Page_Fragment)

· [片段定义](#Fragment_Definition)

· [文件夹](#Folder)

· [关联](#Link)

· [全局页面安全](#Global_Page_Security)

· [标题和元数据](#PSML_Titles_and_Metadata)

· [默认值](#PSML_Defaults)

· [安全约束](#PSML_Security_Constraints)

· [菜单](#PSML_Menus)

· [PSML 文档 XML 模式](https://portals.apache.org/jetspeed-2/devguide/guide-psml-xsd.html)

PSML 是门户结构标记语言的首字母缩写词。创建它是为了允许在 Jetspeed 中进行内容结构和抽象。PSML 定义了如何在门户页面上聚合、布局和修饰 portlet。请注意，页面布局不是 Java Portlet 标准 API 的一部分。因此，PSML 是 Jetspeed 特定的实现。另请注意，Jetspeed-2 中的 PSML 与 Jetspeed-1 中的 PSML 不同。本文档可用作 PSML 资源元素的参考指南。

PSML 文件捕获与门户的页面、文件夹、链接和全局安全约束相关的门户站点信息。PSML 元素可以在文件系统中的目录层次结构中排列的单独文档中定义。PSML 文档的文件夹结构反映了门户 URL 空间。通常，PSML 根目录作为资源访问，位于 jetspeed Web 应用程序中的 /WEB-INF/pages。也可以将 PSML 定义存储在数据库中；PSML 层次结构的文件夹和文档排列也保留在那里。

以下 PSML 文档/元素定义如下：

从外部定义要从多个页面或页面模板引用的片段。片段引用用于引用片段定义。片段定义不能包含对其他片段定义的引用。每个文件夹只能为每个片段 ID 定义一个片段定义。


| **PSML 元素**                       | **文档**      | **描述**                                                                                                                                                                                                                                                         |
| ------------------------------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [页](#Page)                           | \*.psml       | 在特定门户URL处定义门户内的单个门户页面。如果在当前文件夹或父文件夹中找到页面模板，页面定义将被扩充。页面主要由映射到各个 portlet 的片段组成。页面还可以包含对单独定义的片段引用的片段引用。                                                                     |
| [动态页面](#Dynamic_Page)             | \*.dpsml      | 定义与门户内的匹配内容URL一起使用的可重用门户页面。与页面定义一样，动态页面将通过页面模板进行扩充，并由片段和片段引用组成。动态页面通过 URL 和内容类型映射匹配到门户内容页面请求：匹配页面从当前或父文件夹中选择。每个文件夹只能为每种内容类型定义一个动态页面。 |
| [页面模板](#Page_Template)            | \*.tpsml      | 定义要包含在所有具体和动态页面中的片段和片段引用。从当前页面或父文件夹中选择单个页面模板。一个特殊的页面片段用于定义页面模板中当前页面片段的插入位置。每个文件夹只能定义一个页面模板。                                                                           |
| [片段定义](#Fragment_Definition)      | \*.fpsml      |                                                                                                                                                                                                                                                                  |
| [文件夹](#Folder)                     | 文件夹.元数据 | 定义与文件系统文件夹或URL路径关联的元数据。正如人们所期望的，只有一组元数据信息可以与文件夹相关联。除了内容 URL，由文件夹和页面定义的层次结构定义了门户 URL 空间。                                                                                               |
| [关联](#Link)                         | \*。关联      | 定义门户菜单中使用的外部或本地资源的URL链接。                                                                                                                                                                                                                    |
| [全局页面安全](#Global_Page_Security) | 页面安全      | 为所有门户页面和文件夹定义全局安全约束定义和默认值。                                                                                                                                                                                                             |

以下是门户网站[页面](#Page)的示例 PSML 文件(*.psml)：

<?xml 版本="1.0" 编码="UTF-8"?>

<页面>

<!-- 页面信息 -->

<title>欢迎来到 Jetspeed 2</title>

<metadata name="title" xml:lang="fr">Ma Premiere Page de PSML</metadata>

<metadata name="title" xml:lang="es">¡Bienvenido a Jetspeed 2!</metadata>

<metadata name="title" xml:lang="hu">Köszönti a Jetspeed 2!</metadata>

<!-- 页面装饰 -->

<defaults skin="orange" layout-decorator="tigris" portlet-decorator="tigris"/>

<!-- 页面片段 -->

<fragment id="100393" type="layout" name="jetspeed-layouts::VelocityOneColumn">

<fragment id="100939" type="portlet" name="j2-admin::LocaleSelector">

  <属性名称=“行”值=“0”/>

</片段>                                

<fragment id="100345" type="layout" name="jetspeed-layouts::VelocityTwoColumns">

  <property name="row" value="1"/>

  <property name="sizes" value="33%,66%"/>

  <fragment id="100121" type="portlet" name="j2-admin::LoginPortlet">

    <属性名称=“行”值=“0”/>

    <property name="column" value="0"/>

  </片段>                                

  <fragment id="100171" type="portlet" name="demo::UserInfoTest">

    <属性名称=“行”值=“0”/>

    <property name="column" value="1"/>

  </片段>    

</片段>
</片段>

<!-- 安全约束 -->

<安全约束>

<security-constraints-ref>公共视图</security-constraints-ref>
</安全约束>

</页面>

以下是门户网站[动态页面](#Dynamic_Page)(\*.dpsml) 的示例 PSML 文件：

<?xml 版本="1.0" 编码="UTF-8"?>

<dynamic-page content-type="*" 可继承="true">

<title>Jetspeed 2 门户内容</title>

<fragment id="default-content-layout" type="layout" name="jetspeed-layouts::VelocityTwoColumns">

<property name="sizes" value="80%,20%" />

<fragment id="default-content-dynamic-content" type="portlet" name="j2-admin::DynamicWebContentPortlet" decorator="gray-gradient-noborder">

  <属性名称="行" 值="0" />

  <property name="column" value="0" />

  <preference name="SRC">

    <value>http://portals.apache.org/</value>

  </偏好>

  <preference name="PORTALPATH">

    <值>/内容/</值>

  </偏好>

</片段>

<fragment-reference id="default-content-wp-reference" refid="wp-definition">

    <属性名称=“行”值=“0”/>

    <property name="column" value="1"/>

</片段参考>
</片段>

</动态页面>

以下是门户网站[页面模板](#Page_Template)(\*.tpsml) 的示例 PSML 文件：

<?xml 版本="1.0" 编码="UTF-8"?>

<页面模板>

<title>门户模板</title>

<fragment id="template-top" type="layout" name="jetspeed-layouts::VelocityOneColumn">

<page-fragment id="template-top-page-template">

  <属性名称=“行”值=“0”/>

</page-fragment>

<fragment id="template-top-login" type="portlet" name="j2-admin::LoginPortlet">

  <property name="row" value="1"/>

</片段>                                

<fragment-reference id="template-top-wp-reference" refid="wp-definition">

  <property name="row" value="2"/>

</片段参考>
</片段>

</page-template>

这是门户网站[片段定义](#Fragment_Definition)的示例 PSML 文件(*.fpsml)：

<?xml 版本="1.0" 编码="UTF-8"?>

<片段定义>

<title>当前天气</title>

<fragment id="wp-definition" type="portlet" name="demo::WeatherPortlet"/>

</片段定义>

下面是一个定义门户站点[文件夹](#Folder)的示例 PSML 文件(folder.metadata)：

<?xml 版本="1.0" 编码="UTF-8"?>

<文件夹>

<!-- 文件夹说明 -->

<title>根文件夹</title>

<metadata name="title" xml:lang="fr">Répertoire racine</metadata>

<metadata name="title" xml:lang="es">地毯 raiz</metadata>

<!-- 默认页面装饰 -->

<defaults layout-decorator="tigris" portlet-decorator="tigris"/>

<!-- 文件夹中文件的顺序 -->

<document-order>Jetspeed2.link</document-order>

<document-order>Jetspeed2Wiki.link</document-order>

<document-order>apache_portals.link</document-order>

<document-order>apache.link</document-order>

<!-- 门户网站菜单 -->

<菜单名称="页面导航">

<分隔符>

  <text>首页</text>

  <metadata name="text" xml:lang="fr">Page haut</metadata>

  <metadata name="text" xml:lang="es">流行页面</metadata>

</分隔符>

<options>/管理性</options>

<分隔符>

  <text>简介页面</text>

  <metadata name="text" xml:lang="es">Páginas del Perfil</metadata>

</分隔符>

<options regexp="true">/p[0-9][0-9][0-9].psml</options>

<分隔符>

  <text>非 Java 页面</text>

  <metadata name="text" xml:lang="es">Ejemplos sin java</metadata>

</分隔符>

<options>/非java</options>
</菜单>

<!-- 安全约束 -->

<安全约束>

<security-constraints-ref>公共视图</security-constraints-ref>
</安全约束>

</文件夹>

以下是门户网站[链接](#Link)(\*.link) 的示例 PSML 文件：

<?xml 版本="1.0" 编码="UTF-8"?>

<链接目标=“顶部”>

<!-- 链接说明 -->

<title>Jetspeed 2 主页</title>

<url>http://portals.apache.org/jetspeed-2/</url>

<metadata name="title" xml:lang="es">Jetspeed 2</metadata>

</链接>

这是门户网站[页面安全性](#Global_Page_Security)(page.security) 的示例 PSML 文件：

<?xml 版本="1.0" 编码="UTF-8"?>

<页面安全>

<!-- 全局管理约束 -->

<security-constraints-def name="admin">

<安全约束>

  <角色>管理员</角色>

  <permissions>查看、编辑</permissions>

</安全约束>
</security-constraints-def>

<global-security-constraints-ref>admin</global-security-constraints-ref>

<!-- 公共约束 -->

<security-constraints-def name="public-view">

<安全约束>

  <用户>*</用户>

  <permissions>查看</permissions>

</安全约束>
</security-constraints-def>

<security-constraints-def name="public-edit">

<安全约束>

  <用户>*</用户>

  <permissions>查看、编辑</permissions>

</安全约束>
</security-constraints-def>

</page-security>

#### 3.2.10.1. **页**

<page> 元素是一个简单的容器，用于保存与门户网站页面关联的其他 PSML 元素。此元素作为扩展名为“.psml”的文件保存在与父[文件夹](#Folder)关联的相应文件系统目录中。页面元素有两个有效属性：


| **属性** | **描述**                                                           |
| -------- | ------------------------------------------------------------------ |
| 隐       | 一个布尔属性，用于指示页面不应出现在门户网站菜单或其他导航元素中。 |
| 版本     | 通用版本跟踪属性。Jetspeed2目前不使用。                            |

<page> 元素包含许多其他 PSML 元素：


| **元素**                               | **描述**                                                                                                                                                                                    |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 标题？                                   | 包含默认页面标题文本的简单元素。页面的标题被认为是它的长描述，并且如果短标题可用于菜单文本，则在某些装饰器中用作翻转文本。如果未指定，Jetspeed2将尝试从包含页面元素的文件的名称中定义标题。 |
| 短标题？                                 | 可选的简单元素，包含页面默认短标题的文本。短标题（如果可用）在某些装饰器中用作菜单文本。如果未指定，则使用标题文本。                                                                        |
| [默认值？](#PSML_Defaults)               | 指定页面及其片段的装饰。可选的默认值可以从父文件夹继承，但每个页面都需要布局装饰，无论是明确指定还是在父文件夹中。                                                                          |
| [分段](#Layout_Fragments)                | 片段层次结构的根。所有页面都需要一个根片段。                                                                                                                                                |
| [元数据](#PSML_Titles_and_Metadata)\*    | （可选）指定页面的区域设置特定标题和短标题。                                                                                                                                                |
| [菜单](#Menus)\*                         | 可选地为页面指定附加的或覆盖继承的菜单定义。                                                                                                                                                |
| [安全约束](#PSML_Security_Constraints)？ | （可选）定义页面的内联安全约束。如果未指定，则页面继承父[文件夹](#Folder)中有效的安全约束。                                                                                                 |

示例：[参见上面的介绍性示例。](#PSML)

#### 3.2.10.2. **布局片段**

[页面](#Page)布局 <fragment> 元素是一个分层容器 ，用于保存[portlet 片段](#Portlet_Fragments)和嵌套布局片段。[页面](#Page)的根片段必须是布局片段，即使只有一个 portlet 片段是页面的一部分。布局片段受制于父布局片段的布局，因此支持“行”和“列”[布局属性](#Fragment_Properties)。此外，它们还支持用于控制多列布局比例的 'sizes' 布局属性。此元素有 3 个必需属性：


| **属性** | **描述**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ID       | 所需的id用于标识片段，并且在站点内定义的所有片段中**必须是唯一的。**该值对Jetspeed2是不透明的，并且可以遵循任何约定以保证唯一性。由于 Jetspeed2 可能会在内部缓存片段，因此对现有页面的任何编辑都可能需要新的 id 以确保 Jetspeed2 进行修改。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 类型     | 对于所有布局片段，此必需属性必须设置为“布局”。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 姓名     | 用于实现片段布局的portlet的必需名称。portlet 名称通常采用“portlet-app-name:portlet-name”的形式，其中 portlet-app-name 是 web 上下文名称，如 portlet.xml 文件中所指定。以下是受支持的 Jetspeed2 布局 portlet 名称：· jetspeed-layouts::FrameLayoutPortlet· jetspeed-layouts::VelocityOneColumn· jetspeed-layouts::VelocityOneColumnNoActions· jetspeed-layouts::VelocityThreeColumns· jetspeed-layouts::VelocityThreeColumnsNoActions· jetspeed-layouts::VelocityThreeColumnsTable· jetspeed-layouts::VelocityTwoColumns· jetspeed-layouts::VelocityTwoColumns2575· jetspeed-layouts::VelocityTwoColumns2575NoActions· jetspeed-layouts::VelocityTwoColumnsNoActions· jetspeed-layouts::VelocityTwoColumnsSmallLeft· jetspeed-layouts::VelocityTwoColumnsSmallLeftNoActions· jetspeed-layouts::VelocityTwoColumnsTable |

布局 <fragment> 元素包含许多其他 PSML 元素：


| **元素**                               | **描述**                                                                                                                                                                                                          |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [分段\*](#Portlet_Fragments)             | 指定的片段元素可以是要由该布局片段布局的Portlet片段，也可以是嵌套的布局片段。所有子片段都将具有必需的[属性](#Fragment_Properties)元素来指定它们在此布局中的位置。在布局片段中不指定任何片段将导致不生成任何内容。 |
| [财产\*](#Fragment_Properties)           | 布局片段可以有一个可选的“大小”属性，可用于指定多列布局比例。嵌套布局片段也可能具有“行”和/或“列”属性，以标识其在父布局中的位置。                                                                             |
| [安全约束](#PSML_Security_Constraints)？ | 可选地为片段及其子片段定义内联安全约束。与页面、文件夹和链接约束不同，只能约束“查看”权限。如果未指定，则片段继承[页面](#Page)中有效的安全约束。                                                                 |

例子：

<页面>

...

<fragment id="100393" type="layout" name="jetspeed-layouts::VelocityOneColumn">

<fragment id="100939" type="portlet" name="j2-admin::LocaleSelector">

  <属性名称=“行”值=“0”/>

</片段>                                

<fragment id="100345" type="layout" name="jetspeed-layouts::VelocityTwoColumns">

  <property name="row" value="1"/>

  <property name="sizes" value="33%,66%"/>

  <fragment id="100121" type="portlet" name="j2-admin::LoginPortlet">

    <属性名称=“行”值=“0”/>

    <property name="column" value="0"/>

  </片段>                                

  <fragment id="100171" type="portlet" name="demo::UserInfoTest">

    <属性名称=“行”值=“0”/>

    <property name="column" value="1"/>

  </片段>    

</片段>
</片段>

...

</页面>

#### 3.2.10.3. **Portlet 片段**

portlet <fragment> 元素用于标识页面上的portlet。Portlet 片段受制于父布局片段的布局，因此支持布局所需的“行”和“列”[布局属性](#Fragment_Properties)。此元素有许多有效属性：


| **属性** | **描述**                                                                                                                                                                                                                                    |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ID       | 所需的id用于标识片段，并且在站点内定义的所有片段中**必须是唯一的。**该值对Jetspeed2是不透明的，并且可以遵循任何约定以保证唯一性。由于 Jetspeed2 可能会在内部缓存片段，因此对现有页面的任何编辑都可能需要新的 id 以确保 Jetspeed2 进行修改。 |
| 类型     | 对于所有portlet片段，此必需属性必须设置为“portlet”。                                                                                                                                                                                      |
| 姓名     | 用于填充片段内容的portlet的必需名称。portlet 名称通常采用 portlet.xml 文件中指定的“portlet-app-id:portlet-id”形式。                                                                                                                       |
| 皮肤     | 可以在portlet装饰器中引用以控制片段表示的通用装饰器属性。Jetspeed2 目前不使用。                                                                                                                                                             |
| 装饰师   | 用于呈现片段的默认portlet装饰器的名称。此属性是可选的，但如果未指定，则页面的[默认值](#PSML_Defaults)必须指定默认的portlet装饰器。                                                                                                          |
| 状态     | 片段portlet的初始状态；'hidden' 当前是此属性的唯一有效值。                                                                                                                                                                                  |

portlet <fragment> 元素包含其他 PSML 元素：


| **元素**                               | **描述**                                                                                                                                  |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| [财产\*](#Fragment_Properties)           | 父片段可能具有“行”和/或“列”属性来标识父布局中的位置。                                                                                 |
| 标题？                                   | 可选的简单文本元素，包含片段portlet的标题，覆盖 portlet.xml 中设置的标题。                                                                |
| [偏爱\*](#Preferences)                   | 指定片段portlet的初始用户首选项设置，覆盖在 portlet.xml 中设置的任何 portlet 首选项。反过来，用户偏好会覆盖这些值。                       |
| [安全约束](#PSML_Security_Constraints)？ | 可以选择为片段定义内联安全约束。与页面、文件夹和链接约束不同，只能约束“查看”权限。如果未指定，则片段继承[页面](#Page)中有效的安全约束。 |

例子：

<fragment id="100393" type="layout" name="jetspeed-layouts::VelocityOneColumn">

...

<fragment id="100939" type="portlet" name="j2-admin::LocaleSelector">

<属性名称=“行”值=“0”/>
</片段>                                

...

</片段>

#### 3.2.10.4. **片段参考**

<fragment-reference> 元素用于将外部[片段定义](#Fragment_Definition)片段层次结构插入到包含[页面](#Page)、[动态页面](#Dynamic_Page)或[页面模板](#Page_Template)中。片段引用不能出现在[片段定义](#Fragment_Definition)中。引用的片段可以是[布局片段](#Layout_Fragments)或[portlet 片段](#Portlet_Fragments)。片段引用元素的属性和子元素会覆盖被引用片段中的设置。[片段引用元素支持布局片段](#Layout_Fragments)或[portlet 片段](#Portlet_Fragments)不支持的一个附加属性：


| **属性** | **描述**                                                         |
| -------- | ---------------------------------------------------------------- |
| 重新定义 | 要插入的[片段定义](#Fragment_Definition)中的根片段的唯一标识符。 |

片段引用元素不支持以下[布局片段](#Layout_Fragments)和[portlet 片段](#Portlet_Fragments)属性和子元素：名称、类型、片段、片段引用和页面片段。

例子：

<fragment-reference id="template-top-wp-reference" refid="wp-definition">

<property name="row" value="2"/>

</片段参考>

#### 3.2.10.5. **片段属性**

[片段](#Portlet_Fragments)<property> 元素用于指定片段的命名属性 。这些属性通常用于指定页面中的布局 portlet 参数和 portlet 位置。property 元素有 3 个受支持的属性：


| **属性**         | **描述**                                                                                                                                                         |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 布局*（已弃用）* | 与属性关联的布局片段Portlet的符号名称。出于兼容性原因，支持此属性。布局和 Portlet 片段的严格层次结构意味着任何单个片段及其属性都可以受制于一个布局片段 Portlet。 |
| 姓名             | 片段属性名称。Jetspeed2布局portlet 支持“行”、“列”和“大小”属性。                                                                                            |
| 价值             | 片段属性值。'row'和 'column' 属性接受基于 0 的索引值。'sizes' 属性接受 HTML 框架集标记 'rows' 和 'cols' 属性语法（即 '25%,75%'）。                               |

例子：

<fragment id="100876" type="portlet" name="j2-admin::LoginPortlet">

...

<property name="row" value="2"/>

<property name="column" value="1"/>

...

</片段>

<fragment id="103456" type="layout" name="jetspeed-layouts::VelocityTwoColumns">

...

<property name="sizes" value="33%,66%"/>

...

</片段>

#### 3.2.10.6. **优先**

[portlet 片段](#Portlet_Fragments)<preference> 元素允许定义默认的 portlet 首选项值 。这为在页面上为 portlet 实例设置默认 portlet 首选项提供了一种更简单的途径，而无需在 portlet 应用程序的 portlet.xml 中复制 portlet 定义。

首选项优先级：用户定义 > 片段定义 > portlet.xml 定义。

<preference> 元素属性：


| **属性** | **描述**                                   |
| -------- | ------------------------------------------ |
| 姓名     | 首选项的名称。                             |
| 只读     | 指示用户是否可以更改此首选项的值的布尔值。 |

<preference> 元素包含以下元素：


| **元素** | **描述**                                 |
| ---------- | ---------------------------------------- |
| 价值+      | 包含与命名首选项关联的值的简单文本元素。 |

例子：

<fragment id="uhtemp-1012" type="portlet" name="demo::BookmarkPortlet">

...

<preference name="Google" readOnly="false">

<value>http://www.google.com</value>
</偏好>

...

</片段>

#### 3.2.10.7. **动态页面**

<dynamic-page> 元素定义了一个可重用页面，用于在门户站点中显示任何匹配的门户内容请求 URL。各个动态页面由门户 URL 路径和内容类型的门户站点映射选择。除了这个匹配过程之外，内容页面与具体[页面](#Page)定义相同。除了页面元素属性和子元素之外，动态页面元素还支持两个属性：


| **属性** | **描述**                                                                                                                                     |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 内容类型 | 标识此可重用页面将用于显示的内容的内容类型字符串。通配符类型“*”可用于标识应由所有内容类型使用的动态页面，或作为不匹配内容请求 URL 的后备。 |
| 可继承   | 指示其他更具体的门户内容URL是否可以使用此页面定义的布尔值。                                                                                  |

例子：

<动态页面内容类型=“文档”可继承=“假”>

...

<fragment id="default-content-layout" type="layout" name="jetspeed-layouts::VelocityTwoColumns">

...
</片段>

...

</动态页面>

#### 3.2.10.8. **页面模板**

<page-template> 元素指定了一个模板页面，该页面定义了要包含在门户网站的所有[具体页面](#Page)和[动态页面](#Dynamic_Page)中的 顶级片段和片段引用。所需的单个[页面片段](#Page_Fragment)必须是页面模板片段层次结构的一部分。当页面被合并到模板中时，这个片段被替换为显示的[具体页面](#Page)和[动态页面](#Dynamic_Page)的根片段。除了[页面片段](#Page_Fragment)，页面模板元素同样支持所有[页面](#Page)属性和子元素。

例子：

<页面模板>

...

<fragment id="template-top" type="layout" name="jetspeed-layouts::VelocityOneColumn">

...

<page-fragment id="template-top-page-template">

  <property name="row" value="1"/>

</page-fragment>

...
</片段>

...

</page-template>

#### 3.2.10.9. **页面片段**

[<page-fragment> 元素在每个页面模板](#Page_Template)定义 中只出现一次。当页面模板与显示的[具体页面](#Page)或[动态页面](#Dynamic_Page)合并时，所有属性和子元素都会覆盖引用页面的根片段中的相同设置。页面片段元素不支持其他[布局片段属性。](#Layout_Fragments)页面片段元素不支持以下[布局片段](#Layout_Fragments)属性和子元素：名称、类型、片段、片段引用和页面片段。

例子：

<页面模板>

...

<fragment id="template-top" type="layout" name="jetspeed-layouts::VelocityOneColumn">

...

<page-fragment id="template-top-page-template">

  <property name="row" value="1"/>

</page-fragment>

...
</片段>

...

</page-template>

#### 3.2.10.10. **片段定义**

[<fragment-definition> 元素定义了可以在多个页面](#Page)、[动态页面](#Dynamic_Page)或[页面模板](#Page_Template) 中引用和合并的片段层次结构。片段定义由包含的根片段的 id 引用，片段层次结构合并到引用的显示页面中。片段定义的所有属性和子元素（根片段除外）都不会在显示的页面中使用。因此，仅支持用于识别、描述或保护片段定义本身的[页面元素和属性：**id**、安全约束、版本、标题、短标题和元数据。](#Page)只有[布局片段](#Layout_Fragments)和[portlet 片段](#Layout_Fragments)可以出现在片段层次结构中，但与页面不同的是，根片段不必是布局。

例子：

<片段定义>

<title>当前天气</title>

<fragment id="wp-definition" type="portlet" name="demo::WeatherPortlet"/>

</片段定义>

#### 3.2.10.11. **文件夹**

<folder> 元素是一个简单的容器，用于保存与门户网站文件夹关联的其他 PSML 元素。此元素作为文件夹.元数据文件保存在关联的文件系统目录中。文件夹元素有两个有效属性：


| **属性** | **描述**                                                             |
| -------- | -------------------------------------------------------------------- |
| 隐       | 一个布尔属性，用于指示文件夹不应出现在门户网站菜单或其他导航元素中。 |
| 版本     | 通用版本跟踪属性。Jetspeed2目前不使用。                              |

<folder> 元素包含许多其他 PSML 元素：


| **元素**                               | **描述**                                                                                                                                                                                                                                                                                                    |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 标题？                                   | 包含默认文件夹标题文本的简单元素。文件夹的标题被认为是它的长描述，如果短标题可用于菜单文本，则在某些装饰器中用作翻转文本。如果未指定，Jetspeed2将尝试从包含文件夹元素的文件的名称中定义标题。                                                                                                               |
| 短标题？                                 | 包含文件夹默认短标题文本的可选简单元素。短标题（如果可用）在某些装饰器中用作菜单文本。如果未指定，则使用标题文本。                                                                                                                                                                                          |
| [默认值？](#PSML_Defaults)               | （可选）指定文件夹或子文件夹页面及其片段的装饰。在各个页面或父文件夹中明确指定的每个页面都需要布局装饰。                                                                                                                                                                                                    |
| 默认页面？                               | 可选的简单元素，包含带有文件夹默认页面或子文件夹名称的文本。在门户中直接引用文件夹时使用默认页面。可以指定此文件夹中任何[页面或文件夹的名称（包括父文件夹的“..”）。](#Page)如果没有设置默认页面，将使用名为“default-page.psml”的页面；如果“default-page.psml”不存在，文件夹中的第一页将成为默认页面。 |
| 文件顺序\*                               | 一个可选的简单元素集合，包含用于定义[页面](#Page)、子文件夹和[链接](#Link)成员的排序顺序的文本名称。具有匹配名称的成员将按照定义这些元素的顺序排列。其他成员将按其名称排序，并出现在匹配成员之后的菜单和其他列表中。不支持名称匹配的正则表达式。                                                            |
| [元数据](#PSML_Titles_and_Metadata)\*    | （可选）指定文件夹的区域设置特定标题和短标题。                                                                                                                                                                                                                                                              |
| [菜单](#Menus)\*                         | 可以选择为文件夹指定附加的或覆盖继承的菜单定义。                                                                                                                                                                                                                                                            |
| [安全约束](#PSML_Security_Constraints)？ | （可选）定义文件夹的内联安全约束。如果未指定，则文件夹继承父文件夹中有效的安全约束。                                                                                                                                                                                                                        |

示例：[参见上面的介绍性示例。](#PSML)

#### 3.2.10.12. **关联**

<link> 元素是一个简单的容器，用于保存与用于引用门户网站外部内容的门户链接相关联的其他 PSML 元素。[此元素在与父文件夹](#Folder)关联的适当文件系统目录中作为扩展名为“.link”的文件保存。链接元素有三个有效属性：


| **属性** | **描述**                                                                                                                                     |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 目标     | 打开外部内容的可选目标框架名称。如果未指定，链接内容将替换浏览器中的门户。                                                                   |
| 版本     | 通用版本跟踪属性。Jetspeed2目前不使用。                                                                                                      |
| 皮肤     | 可以在portlet装饰器中引用以控制链接表示的通用装饰器属性。[如果没有另外指定，链接的菜单](#Menus)选项元素将采用此外观值。Jetspeed2目前不使用。 |

<link> 元素包含许多其他 PSML 元素：


| **元素**                               | **描述**                                                                                                                                                                                |
| ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 标题？                                   | 包含默认链接标题文本的简单元素。链接的标题被认为是它的长描述，如果短标题可用于菜单文本，则在某些装饰器中用作翻转文本。如果未指定，Jetspeed2将尝试从包含链接元素的文件的名称中定义标题。 |
| 短标题？                                 | 可选的简单元素，包含链接的默认短标题文本。短标题（如果可用）在某些装饰器中用作菜单文本。如果未指定，则使用标题文本。                                                                    |
| 网址                                     | 所需的内容url元素。此元素的文本将用于在浏览器中导航指定的目标框架。                                                                                                                     |
| [元数据](#PSML_Titles_and_Metadata)\*    | （可选）指定链接的区域设置特定标题和短标题。                                                                                                                                            |
| [安全约束](#PSML_Security_Constraints)？ | （可选）定义链接的内联安全约束。如果未指定，则链接继承父[文件夹](#Folder)中有效的安全约束。                                                                                             |

示例：[参见上面的介绍性示例。](#PSML)

#### 3.2.10.13. **全局页面安全**

<page-security> 元素是一个简单的容器，用于保存用于声明全局安全约束及其定义的其他 PSML 元素。该元素作为 page.security 文件持久保存，并且始终位于 PSML 文件系统的根目录中目录。页面安全元素只有一个有效属性：


| **属性** | **描述**                                |
| -------- | --------------------------------------- |
| 版本     | 通用版本跟踪属性。Jetspeed2目前不使用。 |

<page-security> 元素包含两个与 PSML 元素相关的安全约束：


| **元素**                                       | **描述**                                                                                                                                                                   |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [安全约束-def](#PSML_Security_Constraints)\*     | （可选）定义由名称定义的安全约束集合。这些安全约束在[页面](#Page)、[片段](#Layout_Fragments)、[文件夹](#Folder)和[链接](#Link)中以及在此元素中引用，以促进重用和安全维护。 |
| [全局安全约束参考](#PSML_Security_Constraints)\* | （可选）定义要应用于站点中所有安全约束的安全约束引用。每个简单元素的文本引用在此元素中指定的命名安全约束定义。                                                             |

示例：[参见上面的介绍性示例。](#PSML)

#### 3.2.10.14. **PSML 标题和元数据**

[page](#Page) 、[folder](#Folder)和[link](#Link) <metadata> 元素用于定义特定于区域设置的标题和短标题文本。任何数量的这些元素都可能出现在包含 PSML 元素中，但不应为单个语言环境指定多个命名值。PSML xml 文档通常使用 UTF-8 编码声明以支持各种字符集。


|          |                                                                                                                                        |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **属性** | **描述**                                                                                                                               |
| 姓名     | 元数据文本的名称。此名称应为“title”或“short-title”以指定特定于区域设置的标题文本。                                                 |
| xml:语言 | 元数据文本的区域设置语言或语言/国家/地区选择器。期望使用传统的 Java 语言环境名称（ISO-639 和 ISO-3166）。有效值包括“en”和“en_US”。 |

例子：

<页面>

...

<metadata name="title" xml:lang="fr">Ma Premiere Page de PSML</metadata>

<metadata name="title" xml:lang="es">¡Bienvenido a Jetspeed 2!</metadata>

<metadata name="title" xml:lang="hu">Köszönti a Jetspeed 2!</metadata>

...

</页面>

#### 3.2.10.15. **PSML 默认值**

[页面](#Page) 和[文件夹](#Folder)<defaults> 元素定义了默认布局装饰器和默认 portlet 装饰器。默认布局装饰器应用于所有没有装饰器属性的顶级布局片段。默认的 portlet 装饰器应用于所有没有装饰器属性的 portlet 片段。默认值可以从父文件夹默认元素继承。默认元素上有三个有效属性：


| **属性**      | **描述**                                                                                                                                            |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 布局装饰器    | 用于呈现页面的布局装饰器的名称。此属性是必需的，但可以从父文件夹继承。                                                                              |
| portlet装饰器 | 用于呈现页面片段的默认portlet装饰器的名称。此属性是可选的，但几乎总是设置。该属性也可以从父文件夹继承。                                             |
| 皮肤          | 可以在装饰器中引用以控制页面和文件夹呈现的通用装饰器属性。[如果未另行指定，页面和文件夹的菜单](#Menus)选项元素将采用此外观值。Jetspeed2目前不使用。 |

例子：

<页面>

...

<defaults skin="orange" layout-decorator="tigris" portlet-decorator="tigris"/>

...

</页面>

#### 3.2.10.16. **PSML 安全约束**

<security-constraints>、<security-constraints-def> 和 <global-security-constraints-ref> 元素出现在[pages](#Page)、[fragment](#Layout_Fragments)、[folders](#Folder)、[links](#Link)和上面的[页面安全](#Global_Page_Security)元素中分别记录在声明中安全约束指南。

[声明性安全约束指南](https://portals.apache.org/jetspeed-2/deployguide/guide-security-declarative-psml.html)

#### 3.2.10.17. **PSML 菜单**

出现在上述[页面](#Page)和[文件夹](#Folder)元素中的 <menu> 元素在声明性菜单指南中单独记录。

[声明式菜单指南](https://portals.apache.org/jetspeed-2/deployguide/guide-menus-declarative-psml.html)

### 3.2.11. [**PSML DTD**](https://portals.apache.org/jetspeed-2/devguide/guide-psml-dtd.html)

# 4. **数据库**

## 4.1. [**数据库指南**](https://portals.apache.org/jetspeed-2/devguide/guide-database.html)

与 Jetspeed-2 一起分发的默认数据库是 Apache Derby 数据库。要继续使用更强大的数据库，请按照下一节中的说明进行操作。

### 4.1.1. **支持的数据库**

支持的数据库列表：


| **数据库名称**               | **构建常量** | **测试版本** |
| ---------------------------- | ------------ | ------------ |
| IBM DB2                      | 数据库2      | 9.1          |
| Apache Derby，IBM Cloudscape | 德比         | 10.1         |
| 超音速SQL (HSQL)             | hsql         | 1.8          |
| 微软SQL服务器                | mssql        | 2000, 2005   |
| MySQL                        | mysql        | 4.\*, 5.\*   |
| 甲骨文                       | 甲骨文       | 9i, 10g      |
| PostgreSQL                   | postgres     | 8.\*         |
| SAP数据库、MaxDB             | 数据库       | 7.5          |

### 4.1.2. **MySQL**

要使用 My SQL 运行，请将以下属性添加到您的 $HOME/build.properties：

#------------------------------------------------ ----------------------

# 配置 MySQL 测试数据库（仅在运行单元测试时需要）

#------------------------------------------------ ----------------------

org.apache.jetspeed.test.database.default.name=mysql

org.apache.jetspeed.test.database.url = jdbc:mysql://j2-server/j2test

org.apache.jetspeed.test.database.driver = com.mysql.jdbc.Driver

org.apache.jetspeed.test.database.user = jetspeed2

org.apache.jetspeed.test.database.password = 不管

#------------------------------------------------ ----------------------

# 配置 MySQL 生产数据库

#------------------------------------------------ ----------------------

org.apache.jetspeed.production.database.default.name=mysql

org.apache.jetspeed.production.database.url = jdbc:mysql://j2-server/j2

org.apache.jetspeed.production.database.driver = com.mysql.jdbc.Driver

org.apache.jetspeed.production.database.user = jetspeed2

org.apache.jetspeed.production.database.password = 不管

#------------------------------------------------ ----------------------

在上面的示例中，您需要在名为“j2-server”的主机上运行 MySQL 服务器，并在生产环境中使用名为“j2”的数据库。

如果您要运行单元测试，您还需要一个名为“j2test”的附加测试数据库。

应授予名为“jetspeed2”的用户访问“j2”和“j2test”数据库的权限。

#### 4.1.2.1. **MySQL 已知问题**

没有任何

### 4.1.3. **甲骨文**

要使用 Oracle 运行，请将以下属性添加到您的 $HOME/build.properties：

#------------------------------------------------ ----------------------

# 配置 Oracle 测试数据库（仅在运行单元测试时需要）

#------------------------------------------------ ----------------------

# org.apache.jetspeed.test.database.default.name=oracle

# org.apache.jetspeed.test.database.ojb.platform=oracle9i

# org.apache.jetspeed.test.database.url = jdbc:oracle:thin:@j2-sever:1521:j2db

# org.apache.jetspeed.test.database.driver = oracle.jdbc.driver.OracleDriver

# org.apache.jetspeed.test.database.user = j2test

# org.apache.jetspeed.test.database.password = 不管

#------------------------------------------------ ----------------------

# 配置 Oracle 生产数据库

#------------------------------------------------ ----------------------

# org.apache.jetspeed.production.database.default.name=oracle

# org.apache.jetspeed.production.database.ojb.platform=oracle9i

# org.apache.jetspeed.production.database.url = jdbc:oracle:thin:@j2-server:1521:j2db

# org.apache.jetspeed.production.database.driver = oracle.jdbc.driver.OracleDriver

# org.apache.jetspeed.production.database.user = j2

# org.apache.jetspeed.production.database.password = 不管

#------------------------------------------------ ----------------------

在上面的示例中，您需要在名为“j2-server”的主机上运行 Oracle 服务器，并在该服务器上安装名为“j2db”的 Oracle 数据库 SID。此外，您将需要一个名为“j2”的数据库用户（模式）用于生产。

如果您要运行单元测试，您将需要一个名为“j2test”的附加用户。

#### 4.1.3.1. **Oracle 已知问题**

只有在您第一次为 Oracle 创建数据库时，drop 语句才会出现问题。要解决这个问题，请在 $HOME/build.properties 中设置您的属性，然后使用 [Jetspeed 2 Maven 插件 ](https://portals.apache.org/jetspeed-2/devguide/j2-maven-plugin.html)运行这些命令 ：

maven j2:db.scripts.gen

maven j2:dropdrops

maven j2:db.create.test（仅在运行单元测试时）

maven j2:db.create.production

### 4.1.4. **驱动程序**

通过将您指定的 JDBC 驱动程序 jars 添加到 Maven 类路径，JDBC 驱动程序被配置为与 Maven 构建一起使用。 在 $HOME/build.properties 中 使用**org.apache.jetspeed.test.jdbc.drivers.path** 和 **org.apache.jetspeed.production.jdbc.drivers.path**属性指定 jars 。

注意：Derby JDBC 驱动程序随 Jetspeed 一起分发，无需配置。

# My SQL Driver Path 示例，测试和生产

org.apache.jetspeed.test.jdbc.drivers.path=

 /Portal/lib/MySQL/mysql-connector-java-3.0.8-stable-bin.jar
org.apache.jetspeed.production.jdbc.drivers.path=

 /Portal/lib/MySQL/mysql-connector-java-3.0.8-stable-bin.jar
# Oracle 9i 驱动程序路径示例，测试和生产

org.apache.jetspeed.test.jdbc.drivers.path=

 /Portal/lib/oracle/ojdbc14.jar；/Portal/lib/oracle/nls_charset12.jar
org.apache.jetspeed.production.jdbc.drivers.path=

 /Portal/lib/oracle/ojdbc14.jar；/Portal/lib/oracle/nls_charset12.jar
# Oracle 8i Driver Path Example，测试和生产

org.apache.jetspeed.test.jdbc.drivers.path=

 /Portal/lib/oracle/classes12.jar；
org.apache.jetspeed.production.jdbc.drivers.path=

 /Portal/lib/oracle/classes12.jar；

	
#### 4.1.4.1. **分发驱动程序**

当使用 maven 部署目标将 Jetspeed 部署到应用程序服务器时，只有 Derby JDBC 驱动程序被复制到 Web 应用程序中。要分发特定的驱动程序（即 Oracle、MySQL），您需要将驱动程序复制到应用程序服务器的公共类路径中以共享代码。


| **应用服务器** | **程序**                              |
| -------------- | ------------------------------------- |
| 雄猫6+         | 将驱动程序复制到\${TOMCAT\_HOME}/lib/ |

#### 4.1.4.2. **Jetspeed-2 的数据源配置**

Jetspeed-2 需要在部署它的应用服务器中配置数据源。有关详细信息，请参阅[RDBMS 组件文档](https://portals.apache.org/jetspeed-2/devguide/dev-rdbms.html)。

## 4.2. [**表**](https://portals.apache.org/jetspeed-2/devguide/guide-tables.html)


| **表名**        | **描述**                                                           |
| --------------- | ------------------------------------------------------------------ |
| ADMIN\_ACTIVITY | 跟踪管理员用户的管理审计活动。从用户管理器中添加和删除用户等活动   |
| USER\_ACTIVITY  | 跟踪用户活动。跟踪用户活动，例如登录和注销、更改密码、更新用户资料 |

### 4.2.1. **配置**

        #------------------------------------------------ ----------------------

        # jetspeed.properties

        #------------------------------------------------ ----------------------

        portal.audit.enable=true
### 4.2.2. **统计表**


| **表名**            | **描述**                                                             |
| ------------------- | -------------------------------------------------------------------- |
| PAGE\_STATISTICS    | 计算页面访问次数以及系统范围内的最小、最大和平均页面呈现时间         |
| USER\_STATISTICS    | 计算用户总会话和会话最大、最小和平均会话时间                         |
| PORTLET\_STATISTICS | 计算系统范围内的Portlet访问次数以及最小、最大和平均 Portlet 呈现时间 |

##### 4.2.2.0.1. **配置**

        #------------------------------------------------ ----------------------

        # jetspeed.properties

        #------------------------------------------------ ----------------------

        portal.statistics.logToLogger=false

        portal.statistics.logToDatabase=true

        # 记录数

        portal.statistics.MaxPortalRecordToFlush=300

        portal.statistics.MaxUserUserRecordToFlush=50

        portal.statistics.MaxPagePageRecordToFlush=100

        # 以毫秒为单位的刷新时间

        portal.statistics.MaxTimePortalToFlush=300000

        portal.statistics.MaxTimeUserToFlush=5000

        portal.statistics.MaxTimePageToFlush=60000
### 4.2.3. **探查器表**


| **表名**               | **描述**                                                                                                  |
| ---------------------- | --------------------------------------------------------------------------------------------------------- |
| PROFILING\_RULE        | 定义分析规则名称和类                                                                                      |
| RULE\_CRITERION        | 定义一个Profiling Rule Criterion并将其与 Profiling Rule(RULE_ID) 和一个 RULE CRITERIA(CRITERIA_ID) 相关联 |
| PRINCIPAL\_RULE\_ASSOC | 将用户(PRINCIPAL\_NAME)与分析规则 (RULE_ID) 相关联。确定每个用户使用哪个分析规则。                        |
| PROFILE\_PAGE\_ASSOC   | 已弃用                                                                                                    |

#### 4.2.3.1. **配置**

        #------------------------------------------------ ----------------------

        # jetspeed.properties

        #------------------------------------------------ ----------------------

        # 分配给新用户的默认分析规则名称

        profiler.rule.names.default = 页

        # 分配给新用户的默认分析规则值

        profiler.rule.values.default = j2

        # 在注册或新用户创建期间分配的注册默认配置文件规则

        # 逗号分隔列表

        registration.rules.default = j2
### 4.2.4. **安全表**


| **表名**                   | **描述**                                                                                                                                                                   |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SECURITY\_DOMAIN           | 多租户域标识符。目前在数据库中建模，但Jetspeed未使用                                                                                                                       |
| SECURITY\_PRINCIPAL        | 定义用户、角色、组类型的安全主体。用户存储在此表中。存储在PRINCIPAL\_NAME列中的用户名，由 DTYPE + PRINCIPAL_NAME 唯一                                                      |
| SECURITY\_PRINCIPAL\_ASSOC | 通过FROM\_PRINCIPAL到 TO_PRINCIPAL 将一个主体关联到另一个主体。这就是我们表示用户组和角色成员身份的方式。有效的关联类型有：isMemberOf、isChildOf、isA、isPartOf、belongsTo |
| SECURITY\_PERMISSION       | Java安全策略权限定义。支持的权限：文件夹、页面、Portlet、片段。                                                                                                            |
| SECURITY\_CREDENTIAL       | 定义与安全主体关联的凭据。还定义了凭证/密码规则和过期时间                                                                                                                  |
| SECURITY\_ATTRIBUTE        | 与安全主体关联的属性名称值对（一对多属性）。通常用于每个用户的动态用户属性                                                                                                 |
| PRINCIPAL\_PERMISSION      | 关联（join）表将安全主体（SECURITY_PRINCIPAL）连接到权限（SECURITY_PERMISSION）                                                                                            |

#### 4.2.4.1. **配置**

        #------------------------------------------------ ----------------------

        # jetspeed.properties

        #------------------------------------------------ ----------------------

        #1 = 权限 = 使用 Jetspeed Java 安全策略

        #2 = 约束 = 使用 Jetspeed (PageManager) 基于约束的安全性

        portal.core.security.type=2

        # jetspeed 安全持久性管理器缓存大小：

        org.apache.jetspeed.ehcache.jspm.maxelements=128

        # jetspeed 安全持久性管理器缓存元素过期秒数，（无限 = 0）：

        org.apache.jetspeed.ehcache.jspm.element.ttl=150

        # 如果没有设置用户，default.user.principal 将是

        # 通过 HttpRequestContext.setUserPrincpal() 自动添加

        default.user.principal=guest

        default.admin.user=admin

        default.admin.role=管理员

        default.manager.role=经理

        default.user.role=用户

        default.guest.role=guest
### 4.2.5. **PSML 表**


| **表名**                    | **描述**                       |
| --------------------------- | ------------------------------ |
| 文件夹                      | PSML文件夹                     |
| FOLDER\_CONSTRAINT          | PSML文件夹安全                 |
| FOLDER\_CONSTRAINTS\_REF    | PSML文件夹安全                 |
| FOLDER\_MENU                | PSML文件夹菜单                 |
| FOLDER\_MENU\_METADATA      | PSML文件夹菜单                 |
| FOLDER\_METADATA            | PSML文件夹菜单                 |
| FOLDER\_ORDER               | PSML文件夹菜单                 |
| 分段                        | PSML片段（Portlet 实例）       |
| FRAGMENT\_CONSTRAINT        | PSML片段（Portlet 实例）安全性 |
| FRAGMENT\_CONSTRAINTS\_REF  | PSML片段（Portlet 实例）安全性 |
| FRAGMENT\_PREF              | 实体（页面片段）级别首选项     |
| FRAGMENT\_PREF\_VALUE       | 实体（页面片段）级别首选项     |
| FRAGMENT\_PROP              | 片段属性，如列数、行/列定位    |
| 关联                        | PSML链接                       |
| LINK\_CONSTRAINT            | PSML链接安全                   |
| LINK\_CONSTRAINT\_REF       | PSML链接安全                   |
| LINK\_METADATA              | PSML链接                       |
| 页                          | PSML页面                       |
| PAGE\_CONSTRAINT            | PSML页面安全                   |
| PAGE\_CONSTRAINT\_REF       | PSML页面安全                   |
| PAGE\_MENU                  | PSML页面菜单                   |
| PAGE\_MENU\_METADATA        | PSML页面菜单                   |
| PAGE\_METADATA              | PSML页面元数据                 |
| PAGE\_SECURITY              | PSML页面安全定义和参考         |
| PAGE\_SEC\_CONSTRAINTS\_DEF | PSML全局安全约束集合定义       |
| PAGE\_SEC\_CONSTRAINTS\_REF | PSML全局安全约束参考           |
| PAGE\_SEC\_CONSTRAINT\_DEF  | PSML全局安全约束定义           |

#### 4.2.5.1. **配置**

        #------------------------------------------------ ----------------------

        # jetspeed.properties

        #------------------------------------------------ ----------------------

        # 页面管理器安全的默认值

        page.manager.permissions.security = false

        page.manager.constraints.security = true

        db.page.manager.cache.size=128

        #- 文件夹/页面/链接缓存过期秒，默认=-1（默认为 150 秒），infinite=0，min=30

        db.page.manager.cache.expire=-1
### 4.2.6. **首选项表**


| **表名**                   | **描述**                                                            |
| -------------------------- | ------------------------------------------------------------------- |
| PORTLET\_PREFERENCE        | 主要Portlet和用户首选项定义                                         |
| PORTLET\_PREFERENCE\_VALUE | 通过PREF\_ID关联到 PORTLET_PREFERENCE 的主要 Portlet 和用户首选项值 |

        #------------------------------------------------ ----------------------

        # jetspeed.properties

        #------------------------------------------------ ----------------------

        首选项.session.cache.enabled = true
### 4.2.7. **注册表**


| **表名**                  | **描述**                                   |
| ------------------------- | ------------------------------------------ |
| CUSTOM\_PORTLET\_MODE     | portlet.xml                                |
| CUSTOM\_WINDOW\_STATE     | portlet.xml                                |
| 事件别名                  | portlet.xml                                |
| EVENT\_DEFINITION         | portlet.xml                                |
| FILTERED\_PORTLET         | portlet.xml                                |
| FILTER\_LIFECYCLE         | portlet.xml                                |
| FILTER\_MAPPING           | portlet.xml                                |
| JETSPEED\_SERVICE         | jetspeed-portlet.xml                       |
| 语言                      | portlet.xml                                |
| LOCALE\_ENCODING\_MAPPING | portlet.xml                                |
| LOCALIZED\_DESCRIPTION    | portlet.xml                                |
| LOCALIZED\_DISPLAY\_NAME  | portlet.xml                                |
| NAMED\_PARAMETER          | portlet.xml                                |
| 范围                      | portlet.xml                                |
| PARAMETER\_ALIAS          | portlet.xml                                |
| PA\_METADATA\_FIELDS      | jetspeed-portlet.xml                       |
| PA\_SECURITY\_CONSTRAINT  | jetspeed-portlet.xml                       |
| PD\_METADATA\_FIELDS      | jetspeed-portlet.xml                       |
| PORTLET\_APPLICATION      | 来自portlet.xml的主要 Portlet 应用程序定义 |
| PORTLET\_DEFINITION       | 来自portlet.xml的主要 Portlet 定义定义     |
| PORTLET\_FILTER           | portlet.xml                                |
| PORTLET\_LISTENER         | portlet.xml                                |
| PORTLET\_SUPPORTS         | portlet.xml                                |
| PROCESSING\_EVENT         | portlet.xml                                |
| PUBLIC\_PARAMETER         | portlet.xml                                |
| PUBLISHING\_EVENT         | portlet.xml                                |
| RUNTIME\_OPTION           | portlet.xml                                |
| RUNTIME\_VALUE            | portlet.xml                                |
| SECURED\_PORTLET          | portlet.xml                                |
| SECURITY\_ROLE            | portlet.xml                                |
| SECURITY\_ROLE\_REFERENCE | portlet.xml                                |
| USER\_ATTRIBUTE           | portlet.xml                                |
| USER\_ATTRIBUTE\_REF      | portlet.xml                                |

### 4.2.8. **能力表**


| **表名**                  | **描述**                                     |
| ------------------------- | -------------------------------------------- |
| 能力                      | 设备能力                                     |
| 客户                      | 定义一个设备                                 |
| CLIENT\_TO\_CAPABILITY    | 关联表：一个设备（客户端）可以有很多能力     |
| CLIENT\_TO\_MIMETYPE      | 关联表：一个设备（客户端）可以有很多mimetype |
| MEDIATYPE\_TO\_CAPABILITY | 关联表：一个媒体类型可以有很多能力           |
| MEDIATYPE\_TO\_MIMETYPE   | 关联表：媒体类型到MIME类型                   |
| 媒体类型                  | 一种通用的媒体类型，例如HTML或 XML           |
| MIMETYPE                  | Internet标准 Mime 类型，例如 text/html       |

### 4.2.9. **对象关系映射表**


| **表名**     | **描述**                                     |
| ------------ | -------------------------------------------- |
| OJB\_HL\_SEQ | 所有主键的高低序列表（不使用本机数据库序列） |
| OJB\_\*      | 不曾用过                                     |

### 4.2.10. **Jetspeed SSO 表**


| **表名**  | **描述**                                       |
| --------- | ---------------------------------------------- |
| SSO\_SITE | 使用凭据和基于表单的安全参数的安全登录站点定义 |

## 4.3. [**数据访问**](https://portals.apache.org/jetspeed-2/devguide/dao.html)

Jetspeed-2 RDBMS 组件从底层持久性机制中提供了一定程度的抽象。

### 4.3.1. **使用对象关系映射的数据访问**

Jetspeed-2 使用对象关系映射作为持久性的底层技术。默认情况下， [Apache OJB](http://db.apache.org/ojb/)用作 ORM 引擎。为了最小化 Jetspeed-2 OJB 依赖关系，**InitablePersistenceBrokerDaoSupport**提供了一个抽象层来最小化对特定 ORM 引擎的依赖关系。下面的类图说明了利用 Jetspeed-2 的实现类**InitablePersistenceBrokerDaoSupport**：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps65.png)

**InitablePersistenceBrokerDaoSupport**延伸**org.springframework.orm.ojb.support.PersistenceBrokerDaoSupport**。 \_

### 4.3.2. **Spring ORM 支持**

在使用您选择的 O/R 映射层来创建数据访问应用程序时，Spring 增加了重要的支持。扩展了持久性支持的 **InitablePersistenceBrokerDaoSupport**spring 抽象层，特别是 OJB [PersistenceBroker**API **支持](#orm-ojb)。

使用这样的抽象层有很多优点。Spring 文档中概述的一些优点是：

· 易于测试。Spring 的控制反转方法使交换持久性管理器实例、JDBC 数据源、事务管理器和映射器对象实现（如果需要）的实现和配置位置变得容易。这使得隔离和测试每段与持久性相关的代码变得更加容易。

· 常见的数据访问异常。Spring 可以包装来自您选择的 O/R 映射工具的异常，将它们从专有（可能检查的）异常转换为公共运行时 DataAccessException 层次结构。这允许您仅在适当的层中处理大多数不可恢复的持久性异常，而无需烦人的样板捕获/抛出和异常声明。您仍然可以在任何需要的地方捕获和处理异常。请记住，JDBC 异常（包括特定于 DB 的方言）也会转换为相同的层次结构，这意味着您可以在一致的编程模型中使用 JDBC 执行一些操作。

· 通用资源管理。Spring 应用程序上下文可以处理持久性管理器实例、JDBC 数据源和其他相关资源的位置和配置。这使得这些值易于管理和更改。Spring 提供了对持久性资源的高效、简单和安全的处理。

· 综合交易管理。Spring 允许您使用声明性、AOP 样式的方法拦截器或 Java 代码级别的显式“模板”包装类来包装 O/R 映射代码。在任何一种情况下，都会为您处理事务语义，并在出现异常时进行适当的事务处理（回滚等）。如下所述，您还可以获得能够使用和交换各种事务管理器的好处，而不会影响您的 ORM 特定代码：例如，在本地事务和 JTA 之间，具有相同的完整服务（例如声明性事务）在两种情况。作为一个额外的好处，与 JDBC 相关的代码可以与用于执行 O/R 映射的代码在事务上完全集成。这对于不适合 O/R 映射的数据访问很有用，

· 避免供应商锁定，并允许混合搭配实施策略。

## 4.4. [**关系型数据库管理系统**](https://portals.apache.org/jetspeed-2/devguide/dev-rdbms.html)

Jetspeed-2 RDBMS 组件从 Jetspeed-2 使用的持久性机制中提供了一个抽象层。它为数据源配置和数据访问提供了便利。

### 4.4.1. **数据源配置**

Jetspeed-2 使用[OJB](http://db.apache.org/ojb/)PersistenceBroker API 作为其默认的持久性机制。该**ConnectionRepositoryEntry**组件为 Jetspeed-2 以及**/etc/db-ojb**Jetspeed-2 源存储库或**WEB-INF/classes** 已部署的 Jetspeed-2 实例中的可用属性配置 OJB。

**datasource.xml**弹簧组件配置文件配置并 **ConnectionRepositoryEntry**位于 .**WEB-INF/assembly/boot**

根据**ConnectionRepositoryEntry**其属性在 OJB 的 ConnectionRepository 中配置一个条目。属性**driverClassName**、**url**和仅在设置为 no 时使用**username**，即如果连接工厂使用驱动程序创建数据源。平台设置派生自使用 OJB类的已配置数据源或数据库驱动程序。默认的 Jetspeed-2配置公开一个数据源。 **passwordjndiNameJdbcMetadataUtilsConnectionRepositoryEntry**

<bean id="JetspeedDS" class="org.apache.jetspeed.components.rdbms.ojb.ConnectionRepositoryEntry">

  <属性名称="jndiName">

    <value>java:comp/env/jdbc/jetspeed</value>

  </属性>

</豆>
为了使用 Jetspeed-2 正确配置 OJB，**OJB.properties**文件（位于 **/etc/db-ojb/OJB.properties**源代码树下和**WEB-INF/classes**部署的应用程序中）必须设置：

ConnectionManagerClass=org.apache.jetspeed.components.rdbms.ojb.ConnectionManagerImpl
代替：

ConnectionFactoryClass=org.apache.ojb.broker.accesslayer.ConnectionFactoryManagedImpl
**ConnectionRepositoryEntry**和 的类图**ConnectionManagerImpl**如下：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps66.png)

### 4.4.2. **OJB 数据源配置**

中提供的 bean 名称**datasource.xml**必须与位于 OJB中的**jdbc-connection-descriptorjcd-alias**属性（默认情况下）匹配， 如下所示。 **JetspeedDSrepository\_database.xml**

<jdbc-连接描述符

    jcd-alias="JetspeedDS"

    默认连接=“真”

    批处理模式=“假”>
### 4.4.3. **Tomcat 中的 Jetspeed-2 数据源配置**

Jetspeed-2 在 Tomcat 中配置以下数据源。在源代码树中，Tomcat 数据源配置位于**/etc/conf/tomcat**. 在 Tomcat 实例中部署 Jetspeed-2 时，Jetspeed-2 数据源配置部署在**\${tomcat\_home}/conf/Catalina/localhost/jetspeed.xml**. 如果 Jetspeed-2 使用不同的门户名称，配置文件将相应命名。

<资源名称="jdbc/jetspeed" auth="容器"

             factory="org.apache.commons.dbcp.BasicDataSourceFactory"

             类型="javax.sql.DataSource" 用户名=""密码=""

             driverClassName="org.apache.derby.jdbc.EmbeddedDriver"

             url="jdbc:derby:/tmp/productiondb;create=true"

             maxActive="100" maxIdle="30" maxWait="10000"/>
# 5. **APIs**

## 5.1. [**Jetspeed Java API**](https://portals.apache.org/jetspeed-2/apidocs/index.html)

### 5.1.1. [**org.apache.jetspeed**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/package-frame.html)

### 5.1.2. [**org.apache.jetspeed.administration**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/administration/package-frame.html)

### 5.1.3. [**org.apache.jetspeed.aggregator**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/aggregator/package-frame.html)

### 5.1.4. [**org.apache.jetspeed.ajax**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/ajax/package-frame.html)

### 5.1.5. [**org.apache.jetspeed.audit**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/audit/package-frame.html)

### 5.1.6. [**org.apache.jetspeed.cache**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/cache/package-frame.html)

### 5.1.7. [**org.apache.jetspeed.cache.file**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/cache/file/package-frame.html)

### 5.1.8. [**org.apache.jetspeed.cache.general**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/cache/general/package-frame.html)

### 5.1.9. [**org.apache.jetspeed.capabilities**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/capabilities/package-frame.html)

### 5.1.10. [**org.apache.jetspeed.cluster**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/cluster/package-frame.html)

### 5.1.11. [**org.apache.jetspeed.components**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/components/package-frame.html)

### 5.1.12. [**org.apache.jetspeed.components.persistence.store**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/components/persistence/store/package-frame.html)

### 5.1.13. [**org.apache.jetspeed.components.portletentity**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/components/portletentity/package-frame.html)

### 5.1.14. [**org.apache.jetspeed.components.portletpreferences**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/components/portletpreferences/package-frame.html)

### 5.1.15. [**org.apache.jetspeed.components.portletregistry**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/components/portletregistry/package-frame.html)

### 5.1.16. [**org.apache.jetspeed.container**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/container/package-frame.html)

### 5.1.17. [**org.apache.jetspeed.container.invoker**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/container/invoker/package-frame.html)

### 5.1.18. [**org.apache.jetspeed.container.session**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/container/session/package-frame.html)

### 5.1.19. [**org.apache.jetspeed.container.state**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/container/state/package-frame.html)

### 5.1.20. [**org.apache.jetspeed.container.url**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/container/url/package-frame.html)

### 5.1.21. [**org.apache.jetspeed.decoration**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/decoration/package-frame.html)

### 5.1.22. [**org.apache.jetspeed.deployment**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/deployment/package-frame.html)

### 5.1.23. [**org.apache.jetspeed.descriptor**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/descriptor/package-frame.html)

### 5.1.24. [**org.apache.jetspeed.desktop**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/desktop/package-frame.html)

### 5.1.25. [**org.apache.jetspeed.engine**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/engine/package-frame.html)

### 5.1.26. [**org.apache.jetspeed.events**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/events/package-frame.html)

### 5.1.27. [**org.apache.jetspeed.exception**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/exception/package-frame.html)

### 5.1.28. [**org.apache.jetspeed.factory**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/factory/package-frame.html)

### 5.1.29. [**org.apache.jetspeed.headerresource**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/headerresource/package-frame.html)

### 5.1.30. [**org.apache.jetspeed.i18n**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/i18n/package-frame.html)

### 5.1.31. [**org.apache.jetspeed.idgenerator**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/idgenerator/package-frame.html)

### 5.1.32. [**org.apache.jetspeed.layout**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/layout/package-frame.html)

### 5.1.33. [**org.apache.jetspeed.locator**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/locator/package-frame.html)

### 5.1.34. [**org.apache.jetspeed.login**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/login/package-frame.html)

### 5.1.35. [**org.apache.jetspeed.mockobjects**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/mockobjects/package-frame.html)

### 5.1.36. [**org.apache.jetspeed.mockobjects.portlet**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/mockobjects/portlet/package-frame.html)

### 5.1.37. [**org.apache.jetspeed.mockobjects.request**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/mockobjects/request/package-frame.html)

### 5.1.38. [**org.apache.jetspeed.om.common**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/om/common/package-frame.html)

### 5.1.39. [**org.apache.jetspeed.om.folder**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/om/folder/package-frame.html)

### 5.1.40. [**org.apache.jetspeed.om.page**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/om/page/package-frame.html)

### 5.1.41. [**org.apache.jetspeed.om.portlet**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/om/portlet/package-frame.html)

### 5.1.42. [**org.apache.jetspeed.om.preference**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/om/preference/package-frame.html)

### 5.1.43. [**org.apache.jetspeed.openid**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/openid/package-frame.html)

### 5.1.44. [**org.apache.jetspeed.page**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/page/package-frame.html)

### 5.1.45. [**org.apache.jetspeed.page.document**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/page/document/package-frame.html)

### 5.1.46. [**org.apache.jetspeed.pipeline**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/pipeline/package-frame.html)

### 5.1.47. [**org.apache.jetspeed.pipeline.descriptor**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/pipeline/descriptor/package-frame.html)

### 5.1.48. [**org.apache.jetspeed.pipeline.valve**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/pipeline/valve/package-frame.html)

### 5.1.49. [**org.apache.jetspeed.portalsite**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/portalsite/package-frame.html)

### 5.1.50. [**org.apache.jetspeed.portlet**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/portlet/package-frame.html)

### 5.1.51. [**org.apache.jetspeed.profiler**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/profiler/package-frame.html)

### 5.1.52. [**org.apache.jetspeed.profiler.rules**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/profiler/rules/package-frame.html)

### 5.1.53. [**org.apache.jetspeed.request**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/request/package-frame.html)

### 5.1.54. [**org.apache.jetspeed.search**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/search/package-frame.html)

### 5.1.55. [**org.apache.jetspeed.security**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/package-frame.html)

### 5.1.56. [**org.apache.jetspeed.security.activeauthentication**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/security/activeauthentication/package-frame.html)

### 5.1.57. [**org.apache.jetspeed.serializer**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/serializer/package-frame.html)

### 5.1.58. [**org.apache.jetspeed.spaces**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/spaces/package-frame.html)

### 5.1.59. [**org.apache.jetspeed.sso**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/sso/package-frame.html)

### 5.1.60. [**org.apache.jetspeed.statistics**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/statistics/package-frame.html)

### 5.1.61. [**org.apache.jetspeed.tools**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/tools/package-frame.html)

### 5.1.62. [**org.apache.jetspeed.tools.deploy**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/tools/deploy/package-frame.html)

### 5.1.63. [**org.apache.jetspeed.tools.migration**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/tools/migration/package-frame.html)

### 5.1.64. [**org.apache.jetspeed.tools.pamanager**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/tools/pamanager/package-frame.html)

### 5.1.65. [**org.apache.jetspeed.tools.pamanager.servletcontainer**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/tools/pamanager/servletcontainer/package-frame.html)

### 5.1.66. [**org.apache.jetspeed.userinfo**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/userinfo/package-frame.html)

### 5.1.67. [**org.apache.jetspeed.util**](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/util/package-frame.html)

## 5.2. [**Jetspeed AJAX API**](https://portals.apache.org/jetspeed-2/devguide/guide-ajax-api.html)

Jetspeed XML AJAX API 是一个基于 XML 的 API，提供给 AJAX 客户端，用于向 Jetspeed-2 服务发出异步请求。

典型用例：

· **页面定制和 Portlet 放置**- 在页面上移动、复制、添加或删除 Portlet

· **布局选择**- 更改页面上的布局（行数和列数，列的大小）

· **主题和装饰器选择**- 更改页面上的页面主题和 portlet 装饰器。

· **Portlet Selectors** - 为最终用户提供一个 portlet 选择列表

· **安全配置**- 在资源（页面、portlet、文件夹、链接、片段）或门户范围内配置安全约束或策略

· **菜单配置**- 为 Jetspeed 站点创建和编辑菜单

· **一般管理**- 尚未探索一般管理的所有用例。

### 5.2.1. **安全访问**

所有 AJAX XML API 请求都通过标准的 Jetspeed [Pipeline](https://portals.apache.org/jetspeed-2/devguide/guide-pipeline.html)请求运行。这意味着您可以使用通常的 Jetspeed 组件数组配置您的 AJAX 请求。默认的 AJAX 管道保护对所有请求的访问。每个 AJAX 操作都可能有自己的安全约束。对页面发出的所有请求都将使用为该页面配置的声明性安全约束。AJAX 请求操作在编辑或查看模式下强制执行，具体取决于操作的性质。

### 5.2.2. **API**

AJAX XML API 只是一个基于 HTTP 请求的 API，通过简单的 REST（表示状态传输）协议进行通信。API 通过门户 URL 上的“ajaxapi”servlet 路径通过 HTTP 访问：

http://hostname/contextname/ajaxapi

#### 5.2.2.1. **请求参数和页面**

请求参数指定请求的 API 操作和其他 API 参数。请求所引用的页面隐含在 HTTP URL 中。因此，如果我们提出修改页面的请求，该页面在 HTTP URL 中指定：

http://localhost:8080/jetspeed/ajaxapi/Public/db-browser.psml

页面定位算法使用标准的 Jetspeed Profiling 规则来定位页面。URL 中实际上不需要页面，因为[Jetspeed Profiler](https://portals.apache.org/jetspeed-2/devguide/guide-profiler.html)会为您找到该页面。例子：

http://localhost:8080/jetspeed/ajaxapi

转到当前用户的默认页面。

请求参数特定于每个 API。一个请求参数，“action”参数，几乎总是需要的（默认情况除外）。[默认操作是“action=getpage”，它返回PSML](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)中位于配置文件的页面的 XML 表示。（PSML 是一种 XML 格式）。请求参数的具体示例见下表。

以下是当前可用的 API：

#### 5.2.2.2. **获取页面**


| 接口： | 获取页面                                                                                                         |
| ------ | ---------------------------------------------------------------------------------------------------------------- |
| 零件： | AjaxGetPage                                                                                                      |
| 描述： | 获取页面从页面管理器存储中以[PSML](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)格式检索页面。 |
| 参数： |                                                                                                                  |


| 页   | 隐含在URL中                       |
| ---- | --------------------------------- |
| 行动 | getportlets（可选，这是默认操作） |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/Public/content.psml

XML 响应：

<js>

<status>成功</status>

<action>获取页面</action>

<页面隐藏=“假”>

<defaults layout-decorator="tigris" portlet-decorator="tigris"/>

<name>public.psml</name>

<路径>/Public/public.psml</路径>

<title>公开分享</title>

<short-title>公开分享</short-title>

<metadata name="title" xml:lang="es">Carpeta compartida</metadata>

<fragment id="ps-1000" type="layout" name="jetspeed-layouts::VelocityTwoColumns" decorator="">

<fragment id="ps-1001" type="portlet" name="rss::RSS" 装饰器="">

  <属性名称=“行”值=“0”/>

  <property name="column" value="0"/>

</片段>

<fragment id="ps-1002" type="portlet" name="demo::BookmarkPortlet" decorator="">

  <property name="row" value="1"/>

  <property name="column" value="1"/>

</片段>

<fragment id="ps-1003" type="portlet" name="jsf-demo::CalendarPortlet" decorator="">

  <属性名称=“行”值=“0”/>

  <property name="column" value="1"/>

</片段>

<fragment id="P-1080bff9b03-10000" type="portlet" name="jsf-demo::CalendarPortlet" decorator="">

  <property name="row" value="1"/>

  <property name="column" value="0"/>

</片段>
</片段>

</页面>

</js>

#### 5.2.2.3. **绝对移动**


| 接口： | 移动设备                                                      |
| ------ | ------------------------------------------------------------- |
| 零件： | AjaxMovePortletAbsolute                                       |
| 描述： | 将页面上的portlet移动到 row 和 col 请求参数中指定的绝对位置。 |
| 参数： |                                                               |


| 页   | 隐含在URL中                               |
| ---- | ----------------------------------------- |
| 行动 | 移动设备                                  |
| ID   | 要移动的portlet的 portlet PSML 片段 ID    |
| 排   | 放置portlet片段的绝对新行位置（从零开始） |
| 山口 | 放置portlet片段的绝对新列位置（从零开始） |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/Public/public.psml?action=moveabs&id=ps-1003&row=0&col=1

XML 响应：

<js>

<status>成功</status>

<action>moveabs</action>

<id>ps-1003</id>

<旧位置>

  <col>1</col>

  <row>1</row>

</old_position>

<新位置>

  <col>1</col>

  <行>0</行>

</new_position>
</js>

#### 5.2.2.4. **相对移动**


| 蜜蜂： | 左移，右移，上移，下移                                                     |
| ------ | -------------------------------------------------------------------------- |
| 组件： | AjaxMovePortletLeft、AjaxMovePortletRight、AjaxMovePortletUp、AjaxMoveDown |
| 描述： | 根据操作，将页面上的portlet相对移动一个位置。                              |
| 参数： |                                                                            |


| 页   | 隐含在URL中                            |
| ---- | -------------------------------------- |
| 行动 | 左移，右移，上移，下移                 |
| ID   | 要移动的portlet的 portlet PSML 片段 ID |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/Public/public.psml?action=movedown&id=ps-1003

XML 响应：

<js>

<status>成功</status>

<action>下移</action>

<id>ps-1003</id>

<旧位置>

  <col>1</col>

  <行>0</行>

</old_position>

<新位置>

  <col>1</col>

  <row>1</row>

</new_position>
</js>

#### 5.2.2.5. **移动**


| 接口： | 移动                                                                   |
| ------ | ---------------------------------------------------------------------- |
| 零件： | AjaxMovePortlet                                                        |
| 描述： | 根据请求参数将页面上的portlet移动到笛卡尔位置（x、y、z、宽度、高度）。 |
| 参数： |                                                                        |


| 页   | 隐含在URL中                            |
| ---- | -------------------------------------- |
| 行动 | 移动                                   |
| ID   | 要移动的portlet的 portlet PSML 片段 ID |
| X    | portlet笛卡尔 X 位置                   |
| 是的 | portlet笛卡尔 Y 位置                   |
| z    | portlte笛卡尔 Z 位置                   |
| 宽度 | portlet的宽度                          |
| 高度 | 高度笛卡尔Y位置                        |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/Public/public.psml?action=move&id=ps-1003&x=100&y=250&width=200&height=300

XML 响应：

<js>

<status>成功</status>

<action>移动</action>

<id>ps-1003</id>

<旧位置>

  <x>50</x>

  <y>155</row>

</old_position>

<新位置>

  <x>100</x>

  <y>250</y>

</new_position>
</js>

#### 5.2.2.6. **添加 Portlet**


| 接口： | 添加                                                                                            |
| ------ | ----------------------------------------------------------------------------------------------- |
| 零件： | AjaxAddPortlet                                                                                  |
| 描述： | 将新的portlet添加到当前页面。Portlet 可以添加到指定的行和列。如果未指定行或列，则分别默认为零。 |
| 参数： |                                                                                                 |


| 页   | 隐含在URL中                                                                                     |
| ---- | ----------------------------------------------------------------------------------------------- |
| 行动 | 添加                                                                                            |
| ID   | 要放置在页面上的portlet全名，使用 Jetspeed Portlet Naming (PortletApplicationName::PortletName) |
| 排   | 可选：放置新portlet片段的绝对新行位置（从零开始）                                               |
| 山口 | 可选：放置新portlet片段的绝对新列位置（从零开始）                                               |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/Public/public.psml?action=add&id=jsf-demo::CalendarPortlet

XML 响应：

<js>

<status>成功</status>

<action>添加</action>

<id>jsf-demo::CalendarPortlet</id>

<新位置>

<col>0</col>

<行>0</行>
</new_position>

</js>

#### 5.2.2.7. **移除 Portlet**


| 接口： | 消除                              |
| ------ | --------------------------------- |
| 零件： | AjaxRemovePortlet                 |
| 描述： | 从当前页面中删除一个新的portlet。 |
| 参数： |                                   |


| 页   | 隐含在URL中                            |
| ---- | -------------------------------------- |
| 行动 | 消除                                   |
| ID   | 要删除的portlet的 portlet PSML 片段 ID |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/Public/public.psml?action=remove&id=ps-1003

XML 响应：

<js>

<status>成功</status>

<action>删除</action>

<id>jsf-demo::CalendarPortlet</id>

<新位置>

<col>0</col>

<行>0</行>
</new_position>

</js>

#### 5.2.2.8. **获取 Portlet**


| 接口： | 获取portlet                                                                                                                                                                                                           |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 零件： | AjaxGetPortlets                                                                                                                                                                                                       |
| 描述： | Get Portlets检索当前主题可用的（排序的）portlet 列表，过滤 portlet 列表，并返回当前主题可以查看的 portlet。Jetspeed (JAAS) 安全策略强制执行此过滤。Portlet 以 XML 格式返回，带有每个 Portlet 的名称、显示名称和描述。 |
| 参数： |                                                                                                                                                                                                                       |


| 页   | 隐含在URL中                    |
| ---- | ------------------------------ |
| 行动 | 获取portlet                    |
| 筛选 | 尚未实现。要定义的查询过滤器。 |

API 示例：

http://localhost:8080/jetspeed/ajaxapi?action=getportlets

XML 响应：

<js>

<status>成功</status>

<action>getportlets</action>

<portlet>
<portlet name="demo::AttributeScopePortlet" displayName="Attribute Scope Demo" description="$portlet.Description">

    </portlet>
<portlet name="demo::BookmarkPortlet" displayName="Bookmark Portlet" description="Bookmark Portlet">

    </portlet>
<portlet name="demo::BookmarkPortletForXHTMLBasic" displayName="Bookmark Portlet for XHTML Basic" description="Bookmark Portlet for XHTML Basic">

    </portlet>
<portlet name="demo::CSSDemoPortlet" displayName="CSS Demo Portlet" description="$portlet.Description">

    </portlet>
……

<portlet name="rss::RSS" displayName="RSS Portlet" description="RSS Portlet">

    </portlet>
<portlet name="rss::RomeRSS" displayName="Rome RSS Portlet" description="Rome RSS Portlet">

    </portlet>
</portlets>

</js>

#### 5.2.2.9. **权限**


| 接口： | 权限                                                     |
| ------ | -------------------------------------------------------- |
| 零件： | AjaxSecurityPermissions                                  |
| 描述： | 安全权限维护，用于添加、更新和删除Jetspeed安全策略的权限 |
| 参数： |                                                          |


| 行动   | 权限                                         |
| ------ | -------------------------------------------- |
| 方法   | 执行的方法：必须是值：add                    |
| 类型   | 被操作的权限类型：portlet                    |
| 资源   | 被操作的门户资源的名称                       |
| 角色   | 逗号分隔的角色列表，仅对方法有效：添加、更新 |
| 行动   | 逗号分隔的操作列表，仅对方法有效：添加、更新 |
| 旧动作 | 以前操作的逗号分隔列表，仅对方法有效：更新   |

API 示例：

http://localhost:8080/jetspeed/ajaxapi?action=permissions&method=add&type=portlet&resource=demo::*&roles=role1,role2,role3&actions=view,edit

XML 响应：

<js>

<status>成功</status>

<action>权限</action>

<resource>demo::*</resource>

<type>portlet</type>

<actions>查看、编辑</actions>

<actions>role1,role2,role3</actions>    
</js>

#### 5.2.2.10. **获取菜单**


| 接口： | 获取菜单                              |
| ------ | ------------------------------------- |
| 零件： | AjaxGetMenus                          |
| 描述： | 检索当前页面的所有菜单（在URL中隐含） |
| 参数： |                                       |


| 行动 | 获取菜单        |
| ---- | --------------- |
| 页   | （在URL中暗示） |

API 示例：

http://localhost:8080/jetspeed/ajaxapi/default-page.psml?action=getmenus

XML 响应：

<js>

<status>成功</status>

<action>getmenus</action>    

<菜单>

    <menu type="standard">导航</menu>

    <menu type="standard">返回</menu>

    <menu type="standard">页面</menu>

    <menu type="standard">面包屑</menu>

    <menu type="custom">网站导航</menu>

    <menu type="custom">附加链接</menu>

    <menu type="custom">页面导航</menu>

</菜单>
</js>

#### 5.2.2.11. **获取菜单**


| 接口： | 获取菜单               |
| ------ | ---------------------- |
| 零件： | AjaxGetMenu            |
| 描述： | 检索给定菜单的菜单定义 |
| 参数： |                        |


| 行动 | 获取菜单                                 |
| ---- | ---------------------------------------- |
| 菜单 | 要检索的菜单名称（菜单定义可能每页更改） |

API 示例：

http://localhost:8080/jetspeed/ajaxapi?action=getmenu&name=breadcrumbs

XML 响应：

<js>

<status>成功</status>

<action>getmenu</action>

<菜单>

<name>面包屑</name>

<title>你在这里：</title>

<short-title>你在这里：</short-title>

<skin>面包屑</skin>

<url>/default-page.psml</url>

<隐藏>假</隐藏>

<selected>真</selected>

<选项>

<type>文件夹</type>

<title>根文件夹</title>

<short-title>根文件夹</short-title>

<skin>面包屑</skin>

<url>/</url>

<隐藏>假</隐藏>

<selected>真</selected>
</选项>

<选项>

<type>页面</type>

<title>欢迎来到 Jetspeed 2</title>

<short-title>欢迎来到 Jetspeed 2</short-title>

<皮肤>蓝色</皮肤>

<url>/default-page.psml</url>

<隐藏>假</隐藏>

<selected>真</selected>
</选项>

</菜单>

</js>

#### 5.2.2.12. **窗户**


| 接口： | 获取菜单                                 |
| ------ | ---------------------------------------- |
| 零件： | Ajax更改窗口                             |
| 描述： | 更改Portlet窗口的窗口状态或 Portlet 模式 |
| 参数： |                                          |


| 行动 | 窗户                                                        |
| ---- | ----------------------------------------------------------- |
| ID   | 要修改的portlet的窗口 ID                                    |
| 状态 | 一个portlet api有效窗口状态或扩展窗口状态（正常             |
| 模式 | 一个portlet api有效的 portlet 模式或扩展 portlet 模式（查看 |
| 页   | 隐含在URL中                                                 |

API 示例：

http://localhost:8080/jetspeed/ajaxapi?action=window&state=maximized&mode=edit&id=um-2

XML 响应：

<js>

<status>成功</status>

<action>窗口</action>

<id>um-2</id>  

<state>最大化</state>

<mode>编辑</mode>

</js>

#### 5.2.2.13. **获取使用信息**


| 接口： | 获取使用信息                                                                                                                                      |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 零件： | AjaxGetUserInformation                                                                                                                            |
| 描述： | 返回有关当前登录用户的信息。例如，可以在基于AJAX的 portlet 中使用，以更健壮的方式检索用户信息。仅当用户当前登录时才会返回成功，否则将返回 false。 |
| 参数： |                                                                                                                                                   |


| 行动 | 获取用户信息 |
| ---- | ------------ |

API 示例：

http://localhost:8080/jetspeed/ajaxapi?action=getuserinfo

XML 响应：

<js>

<status>成功</status>

<action>用户信息</action>

<用户名>管理员</用户名>

<type>org.apache.jetspeed.security.impl.UserPrincipalImpl</type>

<用户信息>

    <user.name.given>测试伙计</user.name.given>

    <user.name.family>达德利</user.name.family>

</用户信息>
</js>

#### 5.2.2.14. **获取用户列表**


| 接口： | 获取使用信息                                                                                                                                 |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 零件： | AjaxGetUserList                                                                                                                              |
| 描述： | 以xml格式提供有关当前登录用户的基本信息（用户名、IP 地址、会话数和状态）。可选地，它还可以提供更详细的用户信息、访客会话数以及包括离线用户。 |
| 参数： |                                                                                                                                              |


| 行动     | 获取用户信息                               |
| -------- | ------------------------------------------ |
| 用户信息 | 我们是否还应该包含用户信息（true           |
| 离线     | 我们是否应该包括离线用户（true             |
| 客人     | 我们是否也应该返回访客会话（true           |
| 全部     | 如果设置为true，将返回所有的点点滴滴（true |

默认情况下，私有信息（电子邮件等）受到 RolesSecurityBehavior 安全性的保护，但可以在 [AJAX 配置](http://svn.apache.org/viewvc/portals/jetspeed-2/portal/tags/jetspeed-2-2.3.0/jetspeed-portal-resources/src/main/resources/assembly/ajax-layout.xml) 中通过将 protectionScope 构造函数值更改为“all”以保护基本信息或在一切都将保护时更改为“none”向所有人展示（在生产上不明智）。默认值“private”将仅显示在线/离线用户的基本信息和访客会话数，因为“private-offline”甚至不会显示离线用户。可能的 protectionScope 值为“all”、“private-offline”、“private”和“none”。

API 示例：

http://localhost:8080/jetspeed/ajaxapi?action=getuserlist&userinfo=true&guest=true

XML 响应：

<js>

<status>成功</status>

<action>获取用户列表</action>

<用户>

    <用户>

        <用户名>管理员</用户名>

        <会话>1</会话>

        <status>在线</status>

        <ipaddress>127.0.0.1</ipaddress>

        <用户信息>

            <user.name.given>测试伙计</user.name.given>

            <user.name.family>达德利</user.name.family>

        </用户信息>

    </用户>

    <客人>0</客人>

</用户>
</js>

### 5.2.3. **弹簧组件**

这**AjaxRequestService** 是一个处理 AJAX 请求的 Spring 组件。它被挂接到 AJAX[管道](https://portals.apache.org/jetspeed-2/devguide/guide-pipeline.html)中，用于对 AJAX 请求的特殊处理。这是弹簧组件。每个 API 都在 Ajax 服务中进行配置。

<bean id="AjaxRequestService" class="org.apache.jetspeed.ajax.AjaxRequestServiceImpl">

<constructor-arg index="0">

    <地图>

        <进入键=“移动”>

            <ref bean="AjaxMove"/>

        </entry>            

        <entry key="moveabs">

            <ref bean="AjaxMovePortletAbsolute"/>

        </entry>

        <entry key="moveleft">

            <ref bean="AjaxMovePortletLeft"/>

        </entry>

        <entry key="moveright">

            <ref bean="AjaxMovePortletRight"/>

        </entry>

        <entry key="moveup">

            <ref bean="AjaxMovePortletUp"/>

        </entry>

        <entry key="movedown">

            <ref bean="AjaxMovePortletDown"/>

        </entry>

        <入口键=“添加”>

            <ref bean="AjaxAddPortlet"/>

        </entry>

        <entry key="删除">

            <ref bean="AjaxRemovePortlet"/>

        </entry>

        <entry key="getportlets">

            <ref bean="AjaxGetPortlets"/>

        </entry>

        <entry key="getpage">

            <ref bean="AjaxGetPage"/>

        </entry>

        <entry key="getpages">

            <ref bean="AjaxGetPages"/>

        </entry>		

        <entry key="getfolder">

            <ref bean="AjaxGetFolder"/>

        </entry>			          

        <entry key="getlink">

            <ref bean="AjaxGetLink"/>

        </entry>			                      

        <entry key="getfolderlist">

            <ref bean="AjaxGetFolderList"/>

        </entry>			                      

        <entry key="getfolders">

            <ref bean="AjaxGetFoldersList"/>

        </entry>			      					

        <entry key="getthemes">

            <ref bean="AjaxGetThemes"/>

        </entry>

        <entry key="getactions">

            <ref bean="AjaxGetActions"/>

        </entry>

        <进入键=“窗口”>

            <ref bean="AjaxChangeWindow"/>

        </entry>

        <entry key="getmenus">

            <ref bean="AjaxGetMenus"/>

        </entry>			          

        <entry key="getmenu">

            <ref bean="AjaxGetMenu"/>

        </entry>			          

        <entry key="权限">

            <ref bean="AjaxSecurityPermissions"/>

        </entry>			                      

        <entry key="约束">

            <ref bean="AjaxSecurityConstraints"/>

        </entry>			        

        <entry key="updatefolder">

            <ref bean="AjaxUpdateFolder"/>                

        </entry>                          

        <entry key="updatepage">

            <ref bean="AjaxUpdatePage"/>                

        </entry>              

        <entry key="updatelink">

            <ref bean="AjaxUpdateLink"/>                

        </entry>                                                              

        <entry key="getuserinfo">

            <ref bean="AjaxGetUserInformation"/>                

        </entry>

        <entry key="getuserlist">

            <ref bean="AjaxGetUserList"/>                

        </entry>

    </地图>

</constructor-arg>

<constructor-arg index="1">

    <ref bean="AjaxVelocityEngine"/>

</constructor-arg>
</豆>

## 5.3. [**Jetspeed REST API**](https://portals.apache.org/jetspeed-2/devguide/guide-rest-api.html)

Jetspeed REST API 是一个 RESTful Web 服务，用于客户端（包括 AJAX 客户端）向 Jetspeed 服务发出 HTTP 请求。

Jetspeed REST API 的 URL 以以下内容开头：

http://主机名/上下文名/服务/

典型用例：

· **页面定制和 Portlet 放置**- 在页面上移动、复制、添加或删除 Portlet

· **布局选择**- 更改页面上的布局（行数和列数，列的大小）

· **主题和装饰器选择**- 更改页面上的页面主题和 portlet 装饰器。

· **Portlet Selectors** - 为最终用户提供一个 portlet 选择列表

· **安全配置**- 在资源（页面、portlet、文件夹、链接、片段）或门户范围内配置安全约束或策略

· **菜单配置**- 为 Jetspeed 站点创建和编辑菜单

· **一般管理**- 尚未探索一般管理的所有用例。

### 5.3.1. **安全访问**

所有 Jetspeed REST API 请求都通过标准 Jetspeed [Pipeline](https://portals.apache.org/jetspeed-2/devguide/guide-pipeline.html)请求运行。这意味着您可以使用通常的 Jetspeed 组件阵列来配置您的 Web 请求。默认 REST 服务管道可保护对所有请求的访问。每个服务都可能有自己的安全约束。对页面发出的所有请求都将使用为该页面配置的声明性安全约束。REST 请求操作在编辑或查看模式下强制执行，具体取决于操作的性质。

### 5.3.2. **消息生产者和消费者的灵活消息媒体类型**

[在底层**Apache CXF**](http://cxf.apache.org/) JAX-RS 服务器 的帮助下，所有 Jetspeed REST API 都支持消息生产者和消费者的双重消息媒体类型：“application/json”和“application/xml” 。通常，Web 客户端应用程序可以通过在请求 URL 中添加“_type=json”参数来使用 JSON 编组/解组。如果参数是 '_type=xml'，则消息被编组/解组为 XML 消息。如果客户端未设置“_type”参数，Jetspeed REST API 会读取“Accept”HTTP 请求标头以决定哪个适合 Web 客户端。有关详细信息，请参阅 Apache CXF 的文档。

### 5.3.3. **WADL（Web 应用程序描述语言）支持**

您只需添加“?_wadl”查询字符串即可检索每个服务的[WADL](http://www.w3.org/Submission/wadl/)描述。Jetspeed REST API 所依赖的 Apache CXF JAX-RS 服务器自动生成服务的 WADL 描述。例如，您可以为“Portlet Registry Service”的“Get Portlet Application”服务请求以下 URL。

获取 http://localhost:8080/jetspeed/services/portletregistry/application/demo/?_wadl

### 5.3.4. **Portlet 注册服务**

Portlet Registry Service 是一个基于 HTTP 请求的 API，通过简单的 REST（表示状态传输）协议进行通信，提供有关 portlet 应用程序和 portlet 定义的信息和管理功能。通过门户 URL 上的“/services/portletregistry”路径通过 HTTP 访问此服务：

http://hostname/contextname/services/portletregistry/

#### 5.3.4.1. **获取 Portlet 应用程序**


| 进入路径    | /应用/                                          |
| ----------- | ----------------------------------------------- |
| 描述        | 根据路径参数或搜索查询参数获取portlet应用程序。 |
| HTTP方法    | 得到                                            |
| 参数        |                                                 |
| ----------- | -----------                                     |
| 小路        |                                                 |
| 询问        | 询问                                            |
| 询问        | 开始                                            |
| 询问        | 最大限度                                        |

                                                                                                                          |
| REST API示例 | 获取 http://localhost:8080/jetspeed/services/portletregistry/application/demo/?_type=json获取 http://localhost:8080/jetspeed/services/portletregistry/application/?_type=json&query=demo&begin=0&max=10                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| JSON响应示例 | { “开始索引”：-1， “总尺寸”：1， “应用程序”：[ { “名称”：“演示”， "contextPath":"/demo", “应用程序类型”：0， "默认命名空间":"", “修订”：2， “校验和”：2832348922， “显示名称”：[ { "value":"Demoportlets", "lang":"en", "localeString":"en" } ], “说明”：[ { "value":"Demo Portlets 应用程序", "lang":"en", "localeString":"en" } ], “元数据”： { “领域”：[ { “名称”：“标题”， "value":"标题 1", "localeString":"en" }, { “名称”：“标题”， "value":"英文职称", "localeString":"en" } ] }, “容器运行时间选项”：[] } ]}                                                                                                                                                                                                                                                               |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><数据> <beginIndex>-1</beginIndex> <totalSize>1</totalSize> <应用程序> <应用> <applicationType>0</applicationType> <校验和>2832348922</校验和> <containerRuntimeOptions/> <contextPath>/demo</contextPath> <默认命名空间/> <说明> <说明> <lang>zh</lang> <localeString>zh</localeString> <value>演示 Portlets 应用程序</value> </描述> </descriptions> <显示名称> <显示名称> <lang>zh</lang> <localeString>zh</localeString> <value>Demoportlets</value> </显示名称> </displayNames> <元数据> <字段> <字段> <localeString>zh</localeString> <名称>标题</名称> <value>标题 1</value> </字段> <字段> <localeString>zh</localeString> <名称>标题</名称> <value>英文标题</value> </字段> </字段> </元数据> <name>演示</name> <修订>2</修订> </应用> </应用></数据> |

#### 5.3.4.2. **获取 Portlet 定义**


| 进入路径    | /定义/                                  |
| ----------- | --------------------------------------- |
| 描述        | 根据路径参数或查询参数获取portlet定义。 |
| HTTP方法    | 得到                                    |
| 参数        |                                         |
| ----------- | -----------                             |
| 小路        |                                         |
| 询问        | 询问                                    |
| 询问        | 开始                                    |
| 询问        | 最大限度                                |

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| REST API示例 |  获取 http://localhost:8080/jetspeed/services/portletregistry/definition/?_type=json获取 http://localhost:8080/jetspeed/services/portletregistry/definition/?_type=json&begin=0&max=5GET http://localhost:8080/jetspeed/services/portletregistry/definition/?_type=json&begin=0&max=5&query=admin%20%7C%20management获取 http://localhost:8080/jetspeed/services/portletregistry/definition/demo/?_type=json获取 http://localhost:8080/jetspeed/services/portletregistry/definition/demo/?_type=json&begin=0&max=5获取 http://localhost:8080/jetspeed/services/portletregistry/definition/demo/PickANumberPortlet/?_type=json                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| JSON响应示例 | { “开始索引”：-1， “总尺寸”：1， “定义”：[ { "uniqueName":"demo::PickANumberPortlet", "portletName":"PickANumberPortlet", “应用程序名称”：“演示”， "portletIcon":"applications-games.png", “portlet 信息”： { "title":"选择一个数字", “关键词”：“有趣，游戏，挑选” }, “显示名称”：[ { "value":"选数游戏", "lang":"en", "localeString":"en" } ], “说明”：[ { "value":"这个 portlet 运行流行的 'Pick A Number' 猜谜游戏。目标是用最少的猜数猜出 [1..{Range}] 之间的数字", "lang":"en", "localeString":"en" } ], “支持”：[ { "mimeType":"文本/html", “窗口状态”：[]， "portletModes":["view","help","edit","about","edit_defaults","preview","print"] } ], “语言”：[ { "localeString":"en", "title":"选择一个数字", “关键词”：“有趣，游戏，挑选” }, { "localeString":"fr", "title":"选择一个数字", “关键词”：“有趣，游戏，挑选” }, { "localeString":"ja", "title":"数当てゲーム", “关键词”：“有趣，游戏，挑选” } ], “元数据”： { “领域”：[ { “名称”：“标题”， "value":"选择一个数字", "localeString":"en" }, { “名称”：“创作者”， "value":"J2 团队", "localeString":"en" } ] }, "containerRuntimeOptions":[], “初始化参数”：[ { "paramName":"ViewPage", "paramValue":"/WEB-INF/demo/simple/PickANumber.jsp", “说明”：[] }, { "paramName":"帮助页面", "paramValue":"/WEB-INF/demo/simple/PickANumberHelp.jsp", “说明”：[] }, { "paramName":"EditPage", "paramValue":"/WEB-INF/demo/simple/PickANumberEdit.jsp", “说明”：[] }, { "paramName":"portlet-icon", "paramValue":"applications-games.png", “说明”：[] } ] } ]}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><数据> <beginIndex>-1</beginIndex> <totalSize>1</totalSize> <定义> <定义> <applicationName>demo</applicationName> <containerRuntimeOptions/> <说明> <说明> <lang>zh</lang> <localeString>zh</localeString> <值> 这个portlet 运行流行的“Pick A Number”猜谜游戏。目标是以最少的猜测次数猜测 [1..{Range}] 之间的数字 </值> </描述> </descriptions> <显示名称> <显示名称> <lang>zh</lang> <localeString>zh</localeString> <value>选数游戏</value> </显示名称> </displayNames> <初始化参数> <初始化参数> <说明/> <paramName>查看页面</paramName> <paramValue>/WEB-INF/demo/simple/PickANumber.jsp</paramValue> </initParam> <初始化参数> <说明/> <paramName>帮助页面</paramName> <paramValue>/WEB-INF/demo/simple/PickANumberHelp.jsp</paramValue> </initParam> <初始化参数> <说明/> <paramName>编辑页面</paramName> <paramValue>/WEB-INF/demo/simple/PickANumberEdit.jsp</paramValue> </initParam> <初始化参数> <说明/> <paramName>portlet 图标</paramName> <paramValue>applications-games.png</paramValue> </initParam> </initParams> <语言> <语言> <keywords>好玩、游戏、挑选</keywords> <title>选择一个号码</title> <localeString>zh</localeString> </语言> <语言> <keywords>好玩、游戏、挑选</keywords> <title>选择一个号码</title> <localeString>fr</localeString> </语言> <语言> <keywords>好玩、游戏、挑选</keywords> <title>数当てゲーム</title> <localeString>ja</localeString> </语言> </语言> <元数据> <字段> <字段> <localeString>zh</localeString> <名称>标题</名称> <value>选择一个数字</value> </字段> <字段> <localeString>zh</localeString> <name>创作者</name> <value>J2 团队</value> </字段> </字段> </元数据> <portletIcon>applications-games.png</portletIcon> <portlet信息> <keywords>好玩、游戏、挑选</keywords> <title>选择一个号码</title> </portletInfo> <portletName>PickANumberPortlet</portletName> <支持> <支持> <mimeType>文本/html</mimeType> <portlet 模式> <portletMode>查看</portletMode> <portletMode>帮助</portletMode> <portletMode>编辑</portletMode> <portletMode>关于</portletMode> <portletMode>edit_defaults</portletMode> <portletMode>预览</portletMode> <portletMode>打印</portletMode> </portletModes> <windowStates/> </支持> </支持> <uniqueName>demo::PickANumberPortlet</uniqueName> </定义> </定义></数据> |

### 5.3.5. **页面布局服务**

页面布局服务是一个基于 HTTP 请求的 API，通过简单的 REST（代表性状态传输）协议进行通信，提供有关内容页面及其内容片段布局的信息和管理功能。通过门户 URL 上的“/services/pagelayout”路径通过 HTTP 访问此服务：

http://hostname/contextname/services/pagelayout/

#### 5.3.5.1. **获取内容页面**


| 进入路径    | /页/                           |
| ----------- | ------------------------------ |
| 描述        | 获取当前请求上下文的内容页面。 |
| HTTP方法    | 得到                           |
| 参数        |                                |
| ----------- | ------------                   |
| 标题        | X-门户路径                     |

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| HTTP错误     | 在当前内容页面上没有VIEW访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| REST API示例 | 获取 http://localhost:8080/jetspeed/services/pagelayout/page/?_type=json使用以下请求标头： X 门户路径：/jetspeed.psml                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| JSON响应示例 | { "name":"default-page.psml", "id":"/default-page.psml", "路径":"/default-page.psml", "url":"/default-page.psml", "title":"仪表板", "shortTitle":"仪表板", “分段”： { "name":"jetspeed-layouts::VelocityThreeColumns", "属性":{"尺寸":"15%,70%,15%"}, "id":"模板-top2", “类型”：“布局”， “锁定”：真， “片段”：[ { "名称":"j2-admin::SpaceNavigator", “属性”：{“装饰器”：“清除”，“y”：“80.0”，“x”：“12.0”，“jsdesktop”：“分离=真”}， "id":"template-top2.jsSpaceNavigator", "type":"portlet", “锁定”：真， “装饰器”：“清除” }, { "名称":"j2-admin::PageNavigator", "属性":{"z":"201.0","行":"0","宽度":"40.0","高度":"388.0","列":"0","y":" 104.0","x":"1.0"}, "id":"template-top2.jsPageNavigator", "type":"portlet", “锁定”：真 }, { "name":"jetspeed-layouts::VelocityOneColumn", “属性”：{“行”：“0”，“列”：“1”}， "id":"template-top2.page-template.dashboard-1000", “类型”：“布局”， “锁定”：假， “片段”：[ { "名称":"j2-admin::LoginPortlet", “属性”：{“行”：“0”，“列”：“0”}， "id":"template-top2.page-template.dashboard-1000.dashboard-1003", "type":"portlet", “锁定”：假 }, { "name":"j2-admin::LocaleSelector", “属性”：{“行”：“1”，“列”：“0”}， "id":"template-top2.page-template.dashboard-1000.dashboard-1007", "type":"portlet", “锁定”：假 } ] }, { "名称":"j2-admin::JetspeedToolbox", "属性":{"y":"10.0","x":"440.0","jsdesktop":"detached=true"}, "id":"template-top2.jsToolbox", "type":"portlet", “锁定”：真 } ] } }                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| XML响应示例  | <页面> <id>/default-page.psml</id> <name>default-page.psml</name> <路径>/default-page.psml</路径> <shortTitle>仪表板</shortTitle> <title>仪表板</title> <url>/default-page.psml</url> <片段> <id>模板-top2</id> <locked>真</locked> <name>jetspeed-layouts::VelocityThreeColumns</name> <type>布局</type> <属性> <条目> <key>尺寸</key> <value>15%,70%,15%</value> </entry> </属性> <片段> <片段> <decorator>清除</decorator> <id>template-top2.jsSpaceNavigator</id> <locked>真</locked> <name>j2-admin::SpaceNavigator</name> <type>portlet</type> <属性> <条目> <key>装饰器</key> <value>清除</value> </entry> <条目> <key>是</key> <值>80.0</值> </entry> <条目> <key>x</key> <值>12.0</值> </entry> <条目> <key>jsdesktop</key> <value>分离=真</value> </entry> </属性> </片段> <片段> <id>template-top2.jsPageNavigator</id> <locked>真</locked> <name>j2-admin::PageNavigator</name> <type>portlet</type> <属性> <条目> <key>z</key> <value>201.0</value> </entry> <条目> <key>行</key> <值>0</值> </entry> <条目> <key>宽度</key> <值>40.0</值> </entry> <条目> <key>身高</key> <value>388.0</value> </entry> <条目> <key>列</key> <值>0</值> </entry> <条目> <key>是</key> <值>104.0</值> </entry> <条目> <key>x</key> <值>1.0</值> </entry> </属性> </片段> <片段> <id>template-top2.page-template.dashboard-1000</id> <锁定>假</锁定> <name>jetspeed-layouts::VelocityOneColumn</name> <type>布局</type> <属性> <条目> <key>行</key> <值>0</值> </entry> <条目> <key>列</key> <值>1</值> </entry> </属性> <片段> <片段> <id>template-top2.page-template.dashboard-1000.dashboard-1003</id> <锁定>假</锁定> <name>j2-admin::LoginPortlet</name> <type>portlet</type> <属性> <条目> <key>行</key> <值>0</值> </entry> <条目> <key>列</key> <值>0</值> </entry> </属性> </片段> <片段> <id>template-top2.page-template.dashboard-1000.dashboard-1007</id> <锁定>假</锁定> <name>j2-admin::LocaleSelector</name> <type>portlet</type> <属性> <条目> <key>行</key> <值>1</值> </entry> <条目> <key>列</key> <值>0</值> </entry> </属性> </片段> </片段> </片段> <片段> <id>template-top2.jsToolbox</id> <locked>真</locked> <name>j2-admin::JetspeedToolbox</name> <type>portlet</type> <属性> <条目> <key>是</key> <值>10.0</值> </entry> <条目> <key>x</key> <值>440.0</值> </entry> <条目> <key>jsdesktop</key> <value>分离=真</value> </entry> </属性> </片段> </片段> </片段></页面> |

#### 5.3.5.2. **获取内容片段**


| 进入路径    | /分段/                           |
| ----------- | -------------------------------- |
| 描述        | 根据片段ID路径参数获取内容片段。 |
| HTTP方法    | 得到                             |
| 参数        |                                  |
| ----------- | ------------                     |
| 标题        | X-门户路径                       |
| 小路        |                                  |

|
| HTTP错误     | 在当前内容页面上没有VIEW访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                 |
| REST API示例 | 获取 http://localhost:8080/jetspeed/services/pagelayout/fragment/template-top2.page-template.dashboard-1000.dashboard-1003/?_type=json使用以下请求标头： X 门户路径：/jetspeed.psml                                                                        |
| JSON响应示例 | { "名称":"j2-admin::LoginPortlet", "id":"template-top2.page-template.dashboard-1000.dashboard-1003", "type":"portlet", “锁定”：假， “属性”：{“行”：“0”，“列”：“2”}}                                                                            |
| XML响应示例  | <片段> <id>template-top2.page-template.dashboard-1000.dashboard-1003</id> <锁定>假</锁定> <name>j2-admin::LoginPortlet</name> <type>portlet</type> <属性> <条目> <key>行</key> <值>0</值> </entry> <条目> <key>列</key> <值>2</值> </entry> </属性></片段> |

#### 5.3.5.3. **添加内容片段**


| 进入路径    | /分段/                                                              |
| ----------- | ------------------------------------------------------------------- |
| 描述        | 根据片段类型路径参数和portlet名称路径参数将内容片段添加到内容页面。 |
| HTTP方法    | 邮政                                                                |
| 参数        |                                                                     |
| ----------- | ------------                                                        |
| 标题        | X-门户路径                                                          |
| 小路        |                                                                     |
| 询问        | 排                                                                  |
| 询问        | 山口                                                                |
| 询问        | 明罗斯科尔                                                          |

|
| HTTP错误     | 在当前内容页面上没有EDIT访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| REST API示例 | POST http://localhost:8080/jetspeed/services/pagelayout/fragment/portlet/demo::PickANumberPortlet/?_type=json使用以下请求标头： X 门户路径：/default-page.psml                                                                                                                                                                                                                                                                                                                                     |
| JSON响应示例 | { "name":"demo::PickANumberPortlet", "id":"template-top2.page-template.dashboard-1000.P-125fec68f7c-10000", "type":"portlet", “锁定”：假， “属性”：{“行”：“2”，“列”：“2”}}                                                                                                                                                                                                                                                                                                             |
| XML响应示例  | <片段> <id>template-top2.page-template.dashboard-1000.P-125fec68f7c-10000</id> <锁定>假</锁定> <name>demo::PickANumberPortlet</name> <type>portlet</type> <属性> <条目> <key>行</key> <值>2</值> </entry> <条目> <key>列</key> <值>2</值> </entry> </属性></片段>                                                                                                                                                                                                                                  |

#### 5.3.5.4. **删除内容片段**


| 进入路径    | /分段/                                     |
| ----------- | ------------------------------------------ |
| 描述        | 根据分片ID路径参数删除内容页面的内容分片。 |
| HTTP方法    | 删除                                       |
| 参数        |                                            |
| ----------- | ------------                               |
| 标题        | X-门户路径                                 |
| 小路        |                                            |

       |
| HTTP错误     | 在当前内容页面上没有EDIT访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                        |
| REST API示例 | 删除 http://localhost:8080/jetspeed/services/pagelayout/fragment/template-top2.page-template.dashboard-1000.P-125fac24b80-10000/?_type=json使用以下请求标头： X 门户路径：/default-page.psml                                                                      |
| JSON响应示例 | { "name":"demo::PickANumberPortlet", "id":"template-top2.page-template.dashboard-1000.P-125fec68f7c-10000", "type":"portlet", “锁定”：假， “属性”：{“行”：“2”，“列”：“2”}}                                                                            |
| XML响应示例  | <片段> <id>template-top2.page-template.dashboard-1000.P-125fec68f7c-10000</id> <锁定>假</锁定> <name>demo::PickANumberPortlet</name> <type>portlet</type> <属性> <条目> <key>行</key> <值>2</值> </entry> <条目> <key>列</key> <值>2</值> </entry> </属性></片段> |

#### 5.3.5.5. **移动内容片段**


| 进入路径    | /fragment/{id}/pos/*注意：“{id}”必须替换为片段 ID 路径参数。* |
| ----------- | --------------------------------------------------------------- |
| 描述        | 根据查询参数移动内容片段。                                      |
| HTTP方法    | 放                                                              |
| 参数        |                                                                 |
| ----------- | ------------                                                    |
| 标题        | X-门户路径                                                      |
| 小路        |                                                                 |
| 询问        | 布局                                                            |
| 询问        | 目录                                                            |
| 询问        | 排                                                              |
| 询问        | 山口                                                            |
| 询问        | X                                                               |
| 询问        | 是的                                                            |
| 询问        | z                                                               |
| 询问        | w                                                               |
| 询问        | H                                                               |

|
| HTTP错误     | 在当前内容页面上没有EDIT访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| REST API示例 | PUT http://localhost:8080/jetspeed/services/pagelayout/fragment/template-top2.page-template.dashboard-1000.dashboard-1007/pos/?_type=json&col=0&row=0使用以下请求标头： X 门户路径：/default-page.psml                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| JSON响应示例 | { "name":"j2-admin::LocaleSelector", "id":"template-top2.page-template.dashboard-1000.dashboard-1007", "type":"portlet", “锁定”：假， “属性”：{“行”：“1”，“列”：“2”}}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| XML响应示例  | <片段> <id>template-top2.page-template.dashboard-1000.dashboard-1007</id> <锁定>假</锁定> <name>j2-admin::LocaleSelector</name> <type>portlet</type> <属性> <条目> <key>行</key> <值>1</值> </entry> <条目> <key>列</key> <值>2</值> </entry> </属性></片段>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

#### 5.3.5.6. **更改 Content Fragment 上的 portlet 模式和窗口状态**


| 进入路径    | /fragment/{id}/mod/*注意：“{id}”必须替换为片段 ID 路径参数。* |
| ----------- | --------------------------------------------------------------- |
| 描述        |                                                                 |
| HTTP方法    | 放                                                              |
| 参数        |                                                                 |
| ----------- | ------------                                                    |
| 标题        | X-门户路径                                                      |
| 小路        |                                                                 |
| 询问        | 模式                                                            |
| 询问        | 状态                                                            |

|
| HTTP错误     | 在当前内容页面上没有EDIT访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                                                                                                                          |
| REST API示例 | PUT http://localhost:8080/jetspeed/services/pagelayout/fragment/template-top2.page-template.dashboard-1000.dashboard-1007/mode/?_type=json&mode=View&state=Normal使用以下请求标头： X 门户路径：/default-page.psml                                                                                                                                                  |
| JSON响应示例 | { "name":"j2-admin::LocaleSelector", "id":"template-top2.page-template.dashboard-1000.dashboard-1007", "type":"portlet", "模式":"视图", “状态”：“正常”， “锁定”：假， “属性”：{“行”：“1”，“列”：“2”}}                                                                                                                                               |
| XML响应示例  | <片段> <id>template-top2.page-template.dashboard-1000.dashboard-1007</id> <锁定>假</锁定> <name>j2-admin::LocaleSelector</name> <type>portlet</type> <mode>查看</mode> <state>正常</state> <属性> <条目> <key>行</key> <值>1</值> </entry> <条目> <key>列</key> <值>2</值> </entry> </属性></片段>                                                                  |

#### 5.3.5.7. **获取内容片段的装饰**


| 进入路径    | /装饰/片段/                            |
| ----------- | -------------------------------------- |
| 描述        | 根据片段ID路径参数检索内容片段的装饰。 |
| HTTP方法    | 得到                                   |
| 参数        |                                        |
| ----------- | ------------                           |
| 标题        | X-门户路径                             |
| 小路        |                                        |

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| HTTP错误     | 在当前内容页面上没有VIEW访问权限时，HTTP 错误 403 被禁止。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| REST API示例 | 获取 http://localhost:8080/jetspeed/services/pagelayout/decoration/fragment/template-top2.page-template.dashboard-1000.dashboard-1007/pos/?_type=json使用以下请求标头： X 门户路径：/default-page.psml                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| JSON响应示例 | { “名称”：“喷气速度”， "basePath":"/decorations/portlet/jetspeed", "actionsOption":"SHOW", "styleSheet":"decorations/portlet/jetspeed/css/styles.css", "baseCSSClass":"jetspeed", “装饰动作”：[ { "名称":"配置", "link":"decorations/portlet/jetspeed/images/config.gif", “行动”：“http://localhost:8080/jetspeed/services/_ns:YXRlbXBsYXRlLXRvcDIucGFnZS10ZW1wbGF0ZS5kYXNoYm9hcmQtMTAwMC5kYXNoYm9hcmQtMTAwM3xjNA__/”， "actionType":"模式", "actionName":"配置", "alt":"配置" }, { "name":"最小化", "link":"decorations/portlet/jetspeed/images/minimized.gif", “行动”：“http://localhost:8080/jetspeed/services/_ns:YXRlbXBsYXRlLXRvcDIucGFnZS10ZW1wbGF0ZS5kYXNoYm9hcmQtMTAwMC5kYXNoYm9hcmQtMTAwM3xkMQ__/”， "actionType":"状态", "actionName":"最小化", "alt":"最小化" }, { "name":"最大化", "link":"decorations/portlet/jetspeed/images/maximized.gif", “行动”：“http://localhost:8080/jetspeed/services/_ns:YXRlbXBsYXRlLXRvcDIucGFnZS10ZW1wbGF0ZS5kYXNoYm9hcmQtMTAwMC5kYXNoYm9hcmQtMTAwM3xkMg__/”， "actionType":"状态", "actionName":"最大化", "alt":"最大化" } ]}                                                                                                                                                                                                                                       |
| XML响应示例  | <装饰> <name>喷气机速度</name> <actionsOption>显示</actionsOption> <baseCSSClass>jetspeed</baseCSSClass> <basePath>/decorations/portlet/jetspeed</basePath> <styleSheet>decorations/portlet/jetspeed/css/styles.css</styleSheet> <装饰器操作> <装饰器动作> <action>http://localhost:8080/jetspeed/services/_ns:YXRlbXBsYXRlLXRvcDIucGFnZS10ZW1wbGF0ZS5kYXNoYm9hcmQtMTAwMC5kYXNoYm9hcmQtMTAwM3xjNA__/</action> <actionName>配置</actionName> <actionType>模式</actionType> <alt>配置</alt> <link>decorations/portlet/jetspeed/images/config.gif</link> <name>配置</name> </decoratorAction> <装饰器动作> <action>http://localhost:8080/jetspeed/services/_ns:YXRlbXBsYXRlLXRvcDIucGFnZS10ZW1wbGF0ZS5kYXNoYm9hcmQtMTAwMC5kYXNoYm9hcmQtMTAwM3xkMQ__/</action> <actionName>最小化</actionName> <actionType>状态</actionType> <alt>最小化</alt> <link>decorations/portlet/jetspeed/images/minimized.gif</link> <name>最小化</name> </decoratorAction> <装饰器动作> <action>http://localhost:8080/jetspeed/services/_ns:YXRlbXBsYXRlLXRvcDIucGFnZS10ZW1wbGF0ZS5kYXNoYm9hcmQtMTAwMC5kYXNoYm9hcmQtMTAwM3xkMg__/</action> <actionName>最大化</actionName> <actionType>状态</actionType> <alt>最大化</alt> <link>decorations/portlet/jetspeed/images/maximized.gif</link> <name>最大化</name> </decoratorAction> </decoratorActions></装饰> |

### 5.3.6. **页面管理服务**

页面管理服务是一个基于 HTTP 请求的 API，通过简单的 REST（代表性状态传输）协议进行通信，在门户页面节点（例如页面、文件夹和链接）上提供信息和管理功能。通过门户 URL 上的“/services/pagemanagement”路径通过 HTTP 访问此服务：

http://hostname/contextname/services/pagemanagement/

节点：本服务的所有操作只允许对目标节点有编辑权限的人进行。只有拥有查看权限的用户会收到** HTTP **错误 403 Forbidden。

#### 5.3.6.1. **获取节点**


| 进入路径    | /                                |
| ----------- | -------------------------------- |
| 描述        | 根据类型参数和路径参数获取节点。 |
| HTTP方法    | 得到                             |
| 参数        |                                  |
| ----------- | -----------                      |
| 小路        |                                  |
| 小路        |                                  |

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| REST API示例 | 获取 http://localhost:8080/jetspeed/services/pagemanagement/.psml/default-page.psml?_type=json                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| JSON响应示例 | { "id":"/default-page.psml", "name":"default-page.psml", “类型”：“.psml”， "路径":"/default-page.psml", "title":"欢迎来到 Jetspeed", "shortTitle":"欢迎来到 Jetspeed", “隐藏”：假， "url":"/default-page.psml", “约束启用”：真， “权限启用”：假， "有效的DefaultLayoutDecorator":"jetspeed", "effectiveDefaultPortletDecorator":"jetspeed", “脏”：假， “元数据”： { “领域”：[ { “名称”：“标题”， "value":"欢迎来到 Jetspeed", "localeString":"en" }, { “名称”：“标题”， "value":"Bienvenido a Jetspeed 2", "localeString":"es" } ] }}                                                                                                                                                                                                                                                            |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><页面> <id>/default-page.psml</id> <name>default-page.psml</name> <type>.psml</type> <路径>/default-page.psml</路径> <title>欢迎来到 Jetspeed</title> <shortTitle>欢迎来到 Jetspeed</shortTitle> <隐藏>假</隐藏> <url>/default-page.psml</url> <constraintsEnabled>真</constraintsEnabled> <permissionsEnabled>假</permissionsEnabled> <effectiveDefaultLayoutDecorator>jetspeed</effectiveDefaultLayoutDecorator> <effectiveDefaultPortletDecorator>jetspeed</effectiveDefaultPortletDecorator> <dirty>假</dirty> <元数据> <字段> <字段> <localeString>fr</localeString> <名称>标题</名称> <value>Jetspeed 两地</value> </字段> <字段> <localeString>es</localeString> <名称>标题</名称> <value>Bienvenido a Jetspeed 2</value> </字段> </字段> </元数据></页面> |

#### 5.3.6.2. **删除节点**


| 进入路径    | /                                |
| ----------- | -------------------------------- |
| 描述        | 根据类型参数和路径参数删除节点。 |
| HTTP方法    | 得到                             |
| 参数        |                                  |
| ----------- | -----------                      |
| 小路        |                                  |
| 小路        |                                  |

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| REST API示例 | 删除 http://localhost:8080/jetspeed/services/pagemanagement/.psml/default-page.psml?_type=json                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| JSON响应示例 | { "id":"/default-page.psml", "name":"default-page.psml", “类型”：“.psml”， "路径":"/default-page.psml", "title":"欢迎来到 Jetspeed", "shortTitle":"欢迎来到 Jetspeed", “隐藏”：假， "url":"/default-page.psml", “约束启用”：真， “权限启用”：假， "有效的DefaultLayoutDecorator":"jetspeed", "effectiveDefaultPortletDecorator":"jetspeed", “脏”：假， “元数据”： { “领域”：[ { “名称”：“标题”， "value":"欢迎来到 Jetspeed", "localeString":"en" }, { “名称”：“标题”， "value":"Bienvenido a Jetspeed 2", "localeString":"es" } ] }}                                                                                                                                                                                                                                                            |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><页面> <id>/default-page.psml</id> <name>default-page.psml</name> <type>.psml</type> <路径>/default-page.psml</路径> <title>欢迎来到 Jetspeed</title> <shortTitle>欢迎来到 Jetspeed</shortTitle> <隐藏>假</隐藏> <url>/default-page.psml</url> <constraintsEnabled>真</constraintsEnabled> <permissionsEnabled>假</permissionsEnabled> <effectiveDefaultLayoutDecorator>jetspeed</effectiveDefaultLayoutDecorator> <effectiveDefaultPortletDecorator>jetspeed</effectiveDefaultPortletDecorator> <dirty>假</dirty> <元数据> <字段> <字段> <localeString>fr</localeString> <名称>标题</名称> <value>Jetspeed 两地</value> </字段> <字段> <localeString>es</localeString> <名称>标题</名称> <value>Bienvenido a Jetspeed 2</value> </字段> </字段> </元数据></页面> |

#### 5.3.6.3. **复制节点**


| 进入路径    | /复制/                                       |
| ----------- | -------------------------------------------- |
| 描述        | 根据类型参数、路径参数和表单请求参数复制节点 |
| HTTP方法    | 得到                                         |
| 参数        |                                              |
| ----------- | -----------                                  |
| 小路        |                                              |
| 小路        |                                              |
| 形式        | 目标                                         |
| 形式        | 深的                                         |
| 形式        | 合并                                         |
| 形式        | 所有者                                       |
| 形式        | 复制品                                       |

                                                                                                                                                                                            |
| REST API示例 | POST http://localhost:8080/jetspeed/services/pagemanagement/copy/.psml/default-page.psml?_type=json使用以下请求表单参数： target=/Examples/default-page.psml&deep=true&merge=true©ids=false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| JSON响应示例 | { "id":"/Examples/default-page.psml", "name":"default-page.psml", “类型”：“.psml”， "路径":"/Examples/default-page.psml", "title":"欢迎来到 Jetspeed", "shortTitle":"欢迎来到 Jetspeed", “隐藏”：假， "url":"/Examples/default-page.psml", “约束启用”：真， “权限启用”：假， "有效的DefaultLayoutDecorator":"jetspeed", "effectiveDefaultPortletDecorator":"jetspeed", “脏”：假， “元数据”： { “领域”：[ { “名称”：“标题”， "value":"欢迎来到 Jetspeed", "localeString":"en" }, { “名称”：“标题”， "value":"Bienvenido a Jetspeed 2", "localeString":"es" } ] }}                                                                                                                                                                                                                                                            |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><页面> <id>/Examples/default-page.psml</id> <name>default-page.psml</name> <type>.psml</type> <path>/Examples/default-page.psml</path> <title>欢迎来到 Jetspeed</title> <shortTitle>欢迎来到 Jetspeed</shortTitle> <隐藏>假</隐藏> <url>/Examples/default-page.psml</url> <constraintsEnabled>真</constraintsEnabled> <permissionsEnabled>假</permissionsEnabled> <effectiveDefaultLayoutDecorator>jetspeed</effectiveDefaultLayoutDecorator> <effectiveDefaultPortletDecorator>jetspeed</effectiveDefaultPortletDecorator> <dirty>假</dirty> <元数据> <字段> <字段> <localeString>fr</localeString> <名称>标题</名称> <value>Jetspeed 两地</value> </字段> <字段> <localeString>es</localeString> <名称>标题</名称> <value>Bienvenido a Jetspeed 2</value> </字段> </字段> </元数据></页面> |

#### 5.3.6.4. **移动节点**


| 进入路径    | /移动/                                       |
| ----------- | -------------------------------------------- |
| 描述        | 根据类型参数、路径参数和表单请求参数移动节点 |
| HTTP方法    | 得到                                         |
| 参数        |                                              |
| ----------- | -----------                                  |
| 小路        |                                              |
| 小路        |                                              |
| 形式        | 目标                                         |
| 形式        | 深的                                         |
| 形式        | 合并                                         |
| 形式        | 所有者                                       |
| 形式        | 复制品                                       |

                                                                                                                                                                                                        |
| REST API示例 | POST http://localhost:8080/jetspeed/services/pagemanagement/move/.psml/default-page.psml?_type=json使用以下请求表单参数： target=/Examples/default-page.psml&deep=true&merge=true©ids=false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| JSON响应示例 | { "id":"/Examples/default-page.psml", "name":"default-page.psml", “类型”：“.psml”， "路径":"/Examples/default-page.psml", "title":"欢迎来到 Jetspeed", "shortTitle":"欢迎来到 Jetspeed", “隐藏”：假， "url":"/Examples/default-page.psml", “约束启用”：真， “权限启用”：假， "有效的DefaultLayoutDecorator":"jetspeed", "effectiveDefaultPortletDecorator":"jetspeed", “脏”：假， “元数据”： { “领域”：[ { “名称”：“标题”， "value":"欢迎来到 Jetspeed", "localeString":"en" }, { “名称”：“标题”， "value":"Bienvenido a Jetspeed 2", "localeString":"es" } ] }}                                                                                                                                                                                                                                                            |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><页面> <id>/Examples/default-page.psml</id> <name>default-page.psml</name> <type>.psml</type> <path>/Examples/default-page.psml</path> <title>欢迎来到 Jetspeed</title> <shortTitle>欢迎来到 Jetspeed</shortTitle> <隐藏>假</隐藏> <url>/Examples/default-page.psml</url> <constraintsEnabled>真</constraintsEnabled> <permissionsEnabled>假</permissionsEnabled> <effectiveDefaultLayoutDecorator>jetspeed</effectiveDefaultLayoutDecorator> <effectiveDefaultPortletDecorator>jetspeed</effectiveDefaultPortletDecorator> <dirty>假</dirty> <元数据> <字段> <字段> <localeString>fr</localeString> <名称>标题</名称> <value>Jetspeed 两地</value> </字段> <字段> <localeString>es</localeString> <名称>标题</名称> <value>Bienvenido a Jetspeed 2</value> </字段> </字段> </元数据></页面> |

#### 5.3.6.5. **更新节点信息**


| 进入路径    | /信息/                                           |
| ----------- | ------------------------------------------------ |
| 描述        | 根据类型参数、路径参数和表单请求参数更新节点信息 |
| HTTP方法    | 得到                                             |
| 参数        |                                                  |
| ----------- | -----------                                      |
| 小路        |                                                  |
| 小路        |                                                  |
| 形式        | 标题                                             |
| 形式        | 短标题                                           |
| 形式        | 隐                                               |
| 形式        | 皮肤                                             |
| 形式        | 版本                                             |
| 形式        | 记录仪                                           |
| 形式        | 网址                                             |

                                                          |
| REST API示例 | POST http://localhost:8080/jetspeed/services/pagemanagement/info/.psml/default-page.psml?_type=json使用以下请求表单参数： title=欢迎来到 Jetspeed-2 企业门户                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| JSON响应示例 | { "id":"/Examples/default-page.psml", "name":"default-page.psml", “类型”：“.psml”， "路径":"/Examples/default-page.psml", "title":"欢迎使用 Jetspeed-2 企业门户", "shortTitle":"欢迎来到 Jetspeed", “隐藏”：假， "url":"/Examples/default-page.psml", “约束启用”：真， “权限启用”：假， "有效的DefaultLayoutDecorator":"jetspeed", "effectiveDefaultPortletDecorator":"jetspeed", “脏”：假， “元数据”： { “领域”：[ { “名称”：“标题”， "value":"欢迎来到 Jetspeed", "localeString":"en" }, { “名称”：“标题”， "value":"Bienvenido a Jetspeed 2", "localeString":"es" } ] }}                                                                                                                                                                                                                                                            |
| XML响应示例  | <?xml version="1.0" encoding="UTF-8" Standalone="yes"?><页面> <id>/Examples/default-page.psml</id> <name>default-page.psml</name> <type>.psml</type> <path>/Examples/default-page.psml</path> <title>欢迎使用 Jetspeed-2 企业门户</title> <shortTitle>欢迎来到 Jetspeed</shortTitle> <隐藏>假</隐藏> <url>/Examples/default-page.psml</url> <constraintsEnabled>真</constraintsEnabled> <permissionsEnabled>假</permissionsEnabled> <effectiveDefaultLayoutDecorator>jetspeed</effectiveDefaultLayoutDecorator> <effectiveDefaultPortletDecorator>jetspeed</effectiveDefaultPortletDecorator> <dirty>假</dirty> <元数据> <字段> <字段> <localeString>fr</localeString> <名称>标题</名称> <value>Jetspeed 两地</value> </字段> <字段> <localeString>es</localeString> <名称>标题</名称> <value>Bienvenido a Jetspeed 2</value> </字段> </字段> </元数据></页面> |

### 5.3.7. **弹簧组件**

Jetspeed REST 服务在 Spring Assembly 中配置。这是 Spring Assembly 的核心部分。每个服务组件都在资源提供程序中进行配置。

<!--

    内部服务器工厂。

    每个 JAX-RS 服务组件都由“resourceProvider”属性注册。

  -->

<bean id="cxfJaxrsServerFactoryBean" class="org.apache.cxf.jaxrs.JAXRSServerFactoryBean">

<meta key="j2:cat" value="default" />

<property name="地址" value="/" />

<property name="destinationFactory" ref="cxfDestinationFactory" />

<property name="providers">

  <列表>

    <ref bean="jaxrsJsonProvider" />

  </列表>

</属性>

<property name="resourceProviders">

  <列表>

    <bean class="org.apache.cxf.jaxrs.lifecycle.SingletonResourceProvider">

      <meta key="j2:cat" value="default" />

      <constructor-arg ref="jaxrsPortletRegistryService" />

    </豆>

    <bean class="org.apache.cxf.jaxrs.lifecycle.SingletonResourceProvider">

      <meta key="j2:cat" value="default" />

      <constructor-arg ref="jaxrsPageLayoutService" />

    </豆>

    <bean class="org.apache.cxf.jaxrs.lifecycle.SingletonResourceProvider">

      <meta key="j2:cat" value="default" />

      <constructor-arg ref="jaxrsPageManagementService" />

    </豆>

  </列表>

</属性>
</豆>

<!-- Portlet 注册 JAX-RS 服务 -->

<bean id="jaxrsPortletRegistryService" class="org.apache.jetspeed.services.rest.PortletRegistryService">

<meta key="j2:cat" value="default" />

<constructor-arg ref="org.apache.jetspeed.security.SecurityAccessController" />

<constructor-arg ref="org.apache.jetspeed.components.portletregistry.PortletRegistry" />

<constructor-arg ref="org.apache.jetspeed.search.SearchEngine" />
</豆>

<!-- 门户页面布局管理 JAX-RS 服务 -->

<bean id="jaxrsPageLayoutService" class="org.apache.jetspeed.services.rest.PageLayoutService">

<meta key="j2:cat" value="default" />

<constructor-arg ref="org.apache.jetspeed.layout.PageLayoutComponent" />

<constructor-arg ref="org.apache.jetspeed.components.portletregistry.PortletRegistry" />

<constructor-arg ref="PortletActionSecurityBehavior" />
</豆>

<!-- 门户页面管理 JAX-RS 服务 -->

<bean id="jaxrsPageManagementService" class="org.apache.jetspeed.services.rest.PageManagementService">

<meta key="j2:cat" value="default" />

<constructor-arg ref="org.apache.jetspeed.page.PageManager" />
</豆>

# 6. **Portlet 编程**

## 6.1. **eclipse**

### 6.1.1. **Eclipse 类路径**

编译、调试、外部依赖、源代码完成、搜索、自动导入，都依赖于正确配置的类路径。首次创建项目时，会在项目根目录中创建一个 .classpath 文件。通过 Jetspeed 源代码，我们为您提供了一个现成的 Eclipse .classpath 文件。我们已经为您配置了相对源目录。Eclipse 通过 Project->Properties 菜单选项提供了一个 .classpath GUI 编辑器。

### 6.1.2. **JAR 文件和 Maven-1 存储库**

Jetspeed 需要相当多的 JAR 文件才能编译。Jetspeed 附带的 .classpath 文件设置为从本地 Maven-1 存储库中获取其 JAR 文件。您可以从 Eclipse 中查看所有 JAR 文件依赖项。转到项目-> 属性-> Java 构建路径-> 库。请注意，所有 JAR 文件都配置为 VARIABLE 库条目。举一个例子：

                MAVEN_REPO/commons-lang/jars/commons-lang-2.0.jar                            

			
变量是部分是 MAVEN\_REPO。扩展部分是 /commons-lang/jars/commons-lang-2.0.jar Eclipse 从变量位置根目录定位 JAR 依赖项。为了让这个类路径正常工作，变量 root 依赖于 Maven-1 本地存储库文件结构。

要配置 MAVEN\_REPO 变量，请转到 Window->Preferences->Java->Build Path->Classpath Variables，单击 New，然后定义一个名为 MAVEN_REPO 的新变量，将其指向本地 Maven-1 存储库的根目录，通常像你的 $HOME/.maven/repository 这样的地方。

### 6.1.3. **JAR 文件和 Maven-2 存储库**

相同的过程适用于本地 Maven-2 存储库。**我们在etc/editors/m2.classpath**下的源代码中提供了一个替代的 .classpath 文件。将 m2.classpath 复制到项目根目录中的 .classpath 文件上。

这个类路径需要一个不同的 Eclipse 类路径变量：M2_REPO。要配置 M2_REPO 变量，请转到 Window->Preferences->Java->Build Path->Classpath Variables，单击 New，然后定义一个名为 MAVEN_REPO 的新变量，将其指向本地 Maven-2 存储库的根目录，通常像你的 $HOME/.m2/repository 这样的地方。

### 6.1.4. **使用 Eclipse 和 Tomcat 进行调试**

在 Tomcat 上运行的 Jetspeed 门户的远程调试要求您启动 Tomcat 并启用调试。这是一个可用于调试的 shell 脚本：

导出 JPDA_TRANSPORT=dt_socket

导出 JPDA_ADDRESS=8000

./catalina.sh jpda 开始

<p>一个 DOS 脚本：</p>

设置 JPDA_TRANSPORT=dt_socket

设置 JPDA_ADDRESS=8000

卡特琳娜 jpda 开始

从那里，只需按照有关如何远程调试的 Eclipse 文档进行操作。

## 6.2. [**Portlet 桥接器**](https://portals.apache.org/jetspeed-2/devguide/guide-portlet-bridges.html)

Portals Bridges 项目为 Struts 提供了一个 Portlet 桥，可与 Jetspeed 2 一起使用。请访问[Apache Portals Struts Portlet Bridge](http://portals.apache.org/bridges/multiproject/portals-bridges-struts/index.html) 子项目文档。

Bridges 项目还提供了一个很棒的 Struts Portlet 演示应用程序：

· iBATIS JPetstore [Demo Portlet](http://portals.apache.org/bridges/multiproject/jpetstore/index.html)应用程序

### 6.2.1. **JSF Portlet 桥**

Portals Bridges 项目为 JSF 提供了一个 Portlet 桥，可与 Jetspeed 2 一起使用。请访问[Apache Portals JSF Portlet Bridge](http://portals.apache.org/bridges/multiproject/portals-bridges-jsf/index.html) 子项目文档。

Portals Bridges 还提供了一个基于 MyFaces JSF 实现的 JSF portlet 演示应用程序：

· 使用 Apache Portal JSF Portlet Bridge的[JSF Portlet 演示应用程序](http://portals.apache.org/bridges/multiproject/jsf-demo/index.html)

### 6.2.2. **Velocity Portlet 桥**

Portals Bridges 项目为 Velocity 提供了一个 Portlet 桥，它在 Jetspeed 2 本身中被广泛使用。请访问[Apache Portals Velocity Portlet Bridge](http://portals.apache.org/bridges/multiproject/portals-bridges-velocity/index.html) 子项目文档。

### 6.2.3. **Perl Portlet 桥**

Portals Bridges 项目为 Perl 应用程序提供了一个 Portlet 桥。请访问[Apache Portals Perl Portlet Bridge](http://portals.apache.org/bridges/multiproject/portals-bridges-perl/index.html) 子项目文档。

### 6.2.4. **PHP Portlet 桥**

Portals Bridges 项目为 PHP 应用程序提供了一个 Portlet 桥。请访问[Apache Portals PHP Portlet Bridge](http://portals.apache.org/bridges/multiproject/portals-bridges-php/index.html) 子项目文档。

## 6.3. [**简单的 Portlet**](https://portals.apache.org/jetspeed-2/devguide/guide-simple-portlet.html)

本指南提供了创建一个非常简单的 portlet 的教程。Portlet 开发人员应遵循以下步骤。

### 6.3.1. **1. Portlet 类**

在名为 simplest/WEB-INF/classes 的目录中创建文件 Simplest.java：

公共类 Simplest 扩展 javax.portlet.GenericPortlet

{

public void doView（javax.portlet.RenderRequest 请求，javax.portlet.RenderResponse 响应）

            抛出 javax.portlet.PortletException、java.io.IOException

{

        response.setContentType("text/html");

        response.getWriter().println("一个非常简单的portlet。");

}
}

使用命令编译类，

javac -cp $CATALINA_HOME/shared/lib/portlet-api-1.0.jar Simplest.java

### 6.3.2. **2.portlet.xml**

在最简单的/WEB-INF 目录中创建文件 portlet.xml。

<?xml 版本="1.0" 编码="UTF-8"?>

<portlet-app id="simplest" version="1.0">

<portlet id="最简单">

<portlet-name>最简单</portlet-name>

<display-name>简单的显示名称</display-name>

<portlet-class>最简单</portlet-class>

<支持>

  <mime-type>文本/html</mime-type>

  <portlet-mode>查看</portlet-mode>

</支持>

<supported-locale>en</supported-locale>

<portlet 信息>

  <title>简单标题</title>

  <short-title>世界上最简单的portlet</short-title>

</portlet-info>
</portlet>

</portlet-app>

### 6.3.3. **3. web.xml**

在最简单的 WEB-INF 目录中创建文件 web.xml。

<?xml 版本="1.0" 编码="UTF-8"?>

<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"

                         "http://java.sun.com/dtd/web-app_2_3.dtd">

<网络应用>

<display-name>最简单</display-name>

<description>世界上最简单的portlet</description>

</web-app>

### 6.3.4. **4.WAR文件**

从最简单的目录中，使用命令将上面的文件组合成一个war文件，

jar cvf ../simplest.war 。

### 6.3.5. **5.部署WAR文件**

将战争文件复制到**\$CATALINA\_HOME/webapps/jetspeed/WEB-INF/deploy**. Jetspeed-2 将部署 webapp。

### 6.3.6. **6. PSML**

创建文件 simple.psml 并将其复制到您的 Jetspeed 门户的门户页面目录中 **\$CATALINA\_HOME/pages/**。

注意：如果您**psml.pages.path**在[Jetspeed Properties](https://portals.apache.org/jetspeed-2/deployguide/jetspeed-properties.html)中通过属性设置了不同的门户页面目录路径，请使用门户页面目录。

portlet-app id 和 portlet-name 组合在一起来标识 portlet 片段。或者，可以通过单击编辑页面图标来使用 portlet 选择器。您的用户必须具有编辑页面的权限。用户**admin**密码 **admin**有权编辑所有页面。用户**user** 密码**user**有权编辑 [[USER 004] PSML Page](http://localhost:8080/jetspeed/portal/anotherdir)。默认情况下，Jetspeed-2 允许新注册的用户添加 portlet 并自定义他们的主页。

<?xml 版本="1.0" 编码="UTF-8"?>

<页面>

<默认值

 皮肤=“橙色”

 布局装饰器="底格里斯"

 portlet-decorator="tigris"
/>

<title>世界上最简单的portlet</title>

<metadata name="title" xml:lang="fr">La plus simple portlet du monde</metadata>

<fragment id="simplest" type="layout" name="jetspeed-layouts::VelocityTwoColumns">

<fragment id="simplest-1" type="portlet" name="simplest::Simplest">

  <property layout="TwoColumns" name="row" value="0" />

  <property layout="TwoColumns" name="column" value="0" />

</片段>
</片段>

<安全约束>

<security-constraints-ref>公共视图</security-constraints-ref>
</安全约束>

</页面>

在浏览器中 使用[最简单](http://localhost:8080/jetspeed/portal/simplest.psml) 的.psml 测试portlet 。

## 6.4. [**JSF**](https://portals.apache.org/jetspeed-2/devguide/guide-simple-jsf-portlet.html)

本指南提供了一个教程，用于在 portlet 视图模式下使用一个模板创建一个非常简单的 JSF portlet。

### 6.4.1. **1. Portlet 类**

在名为 jsf-simplest/WEB-INF/classes 的目录中创建文件 JSFSimplest.java：

公共类 JSFSimplest 扩展了 org.apache.portals.bridges.jsf.FacesPortlet

{

public void doView（javax.portlet.RenderRequest 请求，javax.portlet.RenderResponse 响应）

            抛出 javax.portlet.PortletException、java.io.IOException

{

    super.doView（请求，响应）；

}
}

使用命令编译jsf-simplest/WEB-INF/classes目录下的类，

javac -cp portlet-api-1.0.jar:portals-bridges-jsf-1.0.jar:portals-bridges-common-1.0.jar JSFSimplest.java

### 6.4.2. **2.portlet.xml**

在 jsf-simplest/WEB-INF 目录中创建文件 portlet.xml。

<?xml 版本="1.0" 编码="UTF-8"?>

<portlet-app id="jsfsimplest" 版本="1.0">

<portlet id="JSFSimplest">

<portlet-name>JSFSimplestPortlet</portlet-name>

<display-name>JSF 最简单的显示名称</display-name>

<portlet-class>JSFSimplest</portlet-class>

<初始化参数>

    <name>查看页面</name>

    <value>/WEB-INF/view/view.jsp</value>

</init-param>

<支持>

  <mime-type>文本/html</mime-type>

  <portlet-mode>查看</portlet-mode>

</支持>

<supported-locale>en</supported-locale>

<supported-locale>fr</supported-locale>

<portlet 信息>

  <title>JSF 最简单的标题</title>

  <short-title>JSF 最简单的短标题</short-title>

</portlet-info>
</portlet>

</portlet-app>

### 6.4.3. **3. web.xml**

在 jsf-simplest/WEB-INF 目录中创建文件 web.xml。

<?xml 版本="1.0" 编码="UTF-8"?>

<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"

                         "http://java.sun.com/dtd/web-app_2_3.dtd">

<网络应用>

<display-name>JSF 最简单</display-name>

<description>世界上最简单的 JSF portlet</description>

<!-- 人脸配置 -->

<上下文参数>

<param-name>javax.faces.application.CONFIG_FILES</param-name>

<param-value>/WEB-INF/faces-config.xml</param-value>
</context-param>

<!-- Faces Servlet -->

<小服务程序>

<servlet-name>Faces Servlet</servlet-name>

<servlet-class>javax.faces.webapp.FacesServlet</servlet-class>
</servlet>

<!-- 人脸扩展映射 -->

<servlet 映射>

<servlet-name>Faces Servlet</servlet-name>

<url-pattern>*.jsf</url-pattern>
</servlet-mapping>

</web-app>

### 6.4.4. **4. 观点**

在 jsf-simplest/WEB-INF/view 目录中创建 view.jsp 文件。

<%@ taglib uri="http://java.sun.com/jsf/core" 前缀="f" %>

<%@ taglib uri="/WEB-INF/tld/portlet.tld" 前缀='portlet'%>

[portlet:defineObjects/](portlet:defineObjects/)

<f:视图>

<h2>一个 JSF Portlet</h2>

你好

<% if (renderRequest.getUserPrincipal() == null) { %>

客人

<% } 其他 { %>

<%=renderRequest.getUserPrincipal().getName()%>

<% } %>！

</f:view>

### 6.4.5. **5.faces-config.xml**

在 jsf-simplest/WEB-INF 目录中创建 faces-config.xml 文件。

<?xml 版本='1.0' 编码='UTF-8'?>

<!DOCTYPE faces-config PUBLIC

  "-//Sun Microsystems, Inc.//DTD JavaServer Faces Config 1.1//EN"

  "http://java.sun.com/dtd/web-facesconfig_1_1.dtd">

<面孔配置>

<应用>

<语言环境配置>

  <default-locale>en</default-locale>

  <supported-locale>fr</supported-locale>

</locale-config>
</应用>

</faces-config>

### 6.4.6. **6. 依赖 JAR**

将依赖项复制到 WEB-INF/lib 目录。这些 jars 应该在您的 Maven 存储库中。如果是这样，在 lib 目录中执行这些命令将为您设置依赖项。

ln -s ~/.maven/repository/commons-beanutils/jars/commons-beanutils-1.7.0.jar

ln -s ~/.maven/repository/commons-collections/jars/commons-collections-3.1.jar

ln -s ~/.maven/repository/commons-digester/jars/commons-digester-1.7.jar

ln -s ~/.maven/repository/myfaces/jars/myfaces-api-1.1.0.jar

ln -s ~/.maven/repository/myfaces/jars/myfaces-impl-1.1.0.jar

ln -s ~/.maven/repository/myfaces/jars/tomahawk-1.1.0.jar

ln -s ~/.maven/repository/org.apache.portals.bridges/jars/portals-bridges-jsf-1.0.jar

ln -s ~/.maven/repository/xerces/jars/xerces-2.4.0.jar

ln -s ~/.maven/repository/xml-apis/jars/xml-apis-2.0.2.jar

### 6.4.7. **7.WAR文件**

从目录 jsf-simplest 使用命令将上面的文件组合成一个war文件，

jar cvf ../jsfsimplest.war 。

### 6.4.8. **8.部署WAR文件**

将战争文件复制到**\$CATALINA\_HOME/webapps/jetspeed/WEB-INF/deploy**. Jetspeed-2 将部署 webapp。

### 6.4.9. **9. PSML**

使用 Jetspeed portlet 选择器创建 PSML 页面。登录并单击编辑页面图标。单击添加 portlet 图标。复选框并将 JSFSimplestPortlet 添加到您的页面。您的用户必须具有编辑页面的权限。用户**admin** 密码 **admin**有权编辑所有页面。

## 6.5. [**Velocity **](https://portals.apache.org/jetspeed-2/devguide/guide-simple-velocity-portlet.html)

本指南提供了一个教程，用于在 portlet 视图模式下使用一个模板创建一个非常简单的 Velocity portlet。

### 6.5.1. **1. Portlet 类**

在名为 velocity-simplest/WEB-INF/classes 的目录中创建文件 VelocitySimplest.java：

公共类 VelocitySimplest 扩展 org.apache.portals.bridges.velocity.GenericVelocityPortlet

{

public void doView（javax.portlet.RenderRequest 请求，javax.portlet.RenderResponse 响应）

            抛出 javax.portlet.PortletException、java.io.IOException

{

    super.doView（请求，响应）；

}
}

使用命令编译velocity-simplest/WEB-INF/classes目录下的类，

javac -cp portlet-api-1.0.jar:portals-bridges-velocity-1.0.jar:portals-bridges-common-1.0.jar VelocitySimplest.java

### 6.5.2. **2.portlet.xml**

在velocity-simplest/WEB-INF 目录中创建文件portlet.xml。

<?xml 版本="1.0" 编码="UTF-8"?>

<portlet-app id="velocitysimplest" version="1.0">

<portlet id="VelocitySimplest">

<portlet-name>VelocitySimplest</portlet-name>

<display-name>Velocity 最简单的显示名称</display-name>

<portlet-class>VelocitySimplest</portlet-class>

<初始化参数>

    <name>查看页面</name>

    <value>/WEB-INF/view/world.vm</value>

</init-param>

<支持>

  <mime-type>文本/html</mime-type>

  <portlet-mode>查看</portlet-mode>

</支持>

<supported-locale>en</supported-locale>

<portlet 信息>

  <title>速度最简单的标题</title>

  <short-title>速度最简单的短标题</short-title>

</portlet-info>
</portlet>

</portlet-app>

### 6.5.3. **3. web.xml**

在velocity-simplest/WEB-INF 目录中创建文件web.xml。

<?xml 版本="1.0" 编码="UTF-8"?>

<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"

                         "http://java.sun.com/dtd/web-app_2_3.dtd">

<网络应用>

<display-name>速度最简单</display-name>

<description>世界上最简单的 Velocity portlet</description>

<!-- 定义 Velocity Servlet -->

<小服务程序>

<servlet-name>速度</servlet-name>

<servlet-class>org.apache.portals.bridges.velocity.BridgesVelocityViewServlet</servlet-class>
</servlet>

<!-- 将 *.vm 文件映射到 Velocity -->

<servlet 映射>

<servlet-name>速度</servlet-name>

<url-pattern>*.vm</url-pattern>
</servlet-mapping>

</web-app>

### 6.5.4. **4. 观点**

在velocity-simplest/WEB-INF/view 目录中创建world.vm 文件。将您想要的任何内容放入其中。请注意，模板文件是在 portlet 初始化参数中定义的** **ViewPage。对象[PortletConfig](http://portals.apache.org/pluto/portlet-2.0-apidocs/javax/portlet/PortletConfig.html)、[RenderRequest](http://portals.apache.org/pluto/portlet-2.0-apidocs/javax/portlet/RenderRequest.html)和[RenderResponse](http://portals.apache.org/pluto/portlet-2.0-apidocs/javax/portlet/RenderResponse.html) 会自动放置在 Velocity 上下文中，以便在 Velocity 模板中使用。这是一个示例模板，显示了其中一些对象的方法和属性。

$portletConfig.portletName

$portletConfig.portletContext.serverInfo

#set ($MESSAGES = $portletConfig.getResourceBundle($renderRequest.Locale))

$renderRequest.portletMode

$renderResponse.namespace

### 6.5.5. **5. 依赖 JAR**

复制 commons-beanutils-1.7.0.jar、commons-collections-3.1.jar、commons-digester-1.7.jar、portals-bridges-velocity-1.0.jar、velocity-1.4.jar 和 velocity-tools-1.1 .jar 到velocity-simplest/WEB-INF/lib 目录。重要提示：请勿将 portlet-api-1.0.jar 放入 war 文件中。如果您已经构建了 Jetspeed，这些 jar 文件应该在您的 Maven 存储库中。如果是这样，在 lib 目录中执行这些命令将为您设置依赖项。

ln -s ~/.maven/repository/commons-beanutils/jars/commons-beanutils-1.7.0.jar

ln -s ~/.maven/repository/commons-collections/jars/commons-collections-3.1.jar

ln -s ~/.maven/repository/commons-digester/jars/commons-digester-1.7.jar

ln -s ~/.maven/repository/org.apache.portals.bridges/jars/portals-bridges-velocity-1.0.jar

ln -s ~/.maven/repository/velocity/jars/velocity-1.4.jar

ln -s ~/.maven/repository/velocity-tools/jars/velocity-tools-1.1.jar

### 6.5.6. **6.WAR文件**

从目录velocity-simplest 使用命令将上面的文件组合成一个war 文件，

jar cvf ../velocitysimplest.war 。

### 6.5.7. **7.部署WAR文件**

将战争文件复制到**\$CATALINA\_HOME/webapps/jetspeed/WEB-INF/deploy**. Jetspeed-2 将部署 webapp。

### 6.5.8. **8. PSML**

使用 Jetspeed portlet 选择器创建 PSML 页面。登录并单击编辑页面图标。您的用户必须具有编辑页面的权限。用户**admin** 密码 **admin**有权编辑所有页面。

## 6.6.

# 7. **门户设计**

## 7.1. [**门户设计简介**](https://portals.apache.org/jetspeed-2/devguide/guide-portal-design.html)

Java Portlet API (JSR-168) 定义了用于编程 Portlet 的 Java 标准接口。Java Portlet API 规范支持 Portlet 和 Portal 之间的互操作性。它是开发 Java portlet 的标准规范。然而，Java Portlet API 没有定义用于在页面上布局和聚合 portlet 和标记的标准。“门户设计”下的文档包括：

· [页面聚合** - **参见 PSML 部分](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)

· [页面和** Portlet **装饰器](https://portals.apache.org/jetspeed-2/devguide/guide-decorators.html)

· [页面布局](https://portals.apache.org/jetspeed-2/devguide/guide-layouts.html)

· [Jetspeed 电动工具](https://portals.apache.org/jetspeed-2/devguide/guide-jpt.html)

· [模板定位器](#Template Locators)

· [术语](#Terminology)

### 7.1.1. **模板**

将一个或多个 portlet 呈现到 portlet 页面主要由将 portlet 聚合为具有模板的动态内容的过程组成。Jetspeed-2 在创建页面布局时使用 Velocity 模板。尽管 Jetspeed-2 体系结构完全支持将 JSP 模板用于装饰器和布局，但开发人员迄今已选择 Velocity 作为编写模板的首选工具。Jetspeed 中有两种类型的模板：布局和装饰器。呈现页面的过程是布局模板、页面装饰器模板、PSML 定义和一个或多个 portlet 装饰器模板的组合聚合。

#### 7.1.1.1. **布局模板**

布局模板打包在特殊的 Jetspeed 特定和可部署的 portlet 应用程序中。布局模板控制门户页面的整体聚合。布局模板与 portlet 相结合，为聚合提供了组件模型。Jetspeed-2 开箱即用，带有多个布局组件，包括一列、二列和三列布局。有关默认 Jetspeed-2 系统中所有可用布局的信息，请参阅[布局文档](https://portals.apache.org/jetspeed-2/devguide/guide-layouts.html)。当然，您可以定义和派生自己的布局。

#### 7.1.1.2. **装饰器**

装饰器模板打包在特殊的 Jetspeed 特定且可部署的档案中。布局模板控制门户页面的整体聚合。布局模板与 portlet 相结合，为聚合提供了组件模型。Jetspeed-2 开箱即用，带有多个布局组件，包括一列、二列和三列布局。有关默认 Jetspeed-2 系统中所有可用布局的信息，请参阅[装饰器文档](https://portals.apache.org/jetspeed-2/devguide/guide-decorators.html)。当然，您可以定义和派生自己的布局。

### 7.1.2. **模板定位器**

模板由 Jetspeed 模板（和装饰器）定位器组件定位。这些组件使用规范化的名称/值对 URL 方案定位模板。在装饰器或布局的所谓“规范化”URL 中使用此方案。但是，诸如 Velocity 之类的模板引擎需要使用与文档根目录相关的模板路径来处理模板。[Jetspeed 电动工具](https://portals.apache.org/jetspeed-2/devguide/guide-jpt.html)有助于规范化路径和相对路径之间的转换。通常在 Spring 配置中，所有装饰器的模板根定义为：

${applicationRoot}/WEB-INF/decorations

并且所有布局（每个 portlet 应用程序）的根定义为：

${applicationRoot}/WEB-INF/模板

规范化路径是用命名的对值定义的。例子：

类型/布局/媒体类型/html/name/tigris/decorator.vm

type/decorator/media-type/html/language/en/country/US/name/metal/decorator.vm


| **姓名** | **价值**                             | **描述**                                                                                                                                          |
| -------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 类型     | 布局                                 | 小门户                                                                                                                                            |
| 媒体类型 | html                                 | wml                                                                                                                                               |
| 姓名     | 有效的装饰器或布局名称               | 装饰器或布局的名称。通常对应于包含装饰器或布局模板、图像和样式表的子目录。                                                                        |
| 语言     | 有效的ISO-639标准两字符语言缩写      | ISO-639 (http://www.ics.uci.edu/pub/ietf/http/related/iso639.txt)定义了语言缩写的标准。典型的缩写是 en 表示英语，fr 表示法语，de 表示德语，...... |
| 国家     | 有效的ISO-3166标准两字符国家代码缩写 | ISO-3166 (http://userpage.chemie.fu-berlin.de/diverse/doc/ISO\_3166.html)定义了国家代码缩写的标准。典型的缩写是 US 代表美国，FR 代表法国，...     |

### 7.1.3. **术语**


| **学期**               | **定义**                                                                                                                                                     |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 布局                   | 定义片段分组相对于对门户的请求的最终聚合内容的组织方式。布局由Portlet定义，该 Portlet 将算法应用于模板以生成页面的聚合内容。典型的算法是两列、三列、嵌套的。 |
| 待办事项：在这里离开： | 片段、装饰、页面、页面装饰器、portlet装饰器、应用程序相关、规范化模板路径、绝对 URL                                                                          |

## 7.2. [**布局**](https://portals.apache.org/jetspeed-2/devguide/guide-layouts.html)

布局模板打包在特殊的 Jetspeed 特定和可部署的 portlet 应用程序中。布局模板控制门户页面的整体聚合。布局模板与 portlet 相结合，为聚合提供了组件模型。Jetspeed-2 开箱即用，带有多个布局组件，包括一列、二列和三列布局。有关默认 Jetspeed-2 系统中的所有可用布局，请参阅下面的[Jetspeed-2 布局。](#Jetspeed-2 Layouts)当然，您可以定义和派生自己的布局。

关于聚合，布局定义了单个门户页面的聚合方式。布局定义了相对于对门户的请求的最终聚合内容来组织片段分组的方式。布局由 Portlet 定义，该 Portlet 将算法应用于模板以生成页面的聚合内容。典型的算法是两列、三列、嵌套的。

布局由以下部分组成：

· 一个或多个模板

· 模板描述符

· 图片

· 样式表 (CSS)

· 宏

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml9180\wps67.jpg)

### 7.2.1. **布局包装**

布局被打包为标准的 portlet 应用程序。布局通常有一个

支持的操作：

· 部署

· 取消部署

· 重新部署

### 7.2.2. **Jetspeed-2 布局**

Jetspeed-2 开箱即用，带有多个布局组件，包括一列、二列和三列布局。当然，您可以定义和派生自己的布局。下表列出了 Jetspeed 中可用的布局组件。自定义（编辑）页面时，会选择布局组件。可以为每个 PSML 页面分配一种布局。


| **布局**                                                                                           | **类型** | **列** | **尺寸**    | **模式**         | **描述**                                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------- | -------- | ------ | ----------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **VelocityOneColumn**                                                                              | 单列     | 1      | 100%        | 查看、编辑、帮助 | 一个或多个片段的单列显示占据了portlet显示区域的 100%。                                                                                                                                                            |
| **VelocityTwoColumns**                                                                             | 双列     | 2      | 50%,50%     | 查看、编辑、帮助 | 一个或多个片段的两列显示，其中每一列分别分配到Portlet显示区域的 50%。[可以使用PSML](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)片段定义 将片段放置在任一列中。                                |
| **速度两列小左**                                                                                   | 双列     | 2      | 15%,85%     | 查看、编辑、帮助 | 一个或多个片段的两列显示，其中左列分配到15%的 portlet 显示区域，右列分配到 85% 的 portlet 显示区域。[可以使用PSML](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)片段定义 将片段放置在任一列中。 |
| **速度三列**                                                                                       | 三栏     | 3      | 33%,33%,33% | 查看、编辑、帮助 | 一个或多个片段的三列显示，其中每列分别分配到portlet显示区域的 33%。[可以使用PSML](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)片段定义 将片段放置在任一列中。                                  |
| **VelocityOneColumnNoActions、****VelocityTwoColumnsNoActions、****VelocityThreeColumnsNoActions** |          |        |             | 看法             | 与具有动作的对应参数相同，但不显示装饰器动作。                                                                                                                                                                    |

## 7.3. [**装饰器**](https://portals.apache.org/jetspeed-2/devguide/guide-decorators.html)

装饰器被定义为围绕动态生成的片段的任何静态或半静态标记。装饰器通常使用 Velocity 或 JSP 模板编写。本指南将主要关注使用 Velocity 脚本语言来构建装饰。但是，这里描述的大多数标准和方法都可以应用于用其他脚本语言编写 decroations。

构建页面时使用了两种不同类型的装饰；Portlet 和布局（或页面）。

Portlet 装饰是 Jetspeed 的“橱窗装饰”。它们用 HTML（XHTML、VXML 等）包装每个单独的 portlet 片段的呈现内容。Portlet 装饰负责显示适当的标题以及与更改窗口状态或 Portlet 模式相关的任何按钮。

布局或页面装饰负责为由 .psml 文档表示的单个门户页面提供“页眉”区域和“页脚”区域（有关 psml 的更多信息，请参阅：[使用** PSML **的设计人员的文档](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html) ）。它们还提供页面和 portlet 的一般样式信息。但是，可以在 portlet 装饰级别覆盖 portlet 级别的样式设置。

### 7.3.1. **装修文件结构**

所有装饰都直接存储在 Web 应用程序根目录下的一个名为**decorations**. 这里的两个主要目录**layout**用于布局装饰和**portlet** portlet 装饰。各个 decoartions 位于这两个目录下的它们自己的目录中。您在其中创建的目录的名称 **layout**或**portlet**Jetspeed 将如何定位您的装饰。我们将在本指南的后面部分详细介绍其工作原理。

### 7.3.2. **布局（页面）装饰剖析**

#### 7.3.2.1. **四个文件一目了然**

在它的最基本形式中，布局声明只需要您定义四个文件：

· 装饰器.properties

· 样式.css

· 标头.vm

· 页脚.vm

其中三个文件；decorator.properties、header.vm 和 footer.vm 直接进入您在**/decorations/layout**. 样式.css 需要放入您的装饰名称的子目录中**css/**。

#### 7.3.2.2. **基本布局装饰配置：decorator.properties**

decorator.properties 文件包含有关布局装饰的基本信息。实际上，这个文件可以是空白的，但我们仍然要求它存在，因为它被其他 API 用来“发现”可用的装饰。话虽如此，可以安全地假设下面定义的所有属性都是可选的。


| **属性名称**   | **描述**                                                                                     | **默认**           |
| -------------- | -------------------------------------------------------------------------------------------- | ------------------ |
| base.css.class | 此值通常放置在标题模板的最顶部元素标记中。当我们开始开发标题模板时，您将看到它是如何使用的。 | 默认为您的装饰名称 |
| 样式表         | 装饰样式表的相对路径                                                                         | css/styles.css     |
| 标题           | 装饰标题模板的相对路径                                                                       | 标头.vm            |
| 页脚           | 装饰页脚模板的相对路径                                                                       | 页脚.vm            |

#### 7.3.2.3. **给你的页面顶部：header.vm**

header.vm**代表**门户页面的顶部。以下是编写功能性标题模板所需的基础知识的逐节演练。

**注意：**假定读者精通 HTML 和 CSS 的使用。Velocity 的基本知识有助于开发装饰，但不是必需的。

<html>

<头部>

 #defineLayoutObjects()
前两行应该很明显，如果不是，那么从这里开始的本指南对您没有太大帮助；-)

##### 7.3.2.3.1. **我们的第一个宏：#defineLayoutObjects()**

现在包含的行的**#defineLayoutObjects()**目的将不像前两个那样明显。 **#defineLayoutObjects()**是众所周知的，在 Velocity 白话中，作为一个宏。宏是预定义的 Velocity 代码片段，可以在任何 Velocity 模板中重复使用。我们将使用的所有全局宏（包括这个）都在**WEB-INF/jetspeed\_macros.vm**. 在本指南的后面部分，我们将讨论提供您自己的自定义宏来帮助您进行装饰开发（如果您愿意的话）。现在，回到**#defineLayoutObjects()**. **#defineLayoutObjects()**向 Velocity 添加可在 header.vm、footer.vm、其他宏和所有 portlet 装饰模板中访问的值。我们可以很容易地在这里停下来**#defineLayoutObjects()**，但是，我觉得对初学者了解 Velocity 的内部工作原理会有所帮助。废话不多说，代码：

#macro（定义布局对象）

#set($preferedLocale = $JS2RequestContext.locale)

#set($rootFragment = $jetspeed.currentFragment)

#set($site = $request.getAttribute("org.apache.jetspeed.portalsite.PortalSiteRequestContext"))

#set($theme = $request.getAttribute("org.apache.jetspeed.theme"))

#set($layoutDecoration = $theme.getDecoration($rootFragment))
＃结尾

唔。这里实际发生了什么。好的，首先我们有，**#set()**这就是 Velocity 中所谓的指令。指令是内置功能而不是宏。**#set()** 非常简单，因为它采用 = 右侧的值并将其分配给左侧。酷，这似乎相当直截了当。但是如何使用这些值以及到底是**\$JS2RequestContext.locale**从哪里来的呢？我想我应该退后一步，描述一下我们如何在 Velocity 中处理对象。Velocity 模板可用的所有对象都可以通过该**\$someObject**符号引用。知道这么多调用方法，让我们 getFoo()，可以像这样完成**\$someObject.getFoo()**. 更酷的是我们可以简写不带任何参数的 getter 方法， **\$someObject.foo**. 至于这个，**\$JS2RequestContext**这实际上是**org.apache.jetspeed.RequestContext**Jetspeed 本身提供给 Velocity 的一个实例。**org.apache.jetspeed.RequestContext**因此，通过查看我们看到 的 javadoc 将为我们提供一个代表当前用户语言环境的**\$JS2RequestContext.locale**实例。**java.util.Locale**不能比这更简单吗？

接下来我们有这行**#set(\$rootFragment = \$jetspeed.currentFragment)**另一个 set() 语句，这次创建一个名为的对象**\$rootFragment**，它是 [org.apache.jetspeed.om.page.ContentFragment的一个实例](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/om/page/ContentFragment.html). 描述正在做什么实际上与本指南无关，**\$jetspeed.currentFragment**因此我将跳过该内容并继续前进。 啊，现在看起来很熟悉，这实际上是 我们从中检索由 Jetspeed 放入 Velocity 的对象的实例。实际对象分别是： [org.apache.jetspeed.portalsite.PortalSiteRequestContext](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/portalsite/PortalSiteRequestContext.html) 和 [org.apache.jetspeed.decoration.Theme](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/decoration/Theme.html) 。我们将在短时间内充分利用所有这些对象。

**#set(\$site = \$request.getAttribute("org.apache.jetspeed.portalsite.PortalSiteRequestContext"))**

**#set(\$theme = \$request.getAttribute("org.apache.jetspeed.theme"))**

**\$requestjavax.servlet.http.HttpServletRequest**

##### 7.3.2.3.2. **喂你的头：如何正确编码你的头标。**

本节为您提供正确编码 Layout decroation 的 <HEAD> 的所有信息。所以，直接上代码。

<html>

<头部>

 #defineLayoutObjects()

 

 <base href="#BaseHref()">

 <meta http-equiv="Content-type" content="#ContentType()" />

 <meta http-equiv="Content-style-type" content="text/css" />   

 #includeJavaScriptForHead()

 #IncludeStylesheets()    

 <title>#PageTitle()</title>

 <meta name="description" content="#PageDescription()" />
###### 7.3.2.3.2.1. **<base> 标签**

首先，我们有** <base href="#BaseHref()">**它允许我们定义 Web 资源解析的基本路径，深入讨论** <base>**请参阅：[W3C 学校参考](http://www.w3schools.com/tags/tag_base.asp)。如果您曾经使用过 Jetspeed，您会注意到它会进行各种疯狂的 URL 重写，这将完全阻止任何尝试始终如一地为您的 html 和样式表提供路径。通过定义 BASE 标签，这个问题几乎会消失。至于**#BaseHref()**宏，它只是为您的 Web 应用程序的根生成一个完全限定的路径。就 servlet api 而言，实际代码与此同义：

HttpServletRequest 请求；

StingBuffer baseHref = new StringBuffer(request.getScheme())

 .append("://").append(request.getServerName())

 .append(":").append(request.getServerPort())

 .append(request.getContextPath()).append("/");
返回 baseHref.toString();

实际的 Velocity 宏代码更简洁；）

${request.scheme}://${request.serverName}:${request.serverPort}${request.contextPath}/

###### 7.3.2.3.2.2. **元标记：<meta http-equiv="Content-type" content="#ContentType()" />**

将返回 text/html 加上正确的编码，例如 UTF。

###### 7.3.2.3.2.3. **#includeJavaScriptForHead()**

在编写本指南时，基本 Jetspeed 2 服务器运行所需的 JavaScript 真的很少。然而，随着我们尝试在配置和管理等方面使用 AJAX，这可能会在不久的将来发生变化。

### 7.3.3. **JSP 装饰器**

JSP 装饰器目前仅在*tigris*装饰器中受支持。默认情况下不启用 JSP 装饰器。JSP 装饰器可以通过修改（正确注释的）设置来启用：

· 装饰器/布局/tigris/decorator.properties

· 装饰器/portlet/tigris/decorator.properties

· WEB-INF/templates/layout/html/columns/layout.properties

· WEB-INF/templates/layout/html/maximized/layout.properties

· WEB-INF/templates/layout/html/solo/layout.properties

注意：您需要更改上述所有属性文件中的设置，然后重新启动jetspeed。

另请注意：对于 tcolumns 模板，（还）没有 JSP 替代品，但无论如何，AFAIK 并没有太多使用。请确定：不要将您的页面布局 portlet 从列切换到 tcolumns，否则您的页面将被破坏。

## 7.4. [**Jetspeed Power Tool**](https://portals.apache.org/jetspeed-2/devguide/guide-jpt.html)

Jetspeed Power Tool (JPT) 是一种用于布局和装饰器的速度工具，用于生成动态内容。JPT 是一个请求级别的速度工具，适用于所有布局和装饰器。JPT 在您的装饰器或布局中被引用为：

$jetspeed

所有公共 JPT API 都可以通过以下方式访问：

· 方法的 Java 点表示法

· 属性的 JavaBean 快捷方式（getter/setter）

调用方法的示例：

# 使用 2 个参数调用方法 'getTitle'

$jetspeed.getTitle($myPE, $myF)

调用获取属性的示例：

# 获取页面bean，相当于$jetspeed.getPage()

$jetspeed.page

### 7.4.1. **JPT 速度 API**

下表定义了 Velocity 的 Jetspeed 电动工具 API

---


| **API** | **装饰和包含（\$片段）**                                                                                                                                      |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 描述    | 为Velocity包含的给定片段参数**(\$fragment)** 检索到装饰器模板的应用程序相对路径。应该作为参数传递给 Velocity #parse 函数（#parse 包括另一个 Velocity 模板）。 |
| 范围    | **\$fragment**-要包含和装饰的片段。                                                                                                                           |
| 退货    | **String**-装饰器模板的应用程序相对路径。                                                                                                                     |
| 例子    | #parse(\$jetspeed.decorateAndInclude(\$fragment))返回/WEB-INF/decorations/layout/html/tigris/header.vm                                                        |

---


| **API** | **getAbsoluteUrl(appRelativePath)**                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 描述    | 给定一个portlet应用程序资源的相对路径，返回一个绝对 URL。此 API 不应用于引用模板 ULS，因为它们通常无法作为绝对 URL 访问，因为它们通常位于 CMS 中或受保护的 WEB-INF 目录后面。 |
| 范围    | **relativePath**-装饰器包中资源的相对路径。                                                                                                                                   |
| 退货    | **字符串**- Web资源的完整绝对路径                                                                                                                                             |
| 例子    | \$jetspeed.getAbsoluteUrl("/images/test.gif")返回http://localhost:8080/jetspeed/portal/images/test.gif                                                                        |

---


| **API** | **列**                                                         |
| ------- | -------------------------------------------------------------- |
| 描述    | 在布局聚合期间返回当前片段的列列表。                           |
| 范围    | **-**                                                          |
| 退货    | **List**-子片段或 portlet 的标准 Java 列表                     |
| 例子    | #set (\$table = \$jetspeed.columns)#foreach(\$table中的$entry) |

---


| **API** |  |
| ------- | - |
| 描述    |  |
| 范围    |  |
| 退货    |  |
| 例子    |  |

---
