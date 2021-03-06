---
title: 动态重新配置
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881969"
---
# <a name="dynamic-reconfiguration"></a>动态重新配置
此示例演示 Windows Communication Foundation (WCF) 路由服务。 路由服务是一个 WCF 组件，它可以轻松地在应用程序中包含基于内容的路由器。 此示例采用标准的 WCF 计算器示例，用于使用路由服务进行通信。 此示例演示如何在运行时动态重新配置路由服务。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>示例详细信息  
 为在运行时动态重新配置路由服务，此示例每五秒触发一次计时器以创建新的 <xref:System.ServiceModel.Routing.RoutingConfiguration> 对象并应用该对象。 此配置引用常规计算器终结点或舍入计算器终结点。 计算器客户端应用程序的消息从其中一个服务返回，具体取决于路由服务当时配置为路由到哪个服务。  
  
 会使用路由服务通过自定义行为动态重新配置的功能。 此自定义行为附加一个服务扩展，该扩展包含的简单线程计时器每五秒触发一次，从而形成对 `UpdateRules` 方法的一次回调。 此回调创建并应用新的路由配置。 在实际部署中，此回调可能会作为某些其他类型事件（如 SQL-Event 通知或 WS-Discovery 公告）的结果实现。  
  
#### <a name="to-use-this-sample"></a>使用此示例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 打开 DynamicReconfiguration.sln。  
  
2.  若要打开**解决方案资源管理器**，选择**解决方案资源管理器**从**视图**菜单。  
  
3.  按**F5**或**CTRL + SHIFT + B** Visual Studio 中。  
  
    1.  如果你想要自动启动所需的项目时，按**F5**，右键单击解决方案并选择**属性**。 选择**启动项目**节点下的**通用属性**的左窗格中。 选择**多个启动项目**单选按钮并设置的所有项目具有**启动**操作。  
  
    2.  如果生成该项目**CTRL + SHIFT + B**，则必须启动以下应用程序：  
  
        1.  计算器客户端 (./CalculatorClient/bin/client.exe)  
  
        2.  计算器服务 (./CalculatorService/bin/service.exe)  
  
        3.  路由计算器服务 (./RoundingCalcService/bin/service.exe)  
  
        4.  路由服务 (./RoutingService/bin/RoutingService.exe)  
  
4.  在计算器客户端的控制台窗口中，按 Enter 启动客户端并调用计算器服务操作。  
  
     随着路由配置每五秒动态更改一次，路由服务将消息交替路由到舍入计算器和常规计算器。 根据路由服务器配置为将消息发送到哪个终结点，客户端控制台窗口中会显示不同的输出。  
  
5.  继续反复按 Enter 超过五秒，观察服务结果的更改。  
  
    1.  下面是路由器服务配置为将消息路由到舍入计算器服务时返回的输出。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  下面是路由服务配置为将消息路由到常规计算器服务时返回的输出。  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  计算器服务和舍入计算器服务也会向其各自的控制台窗口输出调用的操作的日志。  
  
7.  在客户端控制台窗口中，键入"quit"并按 ENTER 退出。  
  
8.  在服务控制台窗口中按 ENTER 终止服务。  
  
## <a name="scenario"></a>方案  
 此示例演示的路由器充当基于内容的路由器，从而可以通过一个终结点公开多种服务类型或实现。  
  
### <a name="real-world-scenario"></a>实际方案  
 Contoso 希望虚拟化其所有服务以仅公开一个终结点，这些服务通过该终结点可提供对多种不同类型的服务的访问。 在这种情况下，这些服务利用路由服务的基于内容的路由功能，以确定应将传入请求发送到哪个位置。  
  
## <a name="see-also"></a>请参阅  
 [AppFabric 承载和持久性示例](https://go.microsoft.com/fwlink/?LinkId=193961)
