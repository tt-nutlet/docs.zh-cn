---
title: 如何：承载和运行基本的 Windows Communication Foundation 服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741154"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>如何：承载和运行基本的 Windows Communication Foundation 服务
这是创建 Windows Communication Foundation (WCF) 应用程序所需六项任务中的第三项。 有关全部六项任务的概述，请参阅[入门教程](../../../docs/framework/wcf/getting-started-tutorial.md)主题。  
  
 本主题说明如何在控制台应用程序中承载 Windows Communication Foundation (WCF) 服务。 此过程包含以下步骤：  
  
-   创建用于承载服务的控制台应用程序项目。  
  
-   为服务创建服务主机。  
  
-   启用元数据交换。  
  
-   打开服务主机。  
  
 在过程后面的以下示例中提供了在此任务中编写的代码的完整清单。  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>新建用于承载服务的控制台应用程序  
  
1.  创建新的控制台应用程序项目，方法是：右键单击“入门”解决方案，然后选择“添加”>“新建项目”。 在“添加新项目”对话框左侧的“C#”或“VB”下选择“Windows”。 在对话框的中心部分选择“控制台应用程序”。 将项目命名为 GettingStartedHost。  
  
2.  在解决方案资源管理器中右键单击“GettingStartedHost”并选择“属性”，将 GettingStartedHost 项目的目标框架设置为 .NET Framework 4.5。 在标记为“目标框架”的下拉框中，选择“.NET Framework 4.5”。 设置 VB 项目的目标框架稍有不同，在 GettingStartedHost 项目属性对话框中，单击屏幕左侧的“编译”选项卡，然后单击对话框左下角的“高级编译选项”按钮。 然后，在标记为“目标框架”的下拉框中选择“.NET Framework 4.5”。  
  
     设置目标框架将导致 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 重新加载解决方案，出现提示后按“确定”。  
  
3.  在解决方案资源管理器中右键单击 GettingStartedHost 项目下的“引用”文件夹，并选择“添加引用”，在 GettingStartedHost 项目中添加一个对 GettingStartedLib 项目的引用。 在“添加引用”对话框中，选择对话框左侧的“解决方案”，并选择对话框中心的 GettingStartedLib，然后单击“添加”。 这使 GettingStartedLib 项目中定义的类型可用于 GettingStartedHost 项目。  
  
4.  在解决方案资源管理器中右键单击 GettingStartedHost 项目下的“引用”文件夹，并选择“添加”引用，在 GettingStartedHost 项目中添加一个对 System.ServiceModel 的引用。 在“添加引用”对话框中，选择对话框左侧的“框架”。 请在“搜索程序集”文本框中，键入 `System.ServiceModel`。 在对话框的中心部分，选择“System.ServiceModel”，单击“添加”按钮，然后单击“关闭”按钮。 单击主菜单下的“全部保存”按钮，保存解决方案。  
  
### <a name="to-host-the-service"></a>承载服务  
  
