---
title: -codepage（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 66edb32d24dd1dc543097b98ff3744f0aa0a7145
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389684"
---
# <a name="-codepage-c-compiler-options"></a>-codepage（C# 编译器选项）
如果所需页不是系统的当前默认代码页，则此选项指定编译期间要使用的代码页。  
  
## <a name="syntax"></a>语法  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>自变量  
 `id`  
 要用于编译中所有源代码文件的代码页 ID。  
  
## <a name="remarks"></a>备注  
 如果编译一个或多个并非是为使用计算机上默认代码页而创建的源代码文件，可使用 -codepage 选项指定应使用的代码页。 -codepage 适用于编译中的所有源代码文件。  
  
 如果源代码文件是使用计算机上采用的相同代码页创建的，或者如果是通过 UNICODE 或 UTF-8 创建的，则无需使用 -codepage。  
  
 有关如何查找系统上支持哪些代码页的信息，请参阅 [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo)。  
  
 此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。  
  
## <a name="see-also"></a>请参阅  

- [C# 编译器选项](../../../csharp/language-reference/compiler-options/index.md)  
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
