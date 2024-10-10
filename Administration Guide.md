[Administration Guide](https://portals.apache.org/jetspeed-2/adminguide/index.html)

您可以使用一组管理 portlet 来管理 Jetspeed。

# 1. **安全管理**

## 1.1. [**用户管理**](https://portals.apache.org/jetspeed-2/adminguide/users.html)

用户管理是您管理单个门户用户的地方。您可以创建新用户，以及编辑或删除现有用户。您可以设置用户的密码，并管理用户的属性、角色、组成员资格和分析规则。用户管理页面位于 Jetspeed 管理 Portlets 部分内。用户管理页面是顶部管理菜单上的第一个选项卡。在这里您可以看到用户浏览器。

### 1.1.1. **用户浏览器**

用户浏览器 portlet 列出所有门户用户，并允许您搜索特定用户。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps90.jpg)

#### 1.1.1.1. **寻呼**

如果系统中有超过 10 个用户，则用户列表将分布在多个页面上，每个页面显示 10 个用户。您可以使用列表正下方的按钮浏览页面。单击“刷新”按钮会将用户列表重置为第一页。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps91.jpg)

#### 1.1.1.2. **搜索**

您可以通过在搜索文本框中输入用户名或用户名的一部分来搜索特定用户。单击“搜索”按钮后，用户列表将显示搜索结果，从与您的搜索查询最匹配的用户开始，然后是通常按字母顺序出现在匹配用户之后的用户。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps92.jpg)

#### 1.1.1.3. **过滤**

要在搜索（或部分）特定用户名时仅获得完全匹配，请选中搜索文本框下方的“过滤器”复选框。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps93.jpg)

#### 1.1.1.4. **选择编辑**

要选择列表中的用户之一进行编辑，请单击用户名。用户名前面会出现一个小箭头，表示它当前已被选中，并且用户的详细信息将加载到用户详细信息信息 portlet 中。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps94.jpg)

### 1.1.2. **用户详细信息**

用户详细信息 Portlet 允许您管理特定用户的属性、凭证、角色、组成员资格和配置文件。这些中的每一个都表示在 portlet 的不同选项卡上。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps95.jpg)

#### 1.1.2.1. **用户属性**

用户属性是您可能希望在门户中存储的有关用户的任何类型的信息。例如名字和姓氏、地址、电话号码或与组织相关的属性，例如员工或学生编号。每个属性都是一个简单的名称-值对。您可以创建任意数量的属性。

用户的用户属性在“属性”选项卡中进行管理。所选用户的现有属性显示在列表中。属性的值可以直接在“值”列的文本框中进行编辑。要存储您的更改，请选中您更改的每个属性前面的复选框，然后单击“更新”按钮。要删除属性，请选中要删除的每个属性前面的复选框，然后单击“删除”按钮。

要创建新属性，请在属性列表正下方的表单中输入名称和值。您可以为名称和值输入任何内容。单击“添加”按钮以存储新属性。请注意，如果您使用现有属性的名称，其值将被覆盖。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps96.jpg)

#### 1.1.2.2. **密码凭证**

有关管理用户凭据的详细信息，请参阅[凭据](https://portals.apache.org/jetspeed-2/adminguide/credentials.html)。

#### 1.1.2.3. **角色**

在“角色”选项卡上，您可以管理为当前选定用户分配的角色。角色本身可以在[角色管理](https://portals.apache.org/jetspeed-2/adminguide/roles.html)页面上进行管理。列出了所选用户当前已分配的角色。您可以通过从下拉列表中选择一个角色并单击“添加”按钮来为用户分配一个新角色。新角色将立即出现在列表中。要删除角色，请选中列表中角色的复选框，然后单击“删除”按钮。该角色将从列表中消失。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps97.jpg)

#### 1.1.2.4. **团体**

在“组”选项卡上，您可以管理当前选定用户的组成员身份。组本身可以在[组管理](https://portals.apache.org/jetspeed-2/adminguide/groups.html)页面上进行管理。列出了所选用户当前所属的组。您可以通过从下拉列表中选择组，然后单击“添加”按钮将用户添加到组。该组将立即出现在列表中。要从组中删除用户，请选中列表中组的复选框，然后单击“删除”按钮。该组将从列表中消失。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps98.jpg)

#### 1.1.2.5. **轮廓**

每个用户主体都可以映射到特定的分析规则。此关联存储在 Jetspeed 数据库中。关联是三向的，结合了 PRINCIPAL + PROFILING RULE + LOCATOR，其中目前支持的 locator 值为菜单或者页. 因此，我们可以应用两种不同的分析规则来为每个用户定位资源：定位页面和定位菜单。当分析器尝试为当前用户定位页面时，它将为给定用户应用分析规则。Jetspeed 用户管理 portlet 有一个用于编辑用户配置文件信息的选项卡：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps99.jpg)

通常，在用户注册（或自注册）期间，分析规则由特定于门户的逻辑确定并关联。Jetspeed 特定的自注册 Portlet 可以处理向系统添加用户、授予角色、设置用户属性和为用户分配概要分析规则的注册过程。

#### 1.1.2.6. **删除用户**

要从系统中删除用户，请单击“删除用户”按钮。此操作是永久性的。将显示一条消息，指示该节点已被删除，并且您刚刚删除的用户不存在。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps100.jpg)

#### 1.1.2.7. **用户详细信息配置**

在编辑模式下配置用户详细信息 portlet 允许您自定义用户详细信息管理窗口的视图。每个选项卡都可以选择显示或隐藏。此外，可以设置角色、新用户、所需角色、配置文件、用户模板、子站点根文件夹和默认子站点新用户的默认值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps101.jpg)


| **场地**                                     | **描述**                                                                                                                                         |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| 显示用户选项卡                               | 显示或隐藏用户选项卡。                                                                                                                           |
| 显示属性选项卡                               | 显示或隐藏“属性”选项卡。                                                                                                                       |
| 显示密码选项卡                               | 显示或隐藏密码选项卡。                                                                                                                           |
| 显示密码过期                                 | 在“密码”选项卡上显示密码到期日期，以及激活/到期/延长密码的选项。                                                                               |
| 显示角色选项卡                               | 显示或隐藏角色选项卡。                                                                                                                           |
| 显示组选项卡                                 | 显示或隐藏“组”选项卡。                                                                                                                         |
| 显示配置文件选项卡                           | 显示或隐藏配置文件选项卡。                                                                                                                       |
| 在用户选项卡上显示密码                       | 显示或隐藏密码信息用户选项卡。如果启用，用户选项卡将有效地提供与密码选项卡相同的功能。                                                           |
| 为新用户定义默认的“首次登录时需要更改密码” | 在添加用户表单中显示或隐藏设置“首次登录时需要更改密码”的选项。                                                                                 |
| 为新用户定义默认角色                         | 在“添加用户”表单中显示或隐藏用于定义默认角色的选项。                                                                                           |
| 为新用户定义默认配置文件                     | 在“添加用户”表单中显示或隐藏用于定义默认配置文件的选项。                                                                                       |
| 允许为新用户分配子站点                       | 在“添加用户”表单中显示或隐藏用于定义默认子站点的选项。                                                                                         |
| 默认“首次登录时需要更改密码”               | 选中或取消选中“添加用户”表单中的“首次登录时需要更改密码”复选框（如果通过选中为新用户定义默认的“首次登录时需要更改密码”启用，请参见上文）。 |
| 新用户的默认角色                             | 在“添加用户”表单的“默认角色”下拉列表中预先选择一个角色。                                                                                     |
| 新用户所需的角色                             | 为新用户设置所需的角色，无论默认角色设置如何，该角色都会分配给每个新用户。                                                                       |
| 新用户的默认配置文件                         | 在添加用户表单的默认配置文件下拉列表中预先选择配置文件。                                                                                         |
| 新用户模板目录                               | 去做                                                                                                                                             |
| 子站点根文件夹                               | 去做                                                                                                                                             |
| 新用户的默认子站点                           | 去做                                                                                                                                             |

### 1.1.3. **添加新用户**

可以通过用户详细信息 portlet 输入新用户。如果您尚未从用户浏览器中选择任何用户，则用户详细信息 portlet 将显示“添加用户”表单。如果您确实选择了一个用户，请单击 portlet 底部的“添加新用户”按钮以转到“添加用户”表单。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps102.jpg)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps103.png)

从这里您可以创建一个新用户。选择一个没有空格的唯一用户名。然后输入安全密码。您可以要求在首次登录时更改密码。您还可以选择分配给该用户的默认角色以及默认分析规则。最后，您可以将此用户分配给子站点。

## 1.2. [**角色管理**](https://portals.apache.org/jetspeed-2/adminguide/roles.html)

角色管理是您管理各个门户角色的地方。您可以创建新角色并删除现有角色。您可以将用户分配给角色。角色管理页面位于 Jetspeed 管理 Portlets 部分中。角色管理页面是顶部管理菜单上的第二个选项卡。角色管理部分由两个 portlet、角色管理和角色详细信息组成。

### 1.2.1. **角色管理员**

Role Admin portlet 列出所有门户角色并允许您搜索特定角色。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps104.jpg)

#### 1.2.1.1. **搜索**

您可以通过在搜索文本框中输入角色名称或角色名称的一部分来搜索特定角色。单击“搜索”按钮后，角色列表将显示搜索结果，从与您的搜索查询最匹配的用户开始，然后是通常按字母顺序出现在匹配用户之后的用户。

#### 1.2.1.2. **过滤**

要在搜索（或部分）特定角色名称时仅获得完全匹配，请选中搜索文本框下方的“过滤器”复选框。

### 1.2.2. **添加和删除角色**

角色详细信息 portlet 允许您添加和/或删除角色。在角色管理 portlet 中选择一个角色，角色详细信息 portlet 将使用该角色的成员进行更新。角色管理 porlet 中选定的角色现在将有一个箭头标记它。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps105.jpg)

#### 1.2.2.1. **添加角色**

要添加角色，根据角色详细信息 portlet 状态，您需要...

· 选择“添加新角色”，输入角色名称并按“保存”（上图），或

· 输入角色名称并按“保存”（如下截图）。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps106.jpg)

#### 1.2.2.2. **删除角色**

要从系统中删除角色，请单击角色管理员 portlet 中的所需角色。角色名称前面将出现一个小箭头，表示它当前已被选中，并且角色的现有用户将加载到角色详细信息 Portlet 中。单击“删除角色”按钮。此操作是永久性的。

### 1.2.3. **将用户添加到角色**

要添加或删除分配给某个角色的用户，请单击 Role Admin portlet 中的角色名称。角色名称前面将出现一个小箭头，表示它当前已被选中，并且角色的现有用户将加载到角色详细信息 Portlet 中。

#### 1.2.3.1. **寻呼**

如果在系统中分配给一个角色的用户超过十个，则角色列表将分布在几个页面上，每个页面显示十个用户。您可以使用列表正下方的按钮浏览页面。单击“刷新”按钮会将用户列表重置为第一页。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps107.jpg)

#### 1.2.3.2. **将用户添加到角色**

