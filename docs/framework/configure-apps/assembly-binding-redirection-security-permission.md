---
title: 程序集绑定重定向安全权限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b9b9ac5c4e8ce08b9f926b0cdf7149dbdd9ac2da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501428"
---
# <a name="assembly-binding-redirection-security-permission"></a>程序集绑定重定向安全权限
应用程序配置文件中的显式程序集绑定重定向需要安全权限。 这适用于对 .NET Framework 程序集和来自第三方的程序集的重定向。 通过设置授予权限<xref:System.Security.Permissions.SecurityPermissionFlag>标志<xref:System.Security.Permissions.SecurityPermission>。 托管程序集默认情况下没有任何权限。  
  
 安全权限授予受信任的区域 （本地计算机） 和 Intranet 区域中运行的应用程序。 在 Internet 区域中运行的应用程序严格禁止执行程序集绑定重定向。  
  
 如果在发布服务器策略文件控制的组件发布服务器，或由管理员控制计算机配置文件中执行程序集重定向，则不需要该权限。 但是，该权限是以显式忽略发行者策略使用的应用需要[ \<apply ="no"/ >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)应用程序配置文件中的元素。  
  
 下表显示的默认安全设置**BindingRedirects**标志。  
  
|区域|BindingRedirects 标志设置|  
|----------|-----------------------------------|  
|受信任的区域 （本地计算机）|**ON**|  
|Intranet 区域|**ON**|  
|Internet 区域|**关闭**|  
|不受信任的区域|**关闭**|  
  
 管理员可以更改这些安全设置，以支持或限制给定计算机上的特定方案。 有工具可用于更改**BindingRedirects**标志设置从默认设置; 管理员必须手动编辑用户的计算机上的 Security.config 文件。  
  
## <a name="see-also"></a>请参阅  
 [发布服务器策略文件和通过并行执行](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [如何：启用和禁用自动绑定重定向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [并行执行](../../../docs/framework/deployment/side-by-side-execution.md)
