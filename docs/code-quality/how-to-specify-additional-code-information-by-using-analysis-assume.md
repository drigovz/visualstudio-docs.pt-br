---
title: 'Como: Especificar informações de código adicionais usando _Analysis_assume'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: badc2159085257f25a224a29cf1163b2b702fe60
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913594"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Como: Especificar informações de código adicionais usando _Analysis_assume
Você pode fornecer dicas para a ferramenta de análise de código para código C/C++ que ajudam no processo de análise e reduzir os avisos. Para fornecer informações adicionais, use a função a seguir:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -qualquer expressão supostamente avaliada como true.

 A ferramenta de análise de código pressupõe que a condição representada pela expressão é verdadeira no ponto em que a função aparece e permanece verdadeira até que a expressão for alterada, por exemplo, por atribuição a uma variável.

> [!NOTE]
>  `_Analysis_assume` não afeta a otimização de código. Fora a ferramenta de análise de código, `_Analysis_assume` é definido como inoperante.

## <a name="example"></a>Exemplo
 O seguinte código usa `_Analysis_assume` para corrigir o aviso de análise de código [C6388](../code-quality/c6388.md):

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
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Consulte também
 [__assume](/cpp/intrinsics/assume)