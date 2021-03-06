---
title: 编写实体框架数据提供程序
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 50c0555d84c5b5f180c8c49a8419e8a414a4befe
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863396"
---
# <a name="writing-an-entity-framework-data-provider"></a>编写实体框架数据提供程序
本部分讨论如何编写[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]提供程序以支持 SQL Server 以外的数据源。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]包括支持 SQL Server 的提供程序。  
  
## <a name="introducing-the-entity-framework-provider-model"></a>实体框架提供程序模型简介  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]是独立于数据库的，您可以使用 ADO.NET 提供程序模型编写提供程序以连接到不同的数据源集。  
  
 实体框架数据提供程序（通过使用 ADO.NET 数据提供程序模型构建）具有下列功能：  
  
-   将实体数据模型 (EDM) 基元类型映射到提供程序类型。  
  
-   公开提供程序特定的函数。  
  
-   为给定 DbQueryCommandTree 生成提供程序特定的命令以支持[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]查询。  
  
-   为给定 DbModificationCommandTree 生成提供程序特定的更新命令以支持[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]中的更新。  
  
-   公开存储架构定义的映射文件以支持基于数据库的模型生成。  
  
-   通过概念模型公开元数据（例如，表和视图）。  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>示例  
 请参阅[实体框架示例提供程序](https://go.microsoft.com/fwlink/?LinkId=180616)有关的示例[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支持 SQL Server 以外的数据源的提供程序。  
  
## <a name="in-this-section"></a>本节内容  
 [SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [修改 SQL 生成](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [提供程序清单规范](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>请参阅  
 [使用数据提供程序](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
