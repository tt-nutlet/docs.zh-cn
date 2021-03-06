---
title: 构造函数设计
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ad920c8028b102a13fdfe928d21768538e25b0f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868149"
---
# <a name="constructor-design"></a>构造函数设计
有两种类型的构造函数： 键入构造函数和实例构造函数。  
  
 类型构造函数是静态的之前使用的类型, 的 CLR 运行。 实例构造函数运行时创建一种类型的实例。  
  
 类型构造函数不能采用任何参数。 实例构造函数可以。 不接受任何参数的实例构造函数通常称为默认构造函数。  
  
 构造函数是最普遍的方法来创建一种类型的实例。 大多数开发人员将搜索并尝试使用的构造函数之前它们，请考虑创建实例 （例如工厂方法） 的替代方法。  
  
 **✓ CONSIDER** 提供简单，理想情况下是默认值，构造函数。  
  
 简单的构造函数具有极少数的参数，并且所有参数都是基元或枚举。 此类简单的构造函数提高可用性的 framework。  
  
 **✓ CONSIDER** 而不一个构造函数中使用的静态工厂方法，如果所需的操作的语义执行不直接映射到的新实例的构造，或遵循的构造函数设计准则是不合理。  
  
 **✓ DO** 设置主属性构造函数参数用作快捷方式。  
  
 应在语义之间没有区别使用跟某些属性集的空构造函数和使用具有多个参数的构造函数。  
  
 **✓ DO** 使用相同的名称用于构造函数参数和属性，如果使用构造函数参数只需设置属性。  
  
 此类参数和属性之间的唯一区别应大小写不同。  
  
 **✓ DO** 构造函数中的最小工作。  
  
 构造函数不应执行大量的工作以外捕获构造函数参数。 需要时才应延迟的任何其他处理成本。  
  
 **✓ DO** 根据引发从实例构造函数的异常。  
  
 **✓ DO** 显式声明在类中，公共默认构造函数，如果这样的构造函数是必需的。  
  
 如果不显式类型上声明任何构造函数，许多语言 （如 C# 中) 将自动添加公共默认构造函数。 （抽象类获取受保护的构造函数。）  
  
 将参数化构造函数添加到类可阻止编译器添加默认构造函数。 这通常会导致意外的重大更改。  
  
 **X AVOID** 显式在结构上定义默认的构造函数。  
  
 这使得数组创建速度更快，因为如果未定义的默认构造函数，它无需在数组中每个插槽上运行。 请注意，许多编译器，包括 C# 中，不允许结构出于此原因具有无参数构造函数。  
  
 **X AVOID** 调用其构造函数内的对象上的虚拟成员。  
  
 调用虚拟成员将导致派生程度最高的替代，以便进行调用，即使派生程度最高的类型的构造函数已完全尚未运行。  
  
### <a name="type-constructor-guidelines"></a>类型构造函数准则  
 **✓ DO** 将设为私有静态构造函数。  
  
 静态构造函数，也称为类构造函数，用于初始化的类型。 创建类型的第一个实例或调用该类型上的任何静态成员之前，CLR 将调用静态构造函数。 用户可以调用静态构造函数时没有控制。 如果静态构造函数不是私有的它可以由非 CLR 代码调用。 根据在构造函数中执行的操作，这可能导致意外的行为。 C# 编译器会强制为私有的静态构造函数。  
  
 **X DO NOT** 从静态构造函数引发异常。  
  
 从类型构造函数引发异常，如果类型不是可使用当前的应用程序域中。  
  
 **✓ CONSIDER** 初始化以内的静态字段，而不用显式静态构造函数，由于运行时能够优化没有显式定义的静态构造函数的类型的性能。  
  
 *部分版权 © 2005, 2009 Microsoft Corporation。保留所有权利。*  
  
 *经 Pearson Education, Inc 授权，转载自[框架设计准则：可重用的 .NET 库的约定、习惯用语和模式，第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 作者：Krzysztof Cwalina 和 Brad Abrams，由 Addison Wesley Professional 于 2008 年 10 月 22 日印发，作为 Microsoft Windows 开发系列的一部分。*  
  
## <a name="see-also"></a>请参阅

- [成员设计准则](../../../docs/standard/design-guidelines/member.md)  
- [框架设计指南](../../../docs/standard/design-guidelines/index.md)
