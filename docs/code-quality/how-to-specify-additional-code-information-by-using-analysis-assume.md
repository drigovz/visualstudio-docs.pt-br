---
title: Usar _Analysis_assume para dicas de análise de código
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 186ea6ac58736098720d60c644c30801073b7453
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018725"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Como: Especificar informações de código adicionais usando _Analysis_assume

Você pode fornecer dicas para a ferramenta de análise de código paraC++ C/Code que ajudará o processo de análise e a reduzir os avisos. Para fornecer informações adicionais, use a seguinte função:

`_Analysis_assume(`  `expr`  `)`

`expr`-qualquer expressão presumida para avaliar como true.

A ferramenta de análise de código pressupõe que a condição representada pela expressão seja verdadeira no ponto em que a função aparece e permaneça true até que a expressão seja alterada, por exemplo, por atribuição para uma variável.

> [!NOTE]
> `_Analysis_assume` não afeta a otimização do código. Fora da ferramenta de análise de código, `_Analysis_assume` é definido como um não op.

## <a name="example"></a>Exemplo

O código a seguir usa `_Analysis_assume` para corrigir o aviso de análise de código [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    __analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Consulte também

- [__assume](/cpp/intrinsics/assume)
