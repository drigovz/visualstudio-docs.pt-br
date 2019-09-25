---
title: 'CA2103: Examinar a segurança imperativa'
ms.date: 11/04/2016
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
ms.openlocfilehash: a2792f1cccad26fe5bb073af800a2fcf0ebcb4b4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232978"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Examinar a segurança imperativa

|||
|-|-|
|NomeDoTipo|ReviewImperativeSecurity|
|CheckId|CA2103|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um método usa segurança obrigatória e pode construir a permissão usando as informações de estado ou os valores de retorno que podem ser alterados desde que a demanda esteja ativa.

## <a name="rule-description"></a>Descrição da regra
A segurança imperativa usa objetos gerenciados para especificar permissões e ações de segurança durante a execução do código, em comparação com a segurança declarativa, que usa atributos para armazenar permissões e ações em metadados. A segurança imperativa é muito flexível porque você pode definir o estado de um objeto de permissão e selecionar ações de segurança usando informações que não estão disponíveis até o tempo de execução. Junto com essa flexibilidade vem o risco de que as informações de tempo de execução usadas para determinar o estado de uma permissão não permaneçam inalteradas, desde que a ação esteja em vigor.

Use a segurança declarativa sempre que possível. As demandas declarativas são mais fáceis de entender.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Examine as demandas de segurança imperativas para garantir que o estado da permissão não dependa de informações que podem ser alteradas desde que a permissão esteja sendo usada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se a permissão não depender da alteração de dados. No entanto, é melhor alterar a demanda imperativa para seu equivalente declarativo.

## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)
- [Dados e modelagem](/dotnet/framework/data/index)