---
title: 'CA2106: Declarações seguras'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8d80c4e9a21c29ce7b34a3998e241b11713f355
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545694"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Declarações seguras

|||
|-|-|
|NomeDoTipo|SecureAsserts|
|CheckId|CA2106|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método declara uma permissão e não executa nenhuma verificação de segurança do chamador.

## <a name="rule-description"></a>Descrição da regra
 A declaração de uma permissão de segurança sem realizar verificações de segurança pode deixar uma fraqueza de segurança explorável no código. Uma movimentação de pilha de segurança para quando uma permissão de segurança é declarada. Se você declarar uma permissão sem executar nenhuma verificação no chamador, o chamador pode executar indiretamente código por meio de suas permissões. Declara sem verificações de segurança são permitidas, se você tiver certeza, que a declaração não pode ser usada de modo prejudicial. Uma declaração é inofensiva, se o código que você chame é inofensivo, ou se os usuários não é possível passar informações arbitrárias para código que você chama.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, adicione uma exigência de segurança para o método ou seu tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Suprima um aviso nessa regra somente após uma análise atenta da segurança.

## <a name="see-also"></a>Consulte também

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)