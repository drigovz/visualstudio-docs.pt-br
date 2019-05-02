---
title: 'CA2124: Encapsulamento vulnerável, por fim, cláusulas em tentativa externa | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 755cce18afcad3fde621fb5a960cc780906afe51
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385992"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Encapsular cláusulas finally vulneráveis em try externo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Nas versões 1.0 e 1.1 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], um método público ou protegido contém um `try` / `catch` / `finally` bloco. O `finally` bloco aparece para redefinir o estado de segurança e não é colocado um `finally` bloco.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra localiza `try` / `finally` bloqueia no código que tem como alvo as versões 1.0 e 1.1 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que podem ser vulneráveis a filtros de exceção mal-intencionados presentes na pilha de chamadas. Se operações confidenciais como representação ocorrerem no bloco try, e uma exceção é lançada, o filtro pode ser executado antes de `finally` bloco. No exemplo de representação, isso significa que o filtro seria executado como o usuário representado. Os filtros são implementável atualmente apenas no Visual Basic.

> [!WARNING]
> **Observação** nas versões 2.0 e posteriores do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], o tempo de execução protege automaticamente um `try` / `catch` /  `finally` bloquear de filtros de exceção mal-intencionados, se ocorrer a redefinição diretamente dentro do método que contém o bloco de exceção.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Coloque o desencapsulamento `try` / `finally` em um bloco try externo. Consulte o segundo exemplo que segue. Isso força o `finally` seja executado antes do código de filtro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de pseudocódigo

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