角色详细信息 portlet 允许您将用户添加到角色。选择“将用户添加到角色”。将出现一个弹出窗口。选中您要添加的用户，然后单击“添加用户”。角色详细信息 portlet 将填充选定的用户。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps108.jpg)

#### 1.2.3.3. **删除选中的用户**

要从角色中删除用户，请选择要删除的用户，然后单击“删除选中的用户”按钮。请注意，此操作是永久性的！

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps109.jpg)

#### 1.2.3.4. **搜索角色中的用户**

您可以通过在搜索文本框中输入用户名或用户名的一部分来搜索特定用户。单击“搜索”按钮后，“角色中的用户”列表将显示搜索结果，从与您的搜索查询最匹配的用户开始，然后是通常按字母顺序出现在匹配用户之后的用户。

#### 1.2.3.5. **过滤角色中的用户**

要在搜索（或部分）特定用户名时仅获得完全匹配，请选中搜索文本框下方的“过滤器”复选框。单击“刷新”按钮会将组列表重置为第一页。

## 1.3. [**组****管理**](https://portals.apache.org/jetspeed-2/adminguide/groups.html)

使用 Jetspeed 管理组。

组管理是您管理为用户和角色创建和删除组的地方。此界面还可用于将用户添加到组以及从组成员中删除单个或多个用户。Group Management 页面位于 Jetspeed 管理 Portlets 部分内。组管理页面是顶部管理菜单上的第三个选项卡。在这里，您可以看到 Group Admin，它位于最初访问此区域时显示的两个 portlet 的左侧。

### 1.3.1. **组浏览器**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps110.jpg)

#### 1.3.1.1. **搜索**

您可以通过在搜索文本框中输入组名或组名的开头来搜索特定组。单击“搜索”按钮后，组列表将显示搜索结果，从与您的搜索查询最匹配的组开始。在匹配的搜索结果之后正常列出的组仍然会显示。

#### 1.3.1.2. **过滤**

要在搜索特定组名时仅获得完全匹配，请选中搜索文本框下方的“过滤器”复选框。单击“刷新”按钮会将组列表重置为第一页。

#### 1.3.1.3. **选择编辑**

通过单击组名称选择列表中的组之一进行编辑。组名前面会出现一个小箭头，表示它当前已被选中，组的详细信息将加载到 Group Detail Information portlet 中。

### 1.3.2. **添加新组**

您可以通过在组详细信息 Portlet 的组名称字段中输入名称并单击保存来添加组。左侧的 Group Admin portlet 将更新以按字母顺序包含新名称。您可以使用用户和角色选项卡将用户和角色添加到新组。

### 1.3.3. **删除组**

您可以通过在 Group Admin portlet 中选择要编辑的组来删除组。组详细信息 portlet 将更新以包括删除选项。作为该组成员的任何用户或角色都不会受到任何其他方式的影响。添加同名组不会自动恢复用户或角色成员资格。必须再次添加角色和用户才能使其属于该组。

### 1.3.4. **组详细信息**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps111.jpg)

以下部分基于如上所述选择进行编辑的组。两个选项卡式菜单，用户和角色，可用于在组内进行编辑。

#### 1.3.4.1. **将用户添加到组**

在“用户”选项卡处于活动状态时，单击下方的“将用户添加到组...”按钮。将出现一个新的弹出窗口，其中包含可用用户列表。选中您希望添加到组的任何用户的复选框，然后单击“添加用户”。通过单独单击复选框可以进行多项选择。窗口将自动刷新并列出新用户。

#### 1.3.4.2. **删除选中的用户**

可以选中列表中每个用户左侧的复选框以选择用户。通过单独单击复选框可以进行多项选择。单击“删除选中的用户”按钮以删除选定的用户。执行操作后，窗口将自行更新。

#### 1.3.4.3. **搜索组中的用户**

您可以通过在搜索文本框中输入用户名或用户名的开头来搜索组中的特定用户。单击“搜索”按钮后，组列表中的用户将显示搜索结果，从最匹配您的搜索查询的用户开始。在匹配的搜索结果之后正常列出的用户仍然会显示。

#### 1.3.4.4. **将角色添加到组**

选择要编辑的组并且角色选项卡处于活动状态，单击下方的“将角色添加到组...”按钮。将出现一个新的弹出窗口，其中包含可用角色的列表。选中您希望添加到组的任何角色的复选框，然后单击“添加角色”。通过单独单击复选框可以进行多项选择。窗口将自动刷新并列出新用户。

#### 1.3.4.5. **删除选中的角色**

可以选中列表中每个角色左侧的复选框以选择角色。通过单独单击复选框可以进行多项选择。单击“删除选中的角色”按钮以删除选定的角色。执行操作后，窗口将自行更新。

#### 1.3.4.6. **在组中搜索角色**

您可以通过在搜索文本框中输入角色名称或角色名称的开头部分来搜索组中的特定角色。单击“搜索”按钮后，“组中的角色”列表将显示搜索结果，从最匹配您的搜索查询的角色开始。在匹配的搜索结果之后正常列出的角色仍将显示。

## 1.4. [**约束**](https://portals.apache.org/jetspeed-2/adminguide/constraints.html)

### 1.4.1. **安全约束管理指南**

安全约束限制对门户中资源的访问。门户资源（文件夹、链接、页面、portlet）可以通过以下方式保护：

· 安全约束（基于 Jetspeed 特定的安全约束）

· 安全权限（基于 Java 安全策略）

默认安全性是约束，因为它们更容易由门户管理员配置。Permissions 的优点是它们存储在 Jetspeed 数据库的中央存储库中，并且它们遵守 Java 安全标准，约束和权限都继承。这意味着如果您对文件夹设置权限或约束，它会被所有子文件夹和页面继承

约束向安全主体授予权限，或者：

· 一名角色

· 一群

· 用户

· 或 \* 对于所有用户

约束定义了操作，可以是标准的 portlet 模式：

· 看法

· 编辑

· 帮助

或 Jetspeed 扩展 portlet 模式：

· 编辑默认值

· 关于

· 配置

· 打印

#### 1.4.1.1. **约束管理**

TODO：描述用户界面，屏幕截图

#### 1.4.1.2. **安全参考**

门户资源引用安全定义来保护该特定资源。可以保护以下资源：

· 文件夹：在文件夹元数据中

· 页面：在 PSML 文件中

· 链接：在 .link 文件中

· Portlet 窗口：页面上的一个 Portlet 实例

· Portlet 定义：所有页面上的 Portlet 的所有实例

· Portlet Application：一个portlet应用程序中的所有portlet

保护资源就像引用定义一样简单。您可以从门户的多个区域执行此操作：

· 1. 站点管理员保护文件夹、页面或链接

· 2. Portlet Application Manager，用于保护 Portlet 应用程序或 Portlet 定义

· 3. 配置模式，如果可用于 portlet，您可以保护 portlet 实例

此外，可以在部署描述符中保护 portlet。有关更多详细信息，请参阅[部署](https://portals.apache.org/jetspeed-2/deployguide/index.html)指南。

## 1.5. [**证书**](https://portals.apache.org/jetspeed-2/adminguide/credentials.html)

### 1.5.1. **凭证管理**

#### 1.5.1.1. **管理密码过期**

如果使用 ，则可以通过随 portlet 应用程序提供的**PasswordExpirationInterceptor**直接管理特定用户的密码过期。**UserDetailPortletsecurity**

如果启用，此 portlet 可以显示密码的当前到期日期并允许更改其值：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps112.jpg)

可以看到，通过radio组，可以将密码有效期更改为：


| **行动** | **过期**                                                        |
| -------- | --------------------------------------------------------------- |
| 已到期   | 今天                                                            |
| 延长     | 今天+**maxLifeSpanInDays**为PasswordExpirationInterceptor配置的 |
| 无限扩展 | 8099年 1 月 1 日（java.sql.Date 允许的最大值）                  |

可以通过以下的编辑/首选项页面启用此功能**UserDetailsPortlet**：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps113.jpg)

注意：当指定新密码值时，选择的密码过期动作**Expired** 将被忽略！

#### 1.5.1.2. **设置默认“首次登录时需要更改密码”**

通过与上面显示的相同的首选项，也可以配置新用户的密码凭证**UserDetailsPortlet**的默认 属性。**updateRequired**

而且，如果您总是需要对所有用户进行相同的设置，您甚至可以取消对话框上通常显示的选择框**Add User**。

使用如上例所示设置的首选项，**Add User**对话框将如下所示：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps114.jpg)

使用示例首选项集添加的用户将**updateRequired**属性设置为 true，**User**分配角色并使用**role-fallback**分析规则。

## 1.6. [**权限**](https://portals.apache.org/jetspeed-2/adminguide/permissions.html)

### 1.6.1. **安全权限管理指南**

安全权限限制对门户中资源的访问。门户资源（文件夹、链接、页面、portlet）可以通过以下方式保护：

· 安全约束（基于 Jetspeed 特定的安全约束）

· 安全权限（基于 Java 安全策略）

默认安全性是约束，因为它们更容易由门户管理员配置。权限的优点是它们存储在 Jetspeed 数据库的中央存储库中，并且它们遵守 Java 安全标准。约束和权限都继承。这意味着如果您对文件夹设置权限或约束，它会被所有子文件夹和页面继承。权限是存储在数据库中的 Java 安全策略的实现。

权限向安全主体授予权限，或者：

· 一名角色

· 一群

· 用户

· 或 \* 对于所有用户

权限定义操作，可以是标准的 portlet 模式：

· 看法

· 编辑

· 帮助

或 Jetspeed 扩展 portlet 模式：

· 编辑默认值

· 关于

· 配置

· 打印

#### 1.6.1.1. **权限管理**

权限管理位于 Jetspeed 管理门户页面左侧的第四个选项卡上。它包含一个portlet，Security Permissions，它允许您为角色设置三种不同资源类型的权限：portlet、文件夹和页面。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps115.jpg)

##### 1.6.1.1.1. **权限用户界面**

Permissions portlet 的 UI 分为以下几个部分：


| **用户界面部分** | **描述**                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 资源类型选项卡   | 通过单击相应的选项卡选择要为其定义权限的资源类型。资源类型有：· 小门户· 文件夹· 页面![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps116.jpg)                                                                                                                                                                                                                                                                                             |
| 权限列表         | 为所选资源类型定义的权限列表。每个权限都显示资源名称、允许的操作以及此权限适用的角色。![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps117.jpg)                                                                                                                                                                                                                                                                                              |
| 许可表格         | 此表单允许您编辑列表中选择的权限，或创建新权限。“角色”显示角色列表，您可以通过选中相应的复选框在其中选择此权限适用的角色。“操作”显示一个操作列表，您可以在其中通过选中相应的复选框来选择对所选资源允许所选角色执行的操作。可用的操作是：· 看法· 编辑· 帮助· 关于· 配置· 编辑默认值· 打印最后，在表单的右上角有四个按钮，用于创建新权限，或者保存、恢复或删除选定的权限。![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps118.jpg) |

##### 1.6.1.1.2. **编辑权限**

