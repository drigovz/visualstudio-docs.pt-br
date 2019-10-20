---
title: 'CA1707: os identificadores não devem conter sublinhados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 526f0333cc4a233996c00576e3439bac4593c29f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669210"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: os identificadores não devem conter sublinhados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre o Visual Studio, consulte [CA1707: identificadores não devem conter sublinhados](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Categoria|Microsoft. Naming|
|Alteração Significativa|Quebra-quando elevado em assemblies<br /><br /> Não separável-quando elevado em parâmetros de tipo|

## <a name="cause"></a>Causa
 O nome de um identificador contém o caractere de sublinhado (_).

## <a name="rule-description"></a>Descrição da Regra
 Por convenção, os nomes de identificador não contêm o caractere de sublinhado (_). A regra verifica namespaces, tipos, membros e parâmetros.

 As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova todos os caracteres de sublinhado do nome.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
