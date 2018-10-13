---
title: 'CA1722: Os identificadores não devem ter prefixo incorreto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 305e0f251ee64165a9a25481aa6c45299d888b33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215586"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: os identificadores não devem ter prefixo incorreto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um identificador tem um prefixo incorreto.

## <a name="rule-description"></a>Descrição da Regra
 Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.

 Nomes de tipo não têm um prefixo específico e não devem ser prefixados com um 'c'. Esta regra relata violações para nomes de tipo como 'CMyClass' e não relata violações para nomes de tipo como 'Cache'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova o prefixo do identificador.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1715: os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)



