---
title: 'CA2103: examinar a segurança imperativa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b4abf0b15a4fbba1abc61572da8a2f6126c754f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652154"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: revisar segurança obrigatória
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ReviewImperativeSecurity|
|CheckId|CA2103|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método usa segurança obrigatória e pode construir a permissão usando as informações de estado ou os valores de retorno que podem ser alterados desde que a demanda esteja ativa.

## <a name="rule-description"></a>Descrição da Regra
 A segurança imperativa usa objetos gerenciados para especificar permissões e ações de segurança durante a execução do código, em comparação com a segurança declarativa, que usa atributos para armazenar permissões e ações em metadados. A segurança imperativa é muito flexível porque você pode definir o estado de um objeto de permissão e selecionar ações de segurança usando informações que não estão disponíveis até o tempo de execução. Junto com essa flexibilidade vem o risco de que as informações de tempo de execução usadas para determinar o estado de uma permissão não permaneçam inalteradas, desde que a ação esteja em vigor.

 Use a segurança declarativa sempre que possível. As demandas declarativas são mais fáceis de entender.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Examine as demandas de segurança imperativas para garantir que o estado da permissão não dependa de informações que podem ser alteradas desde que a permissão esteja sendo usada.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se a permissão não depender da alteração de dados. No entanto, é melhor alterar a demanda imperativa para seu equivalente declarativo.

## <a name="see-also"></a>Consulte também
 [Dados e modelagem de diretrizes de](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [codificação segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
