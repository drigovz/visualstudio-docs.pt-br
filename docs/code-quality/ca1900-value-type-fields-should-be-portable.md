---
title: 'CA1900: Campos de tipo de valor devem ser portáteis'
ms.date: 11/04/2016
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
ms.openlocfilehash: f734d0cf28a5aec28ebbf635dd384efe176b1774
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921314"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Campos de tipo de valor devem ser portáteis

|||
|-|-|
|NomeDoTipo|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Categoria|Microsoft.Portability|
|Alteração Significativa|Quebra-se o campo pode ser visto fora do assembly.<br /><br /> Não separável – se o campo não estiver visível fora do assembly.|

## <a name="cause"></a>Causa
Essa regra verifica se as estruturas declaradas com layout explícito serão alinhadas corretamente quando marshaled para código não gerenciado em sistemas operacionais de 64 bits. IA-64 não permite acessos de memória não alinhados e o processo falhará se essa violação não for corrigida.

## <a name="rule-description"></a>Descrição da regra
Estruturas com layout explícito que contém campos desalinhados causam falhas em sistemas operacionais de 64 bits.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Todos os campos menores que 8 bytes devem ter deslocamentos que são múltiplos de seu tamanho e os campos que têm 8 bytes ou mais devem ter deslocamentos que sejam múltiplos de 8. Outra solução é usar `LayoutKind.Sequential` em vez de `LayoutKind.Explicit`, se for razoável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Esse aviso deve ser suprimido somente se ocorrer um erro.