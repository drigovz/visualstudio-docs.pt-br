---
title: 'CA2124: Encapsular cláusulas finally vulneráveis em try externo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008767f7d37e2c088dad58a328b025f81090ad8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232446"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Encapsular cláusulas finally vulneráveis em try externo

|||
|-|-|
|NomeDoTipo|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Categoria|Microsoft.Security|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Nas versões 1,0 e 1,1 do .NET Framework, um método público ou protegido `try` contém um / `catch` / `finally` bloco. O `finally` bloco é exibido para redefinir o estado de segurança e não está `finally` incluído em um bloco.

## <a name="rule-description"></a>Descrição da regra
Essa regra localiza `try` / blocos no código que têm como destino as versões 1,0 e 1,1 do .NET Framework que podem estar vulneráveis a filtros de exceção mal-intencionada presentes na pilha de chamadas. `finally` Se operações confidenciais, como a representação ocorrerem no bloco try, e uma exceção for lançada, o filtro poderá ser executado `finally` antes do bloco. Para o exemplo de representação, isso significa que o filtro seria executado como o usuário representado. Atualmente, os filtros são implementados somente em Visual Basic.

> [!NOTE]
> Nas versões 2,0 e posteriores do .NET Framework, o tempo de execução protege `try` automaticamente um /  / `catch` `finally` bloco de filtros de exceção mal-intencionada, se a redefinição ocorrer diretamente dentro do método que contém o bloco de exceção.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Coloque o desencapsulado `try` / `finally` em um bloco try externo. Consulte o segundo exemplo a seguir. Isso força o `finally` a executar antes do código de filtro.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de pseudo-código

### <a name="description"></a>Descrição

O pseudocódigo a seguir ilustra o padrão detectado por essa regra.

```csharp
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

O pseudocódigo a seguir mostra o padrão que você pode usar para proteger seu código e atender a essa regra.

```csharp
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