-   打开 Program.cs 或 Module.vb 文件，并输入以下代码：  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close();  
                }  
                catch (CommunicationException ce)  
                {  
                    Console.WriteLine("An exception occurred: {0}", ce.Message);  
                    selfHost.Abort();  
                }  
            }  
        }  
    }  
    ```  
  
    ```vb
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
    ```  
  
    1.  第 1 步 - 创建 Uri 类的实例来保存服务的基址。 服务由包含一个基址和一个可选 URI 的 URL 来标识。 基址的格式如下：[传输协议]://[计算机名或域][:可选端口号]/[可选 URI 段]。计算器服务的基址使用 HTTP 传输协议、本地主机、端口 8000 和 URI 段“GettingStarted”  
  
    2.  第 2 步 – 创建 <xref:System.ServiceModel.ServiceHost> 类的实例以承载服务。 构造函数采用两个参数：实现服务协定的类的类型，以及服务的基址。  
  
    3.  第 3 步 – 创建 <xref:System.ServiceModel.Description.ServiceEndpoint> 实例。 服务终结点由地址、绑定和服务协定组成。 因此<xref:System.ServiceModel.Description.ServiceEndpoint> 构造函数采用服务协定接口类型、绑定和地址。 服务协定是在服务类型中定义和实现的 `ICalculator`。 在此示例中使用的绑定是 <xref:System.ServiceModel.WSHttpBinding>，这是用于连接到符合 WS-＊ 规范的终结点的内置绑定。 有关 WCF 绑定的详细信息，请参阅 [WCF 绑定概述](../../../docs/framework/wcf/bindings-overview.md)。 该地址追加到基址以标识终结点。 在此代码中指定的地址为"CalculatorService"，因此终结点的完全限定的地址是`"http://localhost:8000/GettingStarted/CalculatorService"`。  
  
        > [!IMPORTANT]
        >  使用 .NET Framework 4 或更高版本时，添加服务终结点是可选的。 在这些版本中，如果在代码或配置中未添加任何终结点，则 WCF 为该服务实现的基址和协定的每个组合添加一个默认终结点。 有关默认终结点的详细信息，请参阅[指定终结点地址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)。 有关默认终结点、绑定和行为的详细信息，请参阅[简化配置](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服务的简化配置](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
    4.  第 4 步 - 启用元数据交换。 客户端将使用元数据交换来生成将用于调用服务操作的代理。 要启用元数据交换，请创建 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 实例，将其 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 属性设置为 `true`，并将行为添加到 <xref:System.ServiceModel.ServiceHost> 实例的 <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` 集合。  
  
    5.  第 5 步 – 打开 <xref:System.ServiceModel.ServiceHost>，以侦听传入消息。 注意，代码会等待用户按 Enter。 如果不这样做，应用程序将立即关闭，并且服务将关闭。另请注意，使用了 try/catch 块。 在实例化 <xref:System.ServiceModel.ServiceHost> 后，所有其他代码放置在 try/catch 块中。 有关 <xref:System.ServiceModel.ServiceHost> 引发的安全捕获异常的详细信息，请参阅[避免出现与 Using 语句有关的问题](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
> [!IMPORTANT]
> 编辑 App.config 中 GettingStartedLib 以反映在代码中所做的更改： 
> 1. 更改第 14 行 `<service name="GettingStartedLib.CalculatorService">`
> 2. 更改到的第 17 行 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. 更改到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`
        
### <a name="to-verify-the-service-is-working"></a>验证服务是否正常运行  
  
1.  从 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 内部运行 GettingStartedHost 控制台应用程序。 在 [!INCLUDE[wv](../../../includes/wv-md.md)] 以及更高版本的操作系统上运行时，必须使用管理员特权运行该服务。 由于 Visual Studio 是使用管理员特权运行的，因此 GettingStartedHost 也是使用管理员特权运行的。 也可以启动新的命令提示，使用管理员特权运行它，并在其中运行 service.exe。  
  
2.  打开 Internet Explorer，并浏览到服务的调试页，网址为 `http://localhost:8000/GettingStarted/CalculatorService`。  
  
## <a name="example"></a>示例  
 下面的示例包括本教程中前面步骤的服务协定和实现，并将服务承载于控制台应用程序中。  
  
 要使用命令行编译器对此进行编译，请将 IService1.cs 和 Service1.cs 编译到引用 `System.ServiceModel.dll` 的类库中。 并将 Program.cs 编译到控制台应用程序。  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
        public interface ICalculator  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                selfHost.Close();  
            }  
            catch (CommunicationException ce)  
            {  
                Console.WriteLine("An exception occurred: {0}", ce.Message);  
                selfHost.Abort();  
            }  
        }  
    }  
}  
```  
  
```vb
'IService1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
'Service1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
```vb
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
```  
  
> [!NOTE]
>  此类服务需要在计算机上注册 HTTP 地址以进行侦听的权限。 管理员帐户具有此权限，但对于非管理员帐户来说，必须授予对 HTTP 命名空间的权限。 有关如何配置命名空间预留的详细信息，请参阅[配置 HTTP 和 HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。 在 Visual Studio 下运行时，必须使用管理员特权运行 service.exe。  
  
 此时服务正在运行。 转到[如何：创建客户端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。 有关疑难解答的信息，请参阅[疑难解答入门教程](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)。  
  
## <a name="see-also"></a>请参阅  
 [入门](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自承载](../../../docs/framework/wcf/samples/self-host.md)
