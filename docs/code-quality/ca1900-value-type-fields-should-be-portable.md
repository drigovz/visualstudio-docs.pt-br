---
title: 'CA1900: Campos de tipo de valor devem ser portáteis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84861aa1d17f041061d1666d6f78c9d273b948b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037766"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Campos de tipo de valor devem ser portáteis

|||
|-|-|
|NomeDoTipo|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Categoria|Microsoft.Portability|
|Alteração Significativa|Quebrando - se o campo pode ser visto de fora do assembly.<br /><br /> Sem quebra - se o campo não está visível fora do assembly.|

## <a name="cause"></a>Causa
 Esta regra verifica que estruturas que são declaradas com layout explícito serão corretamente alinhados quando passa por marshaling para código não gerenciado em sistemas operacionais de 64 bits. IA-64 não permite que os acessos à memória desalinhada e o processo falhará se essa violação não for corrigida.

## <a name="rule-description"></a>Descrição da regra
 Estruturas com layout explícito contendo campos desalinhados podem causar quedas em sistemas operacionais de 64 bits.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Todos os campos que são menores do que 8 bytes devem ter os deslocamentos são um múltiplo de seu tamanho e os campos que são 8 bytes ou mais devem ter os deslocamentos são um múltiplo de 8. Outra solução é usar `LayoutKind.Sequential` em vez de `LayoutKind.Explicit`, se razoável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Esse aviso deve ser suprimido somente se ele ocorrer no erro.