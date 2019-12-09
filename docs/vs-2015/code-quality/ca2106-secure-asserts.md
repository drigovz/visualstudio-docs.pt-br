---
title: 'CA2106: declarações seguras | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1f333478c952db74fa6a9482cdad91ce6a858301
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666008"
---
# <a name="ca2106-secure-asserts"></a>CA2106: declarações seguras
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SecureAsserts|
|CheckId|CA2106|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método declara uma permissão e nenhuma verificação de segurança é realizada no chamador.

## <a name="rule-description"></a>Descrição da Regra
 A declaração de uma permissão de segurança sem realizar verificações de segurança pode deixar uma fraqueza de segurança explorável no código. Uma movimentação de pilha de segurança para quando uma permissão de segurança é declarada. Se você declarar uma permissão sem executar nenhuma verificação no chamador, o chamador poderá executar indiretamente o código usando suas permissões. As declarações sem verificações de segurança só são permitidas quando você tem certeza de que a declaração não pode ser usada de forma prejudicial. Um Assert é inofensivo se o código que você chama é inofensivo ou os usuários não podem passar informações arbitrárias para o código que você chama.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione uma demanda de segurança ao método ou ao seu tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso desta regra somente após uma revisão de segurança cuidadosa.

## <a name="see-also"></a>Consulte também
 [diretrizes de codificação segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
