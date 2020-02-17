---
title: Como especificar informações de código adicionais usando __analysis_assume | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277980"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Como especificar informações de código adicionais usando __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode fornecer dicas para a ferramenta de análise de código paraC++ C/Code que ajudará o processo de análise e a reduzir os avisos. Para fornecer informações adicionais, use a seguinte função:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-qualquer expressão presumida para ser avaliada como true.  
  
 A ferramenta de análise de código pressupõe que a condição representada pela expressão seja verdadeira no ponto em que a função aparece e permaneça true até que a expressão seja alterada, por exemplo, por atribuição para uma variável.  
  
> [!NOTE]
> `__analysis_assume` não afeta a otimização do código. Fora da ferramenta de análise de código, `__analysis_assume` é definido como um não op.  
  
## <a name="example"></a>Exemplo  
 O código a seguir usa `__analysis_assume` para corrigir o aviso de análise de código [C6388](../code-quality/c6388.md):  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
