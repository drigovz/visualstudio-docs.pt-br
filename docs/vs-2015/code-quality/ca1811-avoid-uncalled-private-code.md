---
title: 'CA1811: Evitar código privado não chamado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0f7272178edd1113d01644de9a5224e24907b31
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925485"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitar código particular não chamado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Membro privado ou interno (nível de assembly) não tem chamadores no assembly, não é invocado pelo common language runtime e não é invocado por um delegado. Os seguintes membros não são verificados por essa regra:

-   Membros de interface explícita.

-   Construtores estáticos.

-   Construtores de serialização.

-   Métodos marcados com <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Membros que são substituições.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra pode relatar falsos positivos se houver pontos de entrada que não são identificados no momento pela lógica de regra. Além disso, um compilador pode emitir código noncallable em um assembly.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o código noncallable ou adicionar código que o chama.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1812: Evite classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)
