---
title: 'Como: Especificar informações de código adicionais usando analysis_assume | Microsoft Docs'
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e130f2248ae6715b3248226c780bc162e1ff01ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426636"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Como: Especificar informações de código adicionais usando _analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode fornecer dicas para a ferramenta de análise de código para código C/C++ que ajudam no processo de análise e reduzir os avisos. Para fornecer informações adicionais, use a função a seguir:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -qualquer expressão supostamente avaliada como true.  
  
 A ferramenta de análise de código pressupõe que a condição representada pela expressão é verdadeira no ponto em que a função aparece e permanece verdadeira até que a expressão for alterada, por exemplo, por atribuição a uma variável.  
  
> [!NOTE]
> `__analysis_assume` não afeta a otimização de código. Fora a ferramenta de análise de código, `__analysis_assume` é definido como inoperante.  
  
## <a name="example"></a>Exemplo  
 O seguinte código usa `__analysis_assume` para corrigir o aviso de análise de código [C6388](../code-quality/c6388.md):  
  
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
  
## <a name="see-also"></a>Consulte também  
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
