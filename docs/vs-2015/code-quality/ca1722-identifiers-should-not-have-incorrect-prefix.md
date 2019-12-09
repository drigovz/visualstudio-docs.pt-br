---
title: 'CA1722: os identificadores não devem ter um prefixo incorreto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f50c5aca934886f03a54692d98a6be3f8bb5562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671588"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: os identificadores não devem ter prefixo incorreto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Categoria|Microsoft. Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um identificador tem um prefixo incorreto.

## <a name="rule-description"></a>Descrição da Regra
 Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.

 Os nomes de tipo não têm um prefixo específico e não devem ser prefixados com um ' C'. Essa regra relata violações para nomes de tipo, como ' CMyClass ', e não relata violações para nomes de tipo, como ' cache '.

 As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova o prefixo do identificador.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1715: os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