要编辑权限，请在权限列表中选择一项。权限设置将加载到表单中。通过选中相应的复选框来选择此权限应应用于的角色。通过选中相应的复选框来检查您想要允许的操作。单击“保存”按钮保存权限。只要您尚未保存，您就可以通过单击“还原”按钮来还原您的更改。

##### 1.6.1.1.3. **删除权限**

要删除权限，请在权限列表中选择 on，然后单击“删除”按钮。

##### 1.6.1.1.4. **创建新权限**

要创建新权限，请单击“新建”按钮。将启用“资源”文本字段进行编辑，在此处输入资源名称。新权限将立即显示在列表中。如上所述选择角色和操作以编辑现有权限。单击“保存”以存储权限。如果您决定根本不想创建新权限，请单击“删除”将其删除。

#### 1.6.1.2. **权限使用**

门户资源引用安全定义来保护该特定资源。可以保护以下资源：

· 文件夹：在文件夹元数据中

· 页面：在 PSML 文件中

· 链接：在 .link 文件中

· Portlet 窗口：页面上的一个 Portlet 实例

· Portlet 定义：所有页面上的 Portlet 的所有实例

· Portlet Application：一个portlet应用程序中的所有portlet

保护资源就像使用上面定义的管理 portlet 定义权限定义一样简单。您可以从门户的多个区域执行此操作：

· 1. 站点管理员保护文件夹、页面或链接

· 2. Portlet Application Manager，用于保护 Portlet 应用程序或 Portlet 定义

· 3. 配置模式，如果可用于 portlet，您可以保护 portlet 实例

