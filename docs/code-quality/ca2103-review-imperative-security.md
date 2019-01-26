---
title: 'CA2103: Examinar a segurança imperativa'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ae092017890552613bfddb16cf0c7313cf422e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967239"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Examinar a segurança imperativa

|||
|-|-|
|NomeDoTipo|ReviewImperativeSecurity|
|CheckId|CA2103|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método usa segurança obrigatória e pode construir a permissão usando as informações de estado ou os valores de retorno que podem ser alterados desde que a demanda esteja ativa.

## <a name="rule-description"></a>Descrição da regra
 Segurança imperativa usa objetos gerenciados para especificar as permissões e as ações de segurança durante a execução de código, em comparação comparada a segurança declarativa, que usa atributos para armazenar as permissões e as ações nos metadados. Segurança obrigatória é muito flexível, pois você pode definir o estado de um objeto de permissão e selecione as ações de segurança usando as informações que não estão disponíveis até que o tempo de execução. Junto com que a flexibilidade vem o risco de que as informações de tempo de execução que você usa para determinar que o estado de uma permissão não permanece inalteradas desde que a ação está em vigor.

 Use a segurança declarativa sempre que possível. As solicitações declarativas são mais fáceis de entender.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Examine as demandas de segurança obrigatória para certificar-se de que o estado da permissão não se baseia nas informações que podem ser alterados desde que a permissão está sendo usada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É seguro suprimir um aviso nessa regra, se a permissão não se baseia na alteração de dados. No entanto, é melhor alterar a demanda imperativa para seu equivalente declarativo.

## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)
- [Dados e modelagem](/dotnet/framework/data/index)