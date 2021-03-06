---
title: '#Const 指令 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 58d786c5e16b1e667f7c7c78b0f7857cd9711239
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541609"
---
# <a name="const-directive"></a>#Const 指令
对于 Visual Basic 中定义条件编译器常量。  
  
## <a name="syntax"></a>语法  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>部件  
 `constname`  
 必须的。 正在定义的常量的名称。  
  
 `expression`  
 必须的。 文本、 其他条件编译器常量或包括除之外的任何或所有算术或逻辑运算符的任意组合`Is`。  
  
## <a name="remarks"></a>备注  
 条件编译器常量始终是专用于其显示的文件。 无法创建使用公共编译器常量`#Const`指令; 仅在用户界面或使用可以创建它们`/define`编译器选项。  
  
 可以使用只有条件编译器常量和中的文本`expression`。 使用与定义的标准常量`Const`将导致错误。 相反，可以使用定义的常数`#Const`关键字用于条件编译。 常量还定义，在这种情况下它们具有值为`Nothing`。  
  
## <a name="example"></a>示例  
 此示例使用 `#Const` 指令。  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>请参阅  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)  
 [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