此外，可以在部署描述符中保护 portlet。有关更多详细信息，请参阅 [部署](https://portals.apache.org/jetspeed-2/deployguide/index.html)指南。

## 1.7. [**单点登录管理**](https://portals.apache.org/jetspeed-2/adminguide/sso.html)

### 1.7.1. **Jetspeed 单点登录**

Jetspeed-2 (J2) 单点登录 (SSO) 功能是作为组件实现的凭证存储。它使用 J2 安全实现来存储凭证。管理 portlet 允许编辑 SSO 站点和远程凭据。它支持基本身份验证和基于表单的身份验证，并支持 cookie。

SSO 管理功能使您能够创建“单点登录”访问，这是对应用程序和底层工具的基于权限的访问，它为 Jetspeed-2 内容提供了额外的安全层和管理控制。SSO 管理使组的用户（最初在“组管理”选项卡中定义的几个用户）能够一次性登录 jetspeed-2 门户和指定的站点和数据库。

### 1.7.2. **SSOProxy Portlet**

顾名思义，SSOProxy portlet 是门户和经过身份验证的站点之间的代理。在首选项中，用户定义可能需要自身身份验证的目标页面或具有指向经过身份验证的页面的链接（门户内部或外部）。SSOProxy Portlet 在访问首选项中定义的目标 URL 之前为用户验证所有 SSO 站点。SSOProxy 保留代理客户端的缓存，以便仅在第一次进行身份验证。

### 1.7.3. **SSOReverseProxyIFrame Portlet**

SSOReverseProxyIFrame portlet 利用[Apache Portals Web Content Application](http://portals.apache.org/applications/webcontent/)的反向代理服务组件。此 Portlet 基于导航的 URL 向反向代理服务组件提供单点登录站点和用户凭据。如果站点在 Jetspeed-2 单点登录凭据存储中注册为用户的单点登录站点，则反向代理服务组件会自动为用户验证站点。

例如，如果设置了以下首选项，


| **偏好名称** | **偏好值**                         |
| ------------ | ---------------------------------- |
| SRC          | http://localhost:8080/manager/list |
| 代理远程URL  | http://localhost:8080/             |
| 代理路径     | \${contextPath}/rproxy/localhost/  |

然后 portlet 尝试通过 SRC URL“http://localhost:8080/manager/list”检索用户的注册 SSO 站点和 SSO 远程用户信息。

如果用户有以下 SSO 站点和 SSO 远程用户信息，


| **站点名称** | **网站网址**                   | **站点领域**         | **远程校长** | **远程凭证** |
| ------------ | ------------------------------ | -------------------- | ------------ | ------------ |
| Tomcat管理   | http://localhost:8080/manager/ | Tomcat管理器应用程序 | 雄猫         | 雄猫         |

然后反向代理服务组件可以从 portlet 中检索上述信息，并尝试通过提供的凭据进行身份验证。

如果有多个具有相似 URL 的 SSO 站点，则将选择与 URL 匹配的最佳 SSO 站点和凭据进行身份验证。例如，当用户注册了以下 SSO 站点和凭据时，


| **不。** | **站点名称**     | **网站网址**                 | **站点领域**        | **远程校长** | **远程凭证** | **用户表单字段** | **密码表单字段** |
| -------- | ---------------- | ---------------------------- | ------------------- | ------------ | ------------ | ---------------- | ---------------- |
| 1        | 我的根网站       | http://localhost:8080/       |                     | 用户         | 用户         |                  |                  |
| 2        | 我的基本认证网站 | http://localhost:8080/basic/ | ExampleBasicAuthJSP | 基本的       | 基本的       |                  |                  |
| 3        | 我的表单验证网站 | http://localhost:8080/form/  |                     | 形式         | 形式         | 用户             | 经过             |

然后将向反向代理服务组件提供最匹配的 SSO 站点和凭据信息，如下例所示：


| **请求的网址**                             | **不。** | **描述**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------ | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| http://localhost:8080/                     | 1        | 此请求的URL仅与第一个 SSO 站点 URL 匹配。                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| http://localhost:8080/index.html           | 1        | 此请求的URL以第一个 SSO 站点 URL 开头，并且仅与第一个 SSO 站点 URL 匹配。                                                                                                                                                                                                                                                                                                                                                                                                                |
| http://localhost:8080/somewhere/index.html | 1        | 此请求的URL以第一个 SSO 站点 URL 开头，并且仅与第一个 SSO 站点 URL 匹配。                                                                                                                                                                                                                                                                                                                                                                                                                |
| http://localhost:8080/basic/               | 2, 1     | 此请求的URL以第一个和第二个 SSO 站点 URL 开头。因为第二个更匹配，所以将首先使用第二个 SSO 站点和凭据信息进行身份验证。                                                                                                                                                                                                                                                                                                                                                                   |
| http://localhost:8080/basic/index.html     | 2, 1     | 此请求的URL以第一个和第二个 SSO 站点 URL 开头。因为第二个更匹配，所以将首先使用第二个 SSO 站点和凭据信息进行身份验证。                                                                                                                                                                                                                                                                                                                                                                   |
| http://localhost:8080/form/                | 3        | 此请求的URL以第一个和第三个 SSO 站点 URL 开头。第三个更匹配。但是，与基本身份验证示例不同的是，永远不会使用第一个示例，因为最匹配的 SSO 站点已配置为使用基于表单的身份验证。当最匹配的 SSO 站点配置为使用基于表单的身份验证时，反向代理服务组件将仅将其用于身份验证。<br/>仅当请求的URL等于 SSO 站点的 URL 时，反向代理服务组件才会使用指定的表单字段名称发布用户名表单字段和密码表单字段。 *如果请求的**URL**被用户在 IFrame 中的导航更改，则它不会尝试再次发布用户名和密码表单字段。* |
| http://localhost:8080/form/index.html      | 3        | 此请求的URL以第一个和第三个 SSO 站点 URL 开头。第三个更匹配。但是，与基本身份验证示例不同的是，永远不会使用第一个示例，因为最匹配的 SSO 站点已配置为使用基于表单的身份验证。当最匹配的 SSO 站点配置为使用基于表单的身份验证时，反向代理服务组件将仅将其用于身份验证。<br/>仅当请求的URL等于 SSO 站点的 URL 时，反向代理服务组件才会使用指定的表单字段名称发布用户名表单字段和密码表单字段。 *如果请求的**URL**被用户在 IFrame 中的导航更改，则它不会尝试再次发布用户名和密码表单字段。* |

### 1.7.4. **SSO 提供者服务**

SSO Provider 是 jetspeed 服务框架的一部分，可用于任何 Portlet，而不仅仅是 SSOProxy Portlet。该组件负责存储站点和凭据，并具有从 url 获取内容的 API。

### 1.7.5. **单点登录管理**

SSO 管理 Portlet 有助于管理 SSO 凭证并将其分配给门户用户。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps119.jpg)

可以通过单击用户图标或组图标来填充 Portal Principal 字段。将显示一个弹出窗口，让您选择您的用户或组。

## 1.8. [**OpenID 配置**](https://portals.apache.org/jetspeed-2/adminguide/openid.html)

Jetspeed Portal 中的 OpenID 支持默认禁用，因为它通常需要针对特定的 OpenID 提供程序进行配置。要启用它，需要在门户**web.xml**配置文件中设置 OpenID 支持过滤器和 servlet，并且需要在门户登录页面中提供 OpenID 登录 Portlet。为了利用 OpenID 单点登录 (SSO)，可以使用 OpenID 感知 portlet 无缝访问其他站点上的信息。

### 1.8.1. **启用 OpenID 过滤器和 Servlet**

需要 OpenIDPortalFilter 和 OpenIDRelayingPartyServlet 才能通过门户支持 OpenID。示例设置包含在门户**web.xml**配置文件中。servlet 初始化参数配置 OpenID 发现、OpenID 消费者实现和门户用户注册。如果需要一组以上的配置， 也可以在[OpenID 登录 portlet中完成此处找到的一些 OpenID 配置。](#Using_OpenID_Portlets)

      ...

      <过滤器>

        <filter-name>OpenIDPortalFilter</filter-name>

        <filter-class>org.apache.jetspeed.openid.filter.OpenIDPortalFilter</filter-class>

      </过滤器>

      ...

      <过滤器映射>

        <filter-name>OpenIDPortalFilter</filter-name>

        <url-pattern>/*</url-pattern>

      </filter-mapping>

      ...

      <小服务程序>

        <说明>

          OpenID 中继方 (RP)，用于返回发现的 servlet

          OpenID 领域的元数据并处理身份验证返回

          要求。

        </描述>

        <display-name>OpenID 中继方 Servlet</display-name>

        <servlet-name>OpenIDRelayingPartyServlet</servlet-name>

        <servlet-class>org.apache.jetspeed.openid.OpenIDRelayingPartyServlet</servlet-class>

        <初始化参数>

          <description>发现域到提供者 URL/主机的映射。</description>

          <param-name>discovery.gmail.com</param-name>

          <param-value>https://www.google.com/accounts/o8/id</param-value>

        </init-param>

        <初始化参数>

          <description>启用servlet初始化参数注册配置。</description>

          <param-name>enableRegistrationConfig</param-name>

          <param-value>false</param-value>

        </init-param>

        <初始化参数>

          <description>启用新用户注册。</description>

          <param-name>enableRegistration</param-name>

          <param-value>真</param-value>

        </init-param>

        <初始化参数>

          <description>用于注册的全局新用户模板目录。</description>

          <param-name>newUserTemplateDirectory</param-name>

          <param-value>/_template/new-user/</param-value>

        </init-param>

        <初始化参数>

          <description>用于注册的全局子站点根文件夹。</description>

          <param-name>subsiteRootFolder</param-name>

          <参数值></参数值>

        </init-param>

        <初始化参数>

          <description>注册时分配的全局角色。</description>

          <param-name>角色</param-name>

          <param-value>用户</param-value>

        </init-param>

        <初始化参数>

          <description>注册时分配的全局组。</description>

          <param-name>组</param-name>

          <参数值></参数值>

        </init-param>

        <初始化参数>

          <description>注册时分配的全局分析规则名称。</description>

          <param-name>rulesNames</param-name>

          <param-value>页面</param-value>

        </init-param>

        <初始化参数>

          <description>注册时分配的全局分析规则值。</description>

          <param-name>rulesValues</param-name>

          <param-value>j2</param-value>

        </init-param>

        <load-on-startup>2</load-on-startup>

      </servlet>

      ...

      <servlet 映射>

        <servlet-name>OpenIDRelayingPartyServlet</servlet-name>

        <url-pattern>/openid</url-pattern>

        <url-pattern>/openid/*</url-pattern>

      </servlet-mapping>

      ...
以下初始化参数可用于配置 OpenIDRelayingPartyServlet：


| **范围**       | **描述**                                                                                                                                                                                                                                                                                                   |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 发现。\*       | 发现域到提供者URL/主机的映射。支持的 OpenID 域附加到属性名称前缀，并为具有该属性的域设置映射的域或 URL。仅当使用非标准 OpenID 提供程序 URL（例如 Google）或需要域别名映射时，才需要此属性。示例：discovery.gmail.com = https://www.google.com/accounts/o8/id 或 discovery.anotherdomain.com = mydomain.com |
| 消费者。\*     | 发现域到消费者实现的映射。支持的OpenID域附加到属性名称前缀，并且为具有该属性的域设置映射的使用者实现名称（“step2”或“openid4java”）。此属性仅用于指定用于 Google 托管的 OpenID 域的 Google Step2 库实现（OpenID4Java 是默认实现）。示例：consumer.mydomain.com = step2。                                |
| 启用注册配置   | 启用servlet init参数注册配置。如果未设置此标志，则使用各个[OpenID登录 portlet](#Using_OpenID_Portlets)实例中的注册配置，这些配置将被忽略。                                                                                                                                                                 |
| 启用注册       | 启用新用户注册。                                                                                                                                                                                                                                                                                           |
| 新用户模板目录 | 用于注册的全局新用户模板目录。                                                                                                                                                                                                                                                                             |
| 子站点根文件夹 | 用于注册的全局子站点根文件夹。                                                                                                                                                                                                                                                                             |
| 角色           | 注册时分配的全局角色。                                                                                                                                                                                                                                                                                     |
| 团体           | 注册时分配的全局组。                                                                                                                                                                                                                                                                                       |
| 规则名称       | 要在注册时分配的全局分析规则名称。                                                                                                                                                                                                                                                                         |
| 规则值         | 要在注册时分配的全局分析规则值。                                                                                                                                                                                                                                                                           |

与其 OpenId 登录关联的用户 OpenID 电子邮件地址用作门户中的用户名。每当用户通过[OpenID 登录 portlet](#Using_OpenID_Portlets)和 OpenIDRelayingPartyServlet 进行身份验证时，以下 OpenID 属性交换和/或简单注册数据将与门户用户属性同步：


| **OpenId 数据**                                                  | **门户用户属性**                |
| ---------------------------------------------------------------- | ------------------------------- |
| 属性：http://axschema.org/contact/email<br/>简单注册：email      | user.business-info.online.email |
| 属性：http<br/>://axschema.org/namePerson简单注册：全名          | 用户名                          |
| 属性：http://axschema.org/namePerson/last<br/>简单注册：n/a      | 用户名.family                   |
| 属性：http://axschema.org/namePerson/first<br/>简单注册：n/a     | 用户名.给定                     |
| 属性：http://axschema.org/namePerson/friendly<br/>简单注册：昵称 | user.name.nickName              |

除了提供 OpenID 身份验证服务之外，OpenIDRelayingPartyServlet 还提供 OpenID 中继方元数据。元数据端点允许 OpenID 提供者将门户验证为合法的 OpenID 客户端。与元数据关联的 URI 是从元数据请求本身计算出来的（例如**http[s]://portal.mydomain.com/jetspeed/openid**）。

### 1.8.2. **使用 OpenID Portlet**

需要 OpenIDLoginPortlet 来支持门户 OpenID 登录。默认情况下，此 portlet 配置为支持 Google、Yahoo! 和 myOpenID 提供者的登录按钮，其中包含一个 OpenID 输入字段，用户可以在其中输入 OpenID URL 或提供者域。新用户注册也默认启用，（如上所述，新用户的 OpenID 电子邮件地址用作门户用户 id）。这些和新的用户注册属性可以配置为 portlet 参数和首选项。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps120.jpg)

一旦最终用户登录，OpenIDLoginPortlet 就会显示登录的用户 ID 并允许用户注销。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps121.jpg)

OpenIDLoginPortlet 支持以下配置参数和首选项：


| **参数/首选项名称** | **默认**                           | **描述**                           |
| ------------------- | ---------------------------------- | ---------------------------------- |
| 提供者标签          | Gmail、Yahoo!、myOpenID            | OpenID提供程序按钮的显示名称。     |
| 提供者域            | gmail.com、yahoo.com、myopenid.com | OpenID提供程序按钮的域名。         |
| 启用OpenIDEntry     | 真的                               | 启用OpenID提供程序或 URL 条目。    |
| 启用注册配置        | 错误的                             | 启用portlet初始化参数注册配置。    |
| 启用注册            | 真的                               | 全局启用新用户注册。               |
| 新用户模板目录      | /\_template/新用户/                | 用于注册的全局新用户模板目录。     |
| 子站点根文件夹      | *没有任何*                         | 用于注册的全局子站点根文件夹。     |
| 角色                | 用户                               | 注册时分配的全局角色。             |
| 团体                | *没有任何*                         | 注册时分配的全局组。               |
| 规则名称            | 页                                 | 要在注册时分配的全局分析规则名称。 |
| 规则值              | j2                                 | 要在注册时分配的全局分析规则值。   |

当使用 OpenIDLoginPortlet 对门户网站用户进行身份验证时，会设置包含登录域的会话属性。此会话属性 ( [PortalReservedParameters.SESSION\_OPEN\_ID\_PROVIDER](https://portals.apache.org/jetspeed-2/apidocs/org/apache/jetspeed/PortalReservedParameters.html)) 可以由其他 portlet 检查以确保用户在引用受保护资源之前已登录。OpenIDIFramePortlet 使用此技术在包含受保护的网页之前检查 OpenID 登录域。除了 IFramePortlet 首选项之外，OpenIDIFramePortlet 还支持以下配置首选项：


| **偏好名称**           | **默认**   | **描述**                 |
| ---------------------- | ---------- | ------------------------ |
| 必需的开放式提供商标签 | *没有任何* | 必需的OpenID提供者标签。 |
| 必需的OPENID提供者     | *没有任何* | 必需的OpenID提供程序域。 |

当门户使用单个特定的 OpenID 提供程序来保护企业资产时，通常会使用 OpenIDIFramePortlet。OpenIDLoginPortlet 和 OpenIDIFramePortlet 都可以进行相应的配置。

OpenIDLoginPortlet：

· providerLabels = 我的域

· providerDomains = mydomain.com

· enableOpenIDEntry = false

OpenIDIFramePortlet：

· SRC = http://www.mydomain.com/...

· REQUIREDOPENIDPROVIDERLABEL = MyDomain

· REQUIREDOPENIDPROVIDER = mydomain.com

当用户未登录时，上面的 portlet 配置将如下所示。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps122.jpg)

登录后，用户将能够在门户页面中看到受保护的内容。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps123.jpg)

## 1.9. [**空间**](https://portals.apache.org/jetspeed-2/adminguide/space-manager.html)

### 1.9.1. **空间和空间管理器**

空间是 Jetspeed 站点的顶级组织。您可以使用空间将项目或团队组织或分组到一个公共区域。然后可以使用 Space Navigator 导航到空间。空间是在 2.2.1 版中作为 JetUI 功能集的一部分引入的。有两个管理 portlet 供您管理您的空间。空间列表和空间管理器详细信息。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps124.jpg)![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps125.jpg)

空间列表显示系统中对当前用户可见的所有空间的列表。仅当您具有修改空间的安全访问权限时，该空间才可见。请注意，当您以管理员身份登录时，您实际上可能会看到其他用户拥有的空间（请参阅所有者列）。Jetspeed 将只允许您删除您拥有删除这些空间的安全权限的空间。有一个特殊的空间，叫做公共空间。这是系统上的逻辑根文件夹。它永远不能被删除。使用公共空间在系统中设置全局设置，例如默认主题或默认安全约束。然后其他空间可以覆盖这些默认设置。所有用户还将看到另一个名为**“我的页面”的特殊空间**. 它将显示为文件夹列表中的最后一个空格。这实际上是当前用户的 Home Space。每个用户都有一个家庭空间。

空间管理器详细信息允许您编辑空间的特定属性，包括

· 空间名称

· 空间所有者 - 必须是有效的用户名

· 空间标题

· 空间描述

· 此空间可能的安全约束的下拉列表。有关设置空间安全访问的更多详细信息，请参阅[安全约束指南。](https://portals.apache.org/jetspeed-2/adminguide/constraints.html)

· 空间的主题。主题是仅在 JetUI 中可用的特殊装饰器

### 1.9.2. **太空领航员**

Space Navigator 是一个 JetUI 特殊的导航 portlet，让用户可以快速访问空间。从 Space Navigator，您可以导航到系统中您可以安全访问的任何空间以查看该空间。此外，管理员可以从 Space Navigator 编辑当前空间以及创建新空间。Space Navigator 是使用 JetUI 引入的两个新特性实现的：页面模板和分离的 portlet。为了让 Space Navigator 出现在系统中的每个页面上，我们在页面模板上对其进行了配置。有关详细信息，请参阅[JetUI 指南](https://portals.apache.org/jetspeed-2/deployguide/guide-jetui.html)和[模板指南](https://portals.apache.org/jetspeed-2/deployguide/guide-page-templates.html)。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps126.jpg)

# 2. **门户管理**

## 2.1. [**远程 Portlet 应用程序管理器**](https://portals.apache.org/jetspeed-2/adminguide/rpad.html)

### 2.1.1. **远程 Portlet 应用程序部署管理指南**

Remote Portlet Application Deployer 可以在名为 RPAD 的 Jetspeed 管理 Portlets 选项卡式菜单中找到。您可以使用此 Portlet 部署包含默认情况下不可用的 Portlet 的 War 文件。一旦部署了 War，您将通过转到[编辑模式](https://portals.apache.org/jetspeed-2/usersguide/portletmodes.html)和[Add Portlet](#adding_portlets)区域找到任何新的 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps127.jpg)


| **场地** | **描述**                                                                                                                                                                        |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 组ID     | 分发战争文件的组织或公司的名称。                                                                                                                                                |
| 工件ID   | 命名可分发文件的常用方法。                                                                                                                                                      |
| 姓名     | Portlet应用程序的名称，通常与工件 ID 相同。                                                                                                                                     |
| 版本     | Portlet应用程序的版本。                                                                                                                                                         |
| 类型     | 仅限Portlet应用程序，目前始终作为战争工件分发。                                                                                                                                 |
| 行动     | 在Jetspeed中部署 portlet 应用程序。您可以使用[PALM](https://portals.apache.org/jetspeed-2/adminguide/palm.html)（Portlet Application Lifecycle Manager）管理 portlet 应用程序。 |

存储库下拉菜单列出了所有当前包含的存储库。默认情况下，所有存储库项目以 10 个为一组显示。Portlet 底部的分页将允许您浏览页面。在下拉菜单中选择一个存储库并单击选择将更改显示，以便仅显示该存储库中的项目。选择空白菜单选项将导致显示来自所有存储库的项目。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps128.jpg)

刷新按钮用于重绘窗口的内容。单击部署链接后需要刷新，因为部署操作会将所有部署链接更改为不可单击状态。这些部署链接在部署过程中将保持不可点击，无论是否按下刷新按钮。在部署过程完成并通过刷新按钮或任何其他需要 portlet 重新绘制窗口内容的操作重新绘制屏幕后，部署链接将返回到它们的正常状态。

#### 2.1.1.1. **管理存储库**

可以通过从 portlet 操作栏 进入[编辑模式来管理存储库。](https://portals.apache.org/jetspeed-2/usersguide/portletmodes.html)

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps129.jpg)

编辑操作链接将允许您更改现有信息，例如存储库名称和存储库配置文件的位置。该窗口将发生变化，类似于下图添加存储库的屏幕截图。

删除操作链接删除与链接位于同一行的存储库。

Reload Repositories 按钮将刷新每个存储库的配置 xml 文件。

Add Repository 按钮将带您进入另一个窗口，您可以在该窗口中输入存储库的名称和带有 Repository 信息的 xml 文件的配置路径。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps130.jpg)

## 2.2. [**Portlet 应用程序管理器**](https://portals.apache.org/jetspeed-2/adminguide/pam.html)

### 2.2.1. **Portlet 应用程序管理指南**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps131.jpg)

#### 2.2.1.1. **Portlet 应用程序浏览器**

Portlet Application Manager 窗口默认显示 J2_ROOT 并且它是子 APP_ROOT。单击 APP_ROOT 旁边的开关图标以显示可用应用程序的列表。每个应用程序都有一个开关图标来显示与每个应用程序相关联的一个或多个 portlet。

单击任何应用程序链接将在右侧填充 Portlet 应用程序详细信息窗口。单击任何 Portlet 链接将使用应用程序详细信息和 portlet 详细信息填充同一窗口。


| **场地**       | **描述**                                                                              |
| -------------- | ------------------------------------------------------------------------------------- |
| 搜索           | 搜索将找到与您的搜索参数匹配的任何应用程序、portlet或关键字，并将它们显示在搜索部分。 |
| 应用程序树视图 | 带有可单击链接的分层视图，用于应用程序及其关联的portlet。                             |

#### 2.2.1.2. **Portlet 应用程序详细信息 - 应用程序详细信息**

##### 2.2.1.2.1. **详细信息选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps132.jpg)


| **场地** | **描述**                                                                                                                |
| -------- | ----------------------------------------------------------------------------------------------------------------------- |
| 姓名     | 应用程序战争文件的名称。                                                                                                |
| 版本     | 应用程序的版本号。                                                                                                      |
| 描述     | 用于描述应用程序的可选字段。                                                                                            |
| 类型     | 应用程序类型。                                                                                                          |
| ID       | 一般与应用名称相同。                                                                                                    |
| 安全约束 | 下拉菜单包含以下选项：No Constraints、admin、manager、users、public-view、public-edit、AEUV、dev、devmgr 和 delegated。 |

##### 2.2.1.2.2. **元数据选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps133.jpg)


| **场地** | **描述**                       |
| -------- | ------------------------------ |
| 姓名     | 元数据字段的名称。             |
| 价值     | 与元数据字段名称关联的值。     |
| 语言环境 | 有效的2个字母的国家/地区代码。 |

##### 2.2.1.2.3. **Portlet 选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps134.jpg)


| **场地**   | **描述**                                                                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------- |
| 下拉式菜单 | 用于选择您正在查看的应用程序中包含的任何portlet的下拉菜单。选择一个 portlet 将刷新带有 portlet 详细信息的窗口。 |

##### 2.2.1.2.4. **用户属性选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps135.jpg)


| **场地** | **描述**                                                |
| -------- | ------------------------------------------------------- |
| 姓名     | 与用户关联的任何属性的字段名称。即，电话号码，姓氏等... |
| 价值     | 关联属性的值。                                          |

#### 2.2.1.3. **Portlet 应用程序详细信息 - Portlet 详细信息**

##### 2.2.1.3.1. **详细信息选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps136.jpg)


| **场地**     | **描述**                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------ |
| 过期缓存     | 值-1将 Expiration 设置为永不过期。0 表示不使用过期时间。任何其他值将以秒为单位过期。                         |
| ID           | portlet的标识。                                                                                              |
| 唯一名称     | 该字段的格式为application::ID。                                                                              |
| 首选项验证器 | 实现PreferencesValidator接口的类可以与部署描述符中的首选项定义相关联。                                       |
| 班级名称     | 包含portlet的完全限定类名。                                                                                  |
| 显示名称     | 允许多个条目。可以在下面的部分中添加该区域设置的有效2字母国家代码和将在该区域设置中为该 Portlet 显示的名称。 |

##### 2.2.1.3.2. **元数据选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps137.jpg)


| **场地** | **描述**                                              |
| -------- | ----------------------------------------------------- |
| 姓名     | 元数据字段的名称。                                    |
| 语言环境 | 一个有效的2个字母的国家代码。关联元数据字段名称的值。 |
| 价值     | 有效的2个字母的国家/地区代码。                        |

##### 2.2.1.3.3. **首选项选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps138.jpg)


| **场地** | **描述**                     |
| -------- | ---------------------------- |
| 姓名     | 您希望创建的首选项的名称。   |
| 价值     | 要与首选项关联的首选项的值。 |

##### 2.2.1.3.4. **语言标签**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps139.jpg)


| **场地** | **描述**                                |
| -------- | --------------------------------------- |
| 标题     | 出现在portlet标题栏中的标题。           |
| 短标题   | 一个简短的描述性标题。                  |
| 关键词   | 要与portlet关联的关键字的逗号分隔列表。 |
| 语言环境 | 有效的2个字母的国家/地区代码。          |

##### 2.2.1.3.5. **参数选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps140.jpg)


| **场地** | **描述**                      |
| -------- | ----------------------------- |
| 姓名     | 要与portlet关联的参数的名称。 |
| 价值     | 要与参数名称关联的值。        |
| 描述     | portlet的可选描述。           |
| 语言环境 | 可选的有效2字母国家代码。     |

##### 2.2.1.3.6. **安全选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps141.jpg)


| **场地** | **描述**                                                                                                                |
| -------- | ----------------------------------------------------------------------------------------------------------------------- |
| 角色名称 | 角色的名称。                                                                                                            |
| 角色链接 | 角色链接的id。                                                                                                          |
| 描述     | 此项目的描述性短语。                                                                                                    |
| 语言环境 | 有效的2个字母的国家/地区代码。                                                                                          |
| 安全约束 | 下拉菜单包含以下选项：No Constraints、admin、manager、users、public-view、public-edit、AEUV、dev、devmgr 和 delegated。 |

##### 2.2.1.3.7. **内容类型选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps142.jpg)


| **场地**    | **描述**                                                                    |
| ----------- | --------------------------------------------------------------------------- |
| 内容类型    | 像text/html这样的 MimeType。允许使用通配符。                                |
| Portlet模式 | portlet支持的标准 portlet 模式。按住 Shift 单击以选择多个。                 |
| 自定义模式  | portlet支持的自定义模式。自定义模式直接添加到任何标准模式之后的模式列表中。 |

## 2.3. [**门户网站管理员**](https://portals.apache.org/jetspeed-2/adminguide/site.html)

### 2.3.1. **门户网站管理指南**

门户站点管理器可以看作是一个类似于文件系统的门户资源树。

该网站由三种不同的资源组成：

· [PSML 页面](#PSML_Pages)

· [文件夹](#Folders)

· [链接](#Links)

所有门户资源都可以在 Jetspeed 中自定义。Portal Site Manager 只是可用于定制的工具之一。其他工具是 Jetspeed Customizer（桌面和门户）、编辑模式、配置模式、portlet 的编辑默认模式和 Portlet 选择器。

#### 2.3.1.1. **PSML 页面**

用于定义构成站点的资源和元素的 XML 方言也称为 PSML（门户结构标记语言）。PSML 不是标准。

PSML 页面定义了 portlet 在页面上的放置方式和位置，以及页面的装饰和标记方式。

PSML 页面定义：

· 元数据，例如标题和描述

· 装饰（页面和portlet）

· 布局片段（页面上的列数和列的嵌套）

· 哪些 portlet 显示在页面上，由 portlet 片段定义

· portlet 在页面上的位置

· portlet 的属性

· portlet 的首选项

· 安全约束

要通过 Portal Site Manager 自定义 PSML 页面，请在树中选择它。树的右侧将出现四个选项卡，允许您通过表单自定义页面的各个方面。

下面描述了四个选项卡中的每一个。

##### 2.3.1.1.1. **信息选项卡**

信息选项卡允许您自定义页面的标题和外观。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps143.jpg)


| **场地**      | **描述**                                         |
| ------------- | ------------------------------------------------ |
| 姓名          | .psml文件的名称。                                |
| 标题          | 此对象的xml标题字段中显示的名称。                |
| 短标题        | 出现在此对象的xml短标题字段中的名称。            |
| 页面装饰器    | 所有可用页面装饰器的下拉菜单。                   |
| Portlet装饰器 | 所有可用portlet装饰器的下拉菜单。                |
| 桌面主题      | 所有可用桌面主题的下拉菜单。                     |
| 隐            | 隐藏的文件夹不会显示在菜单上，但仍然可以导航到。 |

##### 2.3.1.1.2. **安全选项卡**

安全选项卡允许您修改页面的安全约束。为选定页面定义的所有安全约束都显示在列表中。要修改约束，请从列表中选择它并在下拉字段中选择一个新值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps144.jpg)


| **场地** | **描述**                                 |
| -------- | ---------------------------------------- |
| 约束     | 此处将为所选项目列出任何安全和约束类型。 |

##### 2.3.1.1.3. **元数据选项卡**

元数据选项卡显示可能为页面定义的元数据属性列表，例如页面标题的不同语言的翻译，如下面的屏幕截图所示。单击属性将在列表正下方的表单中加载它，以便可以修改值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps145.jpg)


| **场地** | **描述**                      |
| -------- | ----------------------------- |
| 姓名     | 此对象的xml文件中的属性名称。 |
| 语言     | 属性的本地化。                |
| 价值     | 要本地化的文本。              |

##### 2.3.1.1.4. **导出选项卡**

导出选项卡提供页面的 XML 导出。导出的 XML 文件可用于将通过用户界面进行的自定义存储在自定义门户项目中，以便在部署新版本的门户时，不必再次进行自定义。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps146.jpg)


| **场地** | **描述**                |
| -------- | ----------------------- |
| 导出对象 | 以XML格式导出所选项目。 |

#### 2.3.1.2. **链接**

链接是指向外部资源的 URL，通常在站点之外。该元素以 .link 扩展名保存在文件系统上。

要通过 Portal Site Manager 自定义链接，请在树中选择它。树的右侧将出现四个选项卡，允许您通过表单自定义链接的各个方面。

下面描述了四个选项卡中的每一个。

##### 2.3.1.2.1. **信息选项卡**

信息选项卡允许您更改链接的标题和 URL。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps147.jpg)


| **场地** | **描述**                                                      |
| -------- | ------------------------------------------------------------- |
| 姓名     | .link文件的名称。                                             |
| 标题     | 此对象的xml标题字段中显示的名称。                             |
| 短标题   | 出现在此对象的xml短标题字段中的名称。                         |
| 网址     | 单击时要显示的资源。                                          |
| 目标窗口 | 单击链接以显示目标时的Web浏览器操作。（新，自我，父母，顶部） |
| 隐       | 隐藏的文件夹不会显示在菜单上，但仍然可以导航到。              |

##### 2.3.1.2.2. **安全选项卡**

安全选项卡允许您修改链接的安全约束。为选定链接定义的所有安全约束都显示在列表中。要修改约束，请从列表中选择它并在下拉字段中选择一个新值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps148.jpg)


| **场地** | **描述**                                 |
| -------- | ---------------------------------------- |
| 约束     | 此处将为所选项目列出任何安全和约束类型。 |

##### 2.3.1.2.3. **元数据选项卡**

元数据选项卡显示可能为链接定义的元数据属性列表，例如链接标题的不同语言的翻译，如下面的屏幕截图所示。单击属性将在列表正下方的表单中加载它，以便可以修改值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps149.jpg)


| **场地** | **描述**                      |
| -------- | ----------------------------- |
| 姓名     | 此对象的xml文件中的属性名称。 |
| 语言     | 属性的本地化。                |
| 价值     | 要本地化的文本。              |

##### 2.3.1.2.4. **导出选项卡**

导出选项卡允许您将链接导出到 XML 文件。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps150.jpg)


| **场地** | **描述**                |
| -------- | ----------------------- |
| 导出对象 | 以xml格式导出所选项目。 |

#### 2.3.1.3. **文件夹**

文件夹是一个容器对象，它包含：

· 子文件夹（它又可以包含子文件夹、页面、链接...）

· 页面

· 链接

文件夹构成您网站的物理布局，并具有以下属性：

· 可本地化的元数据（名称、标题、短标题、描述）

· 可选的默认页面

· 可选装饰器

· 隐藏标志（隐藏文件夹不显示在菜单上，但仍可以导航到）

· 安全约束

· 菜单

· 文件排序

要通过 Portal Site Manager 自定义文件夹，请在树中选择它。树的右侧将出现七个选项卡，允许您通过表单自定义链接的各个方面。

下面描述了七个选项卡中的五个（信息、安全、元数据、导入、导出）。菜单和订单选项卡是未来功能的占位符，目前不包含任何信息。

##### 2.3.1.3.1. **信息选项卡**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps151.jpg)


| **场地**      | **描述**                                         |
| ------------- | ------------------------------------------------ |
| 姓名          | Portal Site Manager树中文件夹的名称。            |
| 标题          | 出现在xml文件中的文件夹的标题。                  |
| 短标题        | 出现在xml文件中的文件夹的短平铺。                |
| 默认页面      | 选修的。浏览时默认的页面。                       |
| 页面装饰器    | 所有可用页面装饰器的下拉菜单。                   |
| Portlet装饰器 | 所有可用portlet装饰器的下拉菜单。                |
| 隐            | 隐藏的文件夹不会显示在菜单上，但仍然可以导航到。 |

##### 2.3.1.3.2. **安全选项卡**

安全选项卡允许您修改文件夹的安全约束。为选定文件夹定义的所有安全约束都显示在列表中。要修改约束，请从列表中选择它并在下拉字段中选择一个新值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps152.jpg)


| **场地** | **描述**                                 |
| -------- | ---------------------------------------- |
| 约束     | 此处将为所选项目列出任何安全和约束类型。 |

##### 2.3.1.3.3. **元数据选项卡**

元数据选项卡显示可能为文件夹定义的元数据属性列表，例如文件夹标题的不同语言的翻译，如下面的屏幕截图所示。单击属性将在列表正下方的表单中加载它，以便可以修改值。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps153.jpg)


| **场地** | **描述**                      |
| -------- | ----------------------------- |
| 姓名     | 此对象的xml文件中的属性名称。 |
| 语言     | 属性的本地化。                |
| 价值     | 要本地化的文本。              |

##### 2.3.1.3.4. **导入选项卡**

导入选项卡允许您导入以前导出为 XML 文件的文件夹。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps154.jpg)


| **场地**     | **描述**                                      |
| ------------ | --------------------------------------------- |
| 要导入的文件 | 使用浏览按钮在本地文件中搜索要导入的xml文件。 |
| 文件目的地   | 放置正在导入的xml文件的路径。                 |

##### 2.3.1.3.5. **导出选项卡**

导出选项卡允许您将文件夹导出到 XML 文件。或者，您也可以通过选中“递归导出”复选框以递归方式导出文件夹内的所有子项目。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps155.jpg)


| **场地** | **描述**                                    |
| -------- | ------------------------------------------- |
| 导出对象 | 以xml格式导出 folder.metadata。             |
| 递归导出 | 以xml格式导出所有子项以及 folder.metadata。 |

#### 2.3.1.4. **门户树与用户树**

有系统范围的门户资源和个性化或用户特定的门户资源。这些由单独的树表示。Portal Site Manager 允许您在这两个树之间切换。

##### 2.3.1.4.1. **传送门树**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps156.jpg)

##### 2.3.1.4.2. **用户树**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps157.jpg)

#### 2.3.1.5. **控制文件夹**

控制文件夹始终以下划线 \_ 开头。

控制文件夹用于根据运行时参数分隔页面。例如，您可能有一组不同的手机页面与完整的网络浏览器。在这种情况下，您将手机页面放置在 WML 目录下，其中每个页面的 portlet 可能比 HTML 目录少。

有一个名为 (\_subsite\_root) 的特殊文件夹：

· 子站点将您的门户站点细分为独立的“门户站点”树。这支持用例场景，例如在同一门户实例（应用服务器）上托管两个或更多门户

· 可以将用户配置为指向特定的子站点，该子站点将成为他们的门户视图

用户文件夹 (\_user)：

· \_user 文件夹包含所有用户的主页。每个用户可以拥有一个包含多个子文件夹、页面和链接的文件夹

· 用户不需要拥有主文件夹。根据用户个人资料，可能会或可能不会使用用户主页

· 通常，用户的主页对用户是可定制的（可编辑的），但对其他人不能

· 当用户首次注册或由管理员创建时，Jetspeed 使用“模板”为用户创建默认页面

角色和组文件夹（\_role 和 _group）：

· 角色和组文件夹对于根据用户所属的角色或组共享页面很有用。典型的用例是授予（或拒绝）对页面的访问权限

· 角色文件夹名称应与系统中定义的角色相同，对于组也是如此

· 用户的个人资料定义了要搜索的页面

· 名为“role-fallback”的用户配置文件根据用户的安全配置文件在 _role 目录中查找页面。它将根据用户拥有的角色搜索所有文件夹

· 一个常见的配置文件规则是首先搜索用户的主目录，然后搜索给定用户的每个角色目录，以及默认的根树来查找页面

## 2.4. [**Portlet 应用程序生命周期管理器**](https://portals.apache.org/jetspeed-2/adminguide/palm.html)

### 2.4.1. **Portlet 应用程序生命周期管理指南**

Portlet Application Lifecycle Manager 可以在名为 PALM 的 Jetspeed 管理 Portlets 选项卡式菜单中找到。此管理 portlet 可用于管理从通过 RPAD 添加或作为默认安装的一部分的 war 文件部署的 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps158.jpg)


| **场地** | **描述**                                                                                      |                                                                                                                                                                  |
| -------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 姓名     | 对应于[RPAD portlet中的工件 ID。](https://portals.apache.org/jetspeed-2/adminguide/rpad.html) |                                                                                                                                                                  |
| 版本     | 默认为1.0。                                                                                   |                                                                                                                                                                  |
| 小路     | 路径是Portlet文件相对于应用程序服务器的 webapps 文件夹的位置。                                |                                                                                                                                                                  |
| 跑步     | 显示Portlet的状态。真或假值。                                                                 |                                                                                                                                                                  |
| 命令     | 对同一行中列出的portlet执行的操作。                                                           |                                                                                                                                                                  |
|          | 开始                                                                                          | 启动已使用stop命令停止的 portlet，不会启动未部署的 portlet。                                                                                                     |
|          | 停止                                                                                          | 将正在运行的portlet的状态从 true 更改为 false。Portlet 将保留在之前添加的页面上。                                                                                |
|          | 取消部署                                                                                      | 禁用portlet。Portlet 必须先从[RPAD](https://portals.apache.org/jetspeed-2/adminguide/rpad.html)重新部署，然后才能再次启动。Portlet在 Add Portlets 部分中仍然可用 |
|          | 删除                                                                                          | 从portlet列表中删除 portlet 并从 Add Portlet 部分的 portlet 列表中删除。                                                                                         |

每个命令启动、停止、取消部署和删除都将在下拉窗口中显示一条警告消息，要求您确认您的操作。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps159.jpg)

所需的 portlet 的命令部分将没有可单击的链接，以防止禁用 Jetspeed。

## 2.5. [**探查器管理**](https://portals.apache.org/jetspeed-2/adminguide/profiler.html)

### 2.5.1. **探查器概述**

Jetspeed Profiler 是一个基于门户资源定位规则的引擎。探查器定位以下类型的门户资源：

· PSML 页面

· 文件夹

· 菜单

· 链接

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps160.jpg)

当门户收到请求时，分析器将计算一个规范化的指令集，称为配置文件定位器。然后将定位器添加到请求上下文中，Jetspeed 管道上的后续组件，尤其是页面管理器和门户站点组件，可以从中获取配置文件定位器并使用它来查找请求的资源。例如，页面管理器使用定位器来查找页面或文件夹。Portal Site 组件使用定位器在菜单上构建选项。

配置文件定位器是分析器的输出。输入是一组标准化的运行时参数和状态。分析器输入在分析规则中定义，并且可以由管道上可用的任何 Java 类组成。Jetspeed 带有相当多的预定义规则，用于从请求参数、HTTP 标头、安全信息、语言和会话属性中获取标准。在分析器阀中的 Jetspeed 请求处理管道期间调用分析器。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps161.png)

所有这些运行时参数都称为*配置文件标准*，分析器使用它来定位门户资源。

### 2.5.2. **定位门户资源：页面**

Profiler 搜索 PSML 页面的目录树，试图找到要显示的 PSML 页面。默认情况下，此目录结构位于 WEB-INF/pages 下。pages 目录也可以存储在数据库中。该目录结构由门户资源（页面、文件夹、菜单、链接）组成，是门户站点的*物理*表示。Jetspeed 团队还计划在未来版本中支持门户网站的*逻辑*视图。

类似于文件系统，门户站点有一个物理根。但是，使用*子*站点的概念，Jetspeed 站点可以支持对其他子站点或主站点不可见的整个子站点。探查器标准化了几个保留（系统）目录：


| **保留文件夹** | **描述**                         |
| -------------- | -------------------------------- |
| \_用户         | 保存所有用户特定的文件夹和页面   |
| \_角色         | 保存所有按角色组织的文件夹和页面 |
| \_团体         | 保存所有按组组织的文件夹和页面   |
| \_subsite-root | 包含完整的子站点树，就像根树一样 |

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps162.png)

通过应用分析规则，分析器在门户网站目录中定位页面。

### 2.5.3. **分析规则**

ProfilingRule 定义了在评估请求以确定特定资源的位置时使用的标准列表。剖析器使用剖析规则根据已知 Portlet 请求数据的解耦标准定位门户资源。规则由应按给定顺序应用的标准的有序列表组成。按照此规则的顺序，分析引擎使用不太具体的算法应用规则的每个标准，直到考虑到最不具体的资源标准。当所有条件都用尽时，规则将失败并且需要备用资源。

#### 2.5.3.1. **规则标准**

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps163.png)

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

#### 2.5.3.2. **规则标准解析器**

下表显示了 Jetspeed 开箱即用的所有默认规则标准解析器。解析器是 Java 类，实现来自 Jetspeed API *org.apache.jetspeed.profiler.rules.RuleCriterionResolver*的接口。您可以使用这组默认的解析器来构建您自己的分析规则。规则当前存储在 Jetspeed 数据库中。门户管理员可以使用管理 portlet 编辑规则。在演示系统中，以用户“admin”的身份登录以查看 Jetspeed Profiler Administration portlet 的示例。

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

#### 2.5.3.3. **默认规则**

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
### 2.5.4. **个人资料定位器**

配置文件定位器用于定位配置文件的门户资源，例如页面、文件夹、菜单和链接。定位器包含一组描述要定位的实际资源的属性（名称值对）。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps164.png)

分析器将运行时信息作为输入，概括为通用配置文件定位器，这些定位器被传递给页面管理器以定位页面或菜单。配置文件定位器被规范化并且不耦合到分析器或页面管理器实现。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps165.png)

## 2.6. [**搜索**](https://portals.apache.org/jetspeed-2/adminguide/search.html)

### 2.6.1. **使用 Jetspeed 搜索引擎**

Jetspeed-2**SearchEngine**公开了一个**search**返回的操作**SearchResults**。**SearchResult**可以迭代以显示搜索结果 。

#### 2.6.1.1. **Portlet 搜索**

**SearchEngine**Portlet使用 Jetspeed-2**PortletApplicationBrowser**根据给定的标准搜索和检索Portlet。
![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps166.png)

执行“security”搜索将返回所有匹配的 portlet 和 portlet 定义。

## 2.7. [**门户统计**](https://portals.apache.org/jetspeed-2/adminguide/statistics.html)

### 2.7.1. **查看统计信息**

Jetpseed-2 提供了报告门户统计信息的管理 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps167.png)
![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps168.png)

## 2.8. [**Portlet 选择器**](https://portals.apache.org/jetspeed-2/adminguide/portlet-selector.html)

### 2.8.1. **添加 Portlet**

进入portlet窗口的编辑模式，点击右上角的Add Portlet。Portlet Selector 窗口显示可供您添加的 portlet。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps169.png)

定位 portlet 的主要方法有 3 种。


| **方法** | **描述**                                    |
| -------- | ------------------------------------------- |
| 导航     | 您可以使用编号链接浏览多个页面。            |
| 搜索     | 提供了一个搜索字段，用于按名称搜索portlet。 |
| 类别     | Portlet分为可点击的类别。                   |

portlet 选择器显示 portlet 的名称、简要说明、添加选项和当前正在运行的 portlet 实例数量的计数器。单击添加链接将使计数器增加 1，但此时不会发生其他可见更改。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps170.jpg)

单击 [GoBack] 选项或箭头将带您进入原始定制窗口，您可以在该窗口中看到您的 portlet 已添加到您的 portlet 窗口中。如果您更改了默认装饰器的装饰器，您可能会发现新的 portlet 使用的是不同的装饰器，而不是您现在使用的装饰器。

在看到恢复选项以离开配置区域之前，您需要先返回到原始自定义窗口。

## 2.9. [**Portlet 跟踪**](https://portals.apache.org/jetspeed-2/adminguide/tracking.html)

## 2.10. [**进出口服务**](https://portals.apache.org/jetspeed-2/adminguide/import.html)

导入/导出服务 Portlet 可用于将属性导出到 xml 文件或从 xml 文件导入属性。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps171.jpg)

### 2.10.1. **出口**

使用此 Portlet 可以一起或单独导出四个部分。用户/组/角色、分析规则、功能和权限可导出为 xml 文件。单击要检索的部分或部分，然后单击导出按钮。标题为“下载”的导出按钮右侧将出现一个新链接。单击下载链接会显示在浏览器窗口中导出的 xml 内容。

使用另存为选项将 xml 文件保存在浏览器窗口中，类型为 xml。文件名默认为 tmpExport.xml，重命名并保存到合适的位置。

### 2.10.2. **出口偏好**

导出中的第二部分称为导出首选项。Export Preferences 将检索当前在 Jetspeed 中配置的 portlet 首选项。

使用另存为选项将 xml 文件保存在浏览器窗口中，类型为 xml。文件名默认为 tmpExport.xml，重命名并保存到合适的位置。

### 2.10.3. **进口**

Import 将允许您检索以前导出的 xml 文件或另一个以 xml 格式正确格式化的文件，以用于 Jetspeed。单击浏览按钮，您的浏览器窗口打开对话窗口将允许您在系统中导航文件。找到文件并单击打开。该文件现在将显示在“选择要导入的文件”字段中。单击“导入”按钮以完成该过程。“文件导入成功”消息将出现在 portlet 窗口中 Import 字样的正下方。

## 2.11. [**子网站**](https://portals.apache.org/jetspeed-2/adminguide/subsites.html)

子站点是一种将门户站点地图细分为独立的“门户站点”树的功能。这支持用例场景，例如在同一门户实例（应用程序服务器）上托管两个或多个 Jetspeed 门户。使用子站点，可以将用户子集配置为仅查看整个门户站点的子树或子站点。这些用户永远不会看到其子站点之外的内容。子站点的创建基于分析规则。您应用分析规则将用户导航到他们的子站点根目录。在这个例子中，

### 2.11.1. **子站点方案：按主机名的子站点**

为了将用户引导到不同的子站点，您需要定义一组规则，称为分析规则。这些规则决定了哪些子站点用户和访客将访问。规则基于运行时参数，例如用户名、当前用户的角色、请求参数、会话状态等。在此示例中，我们将研究根据 URL 的**主机名**部分将用户引导到子站点。我们要研究的用例场景是：

· 您托管不同站点的虚拟托管方案。

· 具有两个或更多站点的单个组织，这些站点也可能在这些子站点中具有一些共同的内容。

#### 2.11.1.1. **虚拟主机**

在我们的虚拟主机示例中，我们托管了三个不同的门户网站子站点：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps172.png)

在这里，我们为三个不同的公司定义了三个子站点（四个包括本地主机）：

· www.company-1.com - “公司 1”的子网站

· www.company-2.com - “公司 2”的子网站

· www.company-3.com - “公司 3”的子网站

#### 2.11.1.2. **单一组织**

在我们的单一组织示例中，我们在组织内托管三个不同的门户子站点：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps173.png)

在这里，我们为三个不同的公司定义了三个子站点（四个包括本地主机）：

· employees.my-company.com - 员工子网站

· partner.my-company.com - 合作伙伴的子网站

· www.my-company.com - 公众子网站

#### 2.11.1.3. **现场经理**

上面的屏幕截图显示使用站点管理器来配置您的子站点。站点管理器对于配置实时站点很有用。最初配置站点时，子站点在文件系统上配置为文件夹、子文件夹和页面。或者，可以将这些文件夹导入数据库中。有关在数据库中存储子站点的详细信息， 请参阅[数据库页面管理器。](https://portals.apache.org/jetspeed-2/devguide/guide-psml.html)

站点管理器在树视图中镜像您的文件系统（或数据库结构）。查看上面的站点视图屏幕截图，我们需要注意几个目录：

· **\_\_subsite-root** - 这是一个保留目录，包含所有子站点控制根

· **\_hostname** - 这是一个包含所有基于主机名的子站点的*控制*目录（以下划线前缀）

控制目录必须始终以下划线开头。分析规则根据运行时参数在控制目录中导航。在此示例中，我们基于主机名运行时参数创建子站点

#### 2.11.1.4. **/etc/hosts**

请注意，本地主机站点仅供开发人员使用。**甚至开发人员也可以通过在本地机器上编辑他们的/etc/hosts**文件（在 Windows 上的**\\windows\\system32\\drivers\\etc\\hosts 下**）并制作虚假条目来模拟虚拟主机环境，例如：

    127.0.0.1 www.company-1.com

    127.0.0.1 www.company-2.com

    127.0.0.1 www.company-3.com

    127.0.0.1 employees.my-company.com

    127.0.0.1 partners.my-company.com

    127.0.0.1 www.my-company.com
### 2.11.2. **XML 种子配置**

最初设置您的 Jetspeed 门户时，您需要为您的门户提供初始种子数据。在这里，我们演示了如何为子站点配置 XML 种子数据。我们将初始化：

· 分析规则

· 用户

#### 2.11.2.1. **分析规则**

<ProfilingRule id="subsite-by-hostname" standardRule="false">

<description value="指定子站点和主页的基于角色回退算法的规则"/>

<标准>

	<条件名称="导航">

		<type value="导航"/>

		<value value="subsite-root"/>

		<fallBackOrder value="0"/>

		<fallBackType value="2"/>

	</标准>

	<标准名称="主机名">

		<type value="主机名"/>

		<fallBackOrder value="1"/>

		<fallBackType value="2"/>

	</标准>

	<条件名称="用户">

		<type value="用户"/>

		<fallBackOrder value="2"/>

		<fallBackType value="2"/>

	</标准>

	<条件名称="navigation-2">

		<type value="导航"/>

		<value value="subsite-root"/>

		<fallBackOrder value="3"/>

		<fallBackType value="2"/>

	</标准>

	<Criterion name="hostname-2">

		<type value="主机名"/>

		<fallBackOrder value="4"/>

		<fallBackType value="2"/>

	</标准>

	<条件名称="角色">

		<type value="角色"/>

		<fallBackOrder value="5"/>

		<fallBackType value="2"/>

	</标准>			

	<条件名称="路径">

		<type value="path"/>

		<value value="home"/>

		<fallBackOrder value="6"/>

		<fallBackType value="2"/>

	</标准>

</标准>
</ProfilingRule>                               

分析规则包含一个或多个标准。每个标准都定义了有关如何在物理门户站点地图中定位页面的指令。*导航*类型的标准用于向下导航门户站点树。fallBackOrder标签通常应该按顺序列出*。*您几乎总是可以使用 2 的*fallBackType*。所有可用的标准*类型*都记录在在线[Profiler Guide中](https://portals.apache.org/jetspeed-2/adminguide/profiler.html). 下表描述了我们的子站点规则中的每个标准以及如何在子站点定位算法中使用它。此规则是使用用户角色回退算法的子站点位置规则。用户角色回退算法首先在用户主目录中查找页面。如果在那里找不到，他们就会在每个用户对应的角色目录中寻找一个页面。还有其他开箱即用的算法，例如角色回退、组回退、媒体类型/语言回退。或者，您可以通过在 XML 种子数据中创建新的分析规则或使用 Profiler Admininistrative portlet 创建自己的算法。


| **姓名** | **类型** | **价值**         | **描述**                                                                                                                                                                                                                                                                     |
| -------- | -------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 导航     | 导航     | 子站点根         | 导航到物理/\_\_subsite-root目录。                                                                                                                                                                                                                                            |
| 主机名   | 主机名   | （在运行时提供） | 导航到控制目录/\_\_subsite-root/\_hostname，然后导航到与运行时 _hostname 参数匹配的子目录。如果运行时_hostname 参数等于“localhost”，那么物理位置是/__subsite-root/_hostname/localhost。                                                                                    |
| 用户     | 用户     | （在运行时提供） | 导航到控制目录/\_\_subsite-root/\_hostname/user，然后导航到与运行时 _user 参数匹配的子目录。如果运行时 _user 参数等于“dean”，则物理位置为 /__subsite-root/_hostname/localhost/_user/dean。                                                                                 |
| 导航-2   | 导航     | 子站点根         | 当在用户目录下找不到页面时，我们重新开始并导航回子站点根目录。                                                                                                                                                                                                               |
| 主机名   | 主机名   | （在运行时提供） | 然后再次导航到\_hostname目录                                                                                                                                                                                                                                                 |
| 角色     | 角色     | （在运行时提供） | 导航到给定用户的每个角色目录，直到找到该页面。例如，对于名为“role1”的角色，导航到控制目录 /__subsite-root/_hostname/role，然后导航到与每个运行时 _role 参数匹配的子目录。如果运行时_role参数只有“role1”，那么物理位置是/__subsite-root/_hostname/localhost/_role/role1。 |
| 小路     | 小路     | 家               | 这是在所有计算中使用的常量，URL的路径部分，例如 home.psml 或 /accounting/worksheet.psml。它总是附加到计算的路径中，以提供页面的完整物理地址。在没有指定页面的情况下，使用规则“home”中提供的默认值，并且实际上映射到“home.psml”作为默认页面扩展。                         |

下面的屏幕截图显示了*localhost*子站点的目录树。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps174.png)

注意 \_user 和 _role 目录。这些是基于运行时参数*用户*和*角色的控制目录*. user 参数代表当前登录用户的用户名。角色参数可以表示当前用户的一个或多个角色。子站点算法将首先向下导航到用户目录，然后按名称在目录中查找当前用户。它将在那里查找 URL 上请求的当前页面的名称。给定以下示例运行时参数，下表演示了分析器在给定子站点分析规则的情况下定位页面时使用的后备搜索路径算法。一旦找到该页面，立即返回该页面并终止算法。对于以下每个示例，请考虑以下运行时参数：


| 用户名 | 院长                |
| ------ | ------------------- |
| 角色   | 角色1、角色2、角色3 |
| 主机名 | 本地主机            |

**http://localhost:8080/jetspeed/portal/calendar.psml**


| **网址**                                            | **站点物理位置**                                                  |
| --------------------------------------------------- | ----------------------------------------------------------------- |
| http://localhost:8080/jetspeed/portal/calendar.psml | /\_\_subsite-root/\_hostname/localhost/\_user/dean/calendar.psml  |
|                                                     | /\_\_subsite-root/\_hostname/localhost/\_role/role1/calendar.psml |
|                                                     | /\_\_subsite-root/\_hostname/localhost/\_role/role2/calendar.psml |
|                                                     | /\_\_subsite-root/\_hostname/localhost/\_role/role3/calendar.psml |
|                                                     | /\_\_subsite-root/\_hostname/localhost/calendar.psml              |
|                                                     | /\_\_subsite-root/calendar.psml                                   |

**http://localhost:8080/jetspeed/portal/accounting/worksheet.psml**


| **网址**                                                         | **站点物理位置**                                                              |
| ---------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| http://localhost:8080/jetspeed/portal/accounting/worksheets.psml | /\_\_subsite-root/\_hostname/localhost/\_user/dean/accounting/worksheet.psml  |
|                                                                  | /\_\_subsite-root/\_hostname/localhost/\_role/role1/accounting/worksheet.psml |
|                                                                  | /\_\_subsite-root/\_hostname/localhost/\_role/role2/accounting/worksheet.psml |
|                                                                  | /\_\_subsite-root/\_hostname/localhost/\_role/role3/accounting/worksheet.psml |
|                                                                  | /\_\_subsite-root/\_hostname/localhost/accounting/worksheet.psml              |
|                                                                  | /\_\_subsite-root/accounting/worksheet.psml                                   |

**http://localhost:8080/jetspeed/portal/**


| **网址**                               | **站点物理位置**                                              |
| -------------------------------------- | ------------------------------------------------------------- |
| http://localhost:8080/jetspeed/portal/ | /\_\_subsite-root/\_hostname/localhost/\_user/dean/home.psml  |
|                                        | /\_\_subsite-root/\_hostname/localhost/\_role/role1/home.psml |
|                                        | /\_\_subsite-root/\_hostname/localhost/\_role/role2/home.psml |
|                                        | /\_\_subsite-root/\_hostname/localhost/\_role/role3/home.psml |
|                                        | /\_\_subsite-root/\_hostname/localhost/home.psml              |
|                                        | /\_\_subsite-root/home.psml                                   |

#### 2.11.2.2. **与用户关联的规则**

所有用户都与分析规则显式或隐式关联。用户管理实用程序有一个选项卡来设置与用户关联的分析规则：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps175.png)

此外，您可以将用户与 XML 种子数据配置中的分析规则相关联：

<用户>

...                

<用户名="jetspeed">

<credentials password="jetspeed" enabled="TRUE" requiresUpdate="FALSE"/>

<角色>经理</角色>

<groups>工程</groups>

<首选项/>

<用户信息/>

<规则>

	<Rule locator="menu" rule="role-group"/>

	<Rule locator="page" rule="role-fallback"/>

</规则>
</用户>

</用户>                

查看用户的**规则**元素，定位器可以是：

· page - 使用关联的分析规则来定位页面

· menu - 使用关联的分析规则来定位菜单（如果没有指定，使用页面定位器）

**User 的Rule**元素上的**rule**属性定义与页面或菜单定位器相关联的分析规则。如果用户未与定位器关联，则在 Spring 配置文件*profiler.xml*中配置了系统范围的定位器。请参阅 index = 1 的 contructor-arg。此定位器是系统范围内的默认定位器，用于当没有关联的分析规则时。通常，概要分析规则在活动期间与用户相关联，例如使用用户管理 portlet 创建新用户，或在新用户注册期间。

<豆类>

<!-- 分析器 -->

<bean id="profilerImpl" class="org.apache.jetspeed.profiler.impl.JetspeedProfilerImpl" init-method="init">

    <constructor-arg index="0">

        <value>JETSPEED-INF/ojb/profiler_repository.xml</value>

    </constructor-arg>

    <constructor-arg index="1">

        <值>j2</值>

    </constructor-arg>                

    ……
### 2.11.3. **主机名分析规则配置**

主机名可以选择使用整个主机名或前缀。这是在 Spring 配置文件*profiler.xml*中配置的。

<bean id='HostnameCriterionResolver' 类='org.apache.jetspeed.profiler.rules.impl.HostnameCriterionResolver'>

  <!-- 使用点前缀，例如：“accounting.xyz.com”返回“accounting”-->

  <constructor-arg type="boolean" index="0">

        <值>假</值>

    </constructor-arg>    

</豆>                    
通过将前缀布尔参数设置为 true，主机名解析将只查看主机名的前缀。例如，点前缀标志设置为 true，主机名“accounting.xyz.com”返回“accounting”。

### 2.11.4. **使用用户管理器管理子站点**

从用户管理器管理创建新用户时，您可以指定两个字段来为该新用户启用和配置子站点行为：

· **分析规则：**选择一个分析规则以分配给具有内置子站点支持的新用户，例如本文档中使用的示例：**subsite-by-hostname**。

· **子站点：**从下拉列表中选择要分配给新用户的主子站点的子站点，或者留空以使用默认的 /\_user 主站点。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps176.jpg)

