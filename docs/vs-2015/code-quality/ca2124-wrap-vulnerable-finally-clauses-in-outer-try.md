---
title: 'CA2124: encapsular cláusulas finally vulneráveis na tentativa externa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660243"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: encapsular cláusulas finalmente vulneráveis em tentativa externa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Categoria|Microsoft.Security|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Nas versões 1,0 e 1,1 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], um método público ou protegido contém um `try` / `catch` / bloco de `finally`. O bloco `finally` parece redefinir o estado de segurança e não está incluído em um bloco `finally`.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra localiza `try` / blocos de `finally` no código que tem como destino as versões 1,0 e 1,1 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que podem estar vulneráveis a filtros de exceção mal-intencionada presentes na pilha de chamadas. Se operações confidenciais, como a representação ocorrerem no bloco try, e uma exceção for gerada, o filtro poderá ser executado antes do bloco `finally`. Para o exemplo de representação, isso significa que o filtro seria executado como o usuário representado. Atualmente, os filtros são implementados somente em Visual Basic.

> [!WARNING]
> Nas versões 2,0 e posteriores do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], o tempo de execução protege automaticamente um `try` / `catch` /  `finally` bloqueio de filtros de exceção mal-intencionados, se a redefinição ocorrer diretamente dentro do método que contém o bloco de exceção.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Coloque o `try` desencapsulado / `finally` em um bloco try externo. Consulte o segundo exemplo a seguir. Isso força o `finally` a ser executado antes do código de filtro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de pseudo-código

### <a name="description"></a>Descrição
 O pseudocódigo a seguir ilustra o padrão detectado por essa regra.

### <a name="code"></a>Código

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>Exemplo
 O pseudocódigo a seguir mostra o padrão que você pode usar para proteger seu código e atender a essa regra.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