使用**subsite-by-hostname**分析规则时，请确保从 subsites 下拉列表中选择一个子站点，因为这两个属性一起工作。该规则是关于在哪里查找主页的说明，子站点选择告诉分析规则哪个子站点将保存此用户目录

子站点管理也可以委托给特定子站点的管理员。例如，您可能希望为每个子站点设置用户管理器管理页面。通过修改 j2-admin 应用程序的部署描述符，可以为每个用户管理器详细信息 portlet 配置不同的默认子站点：

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps177.jpg)

### 2.11.5. **使用用户注册管理子站点**

从用户注册 portlet 创建新用户时，您可以指定两个字段来为该新用户启用和配置子站点行为：

· **rulesValues：**选择一个分析规则以分配给具有内置子站点支持的新用户，例如本文档中使用的示例：**subsite-by-hostname**。

· **subsiteRootFolder：**一个唯一子站点根文件夹的完整路径。

![](file:///C:\Users\johnfeng\AppData\Local\Temp\ksohtml12504\wps178.jpg)

注意：用户注册 portlet 将基于每个用户存储这些首选项值。通常这意味着只为管理用户存储首选项。如果您将让管理员注册用户，那么这种方法可以正常工作。但是，对于**自助注册**门户，您需要在 portlet 的默认值中设置这些值。默认值通常在 portlet.xml 中设置，例如：

...

    <偏好>

 		<name>子站点根文件夹</name>

        <value>/__subsite-root/_hostname/localhost</value>   

    </偏好>        

    <偏好>

 		<name>规则名称</name>

        <value>页面</value>   

    </偏好>        

    <偏好>

 		<name>规则值</name>

        <value>按主机名的子站点</value>   

    </偏好>        
...

您还可以在每页 (PSML) 中间级别上设置默认值：

<fragment id="example-subsite-1" type="portlet" name="j2-admin::UserRegistrationPortlet">

<preference name="subsiteRootFolder">

<value>/__subsite-root/_hostname/localhost</value>
</偏好>

<preference name="rulesNames">

<value>页面</value>
</偏好>

<preference name="rulesValues">

<value>按主机名的子站点</value>
</偏好>      

</片段>
