---
title: Solucionando problemas de análise do código
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936428b82e721a1df6003a4bb0eecefe5b696b4c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079986"
---
# <a name="troubleshooting-code-analysis-issues"></a>Solucionando problemas de análise do código
Este tópico contém informações de solução de problemas para os seguintes problemas de análise de código do Visual Studio.

- [Alterações em uma Regra do Visual Studio 2010 Não Afetarão as Versões Anteriores do Visual Studio](#ChildRuleSetChangesInPreviousVersions)

## <a name="ChildRuleSetChangesInPreviousVersions"></a> Alterações em uma Regra do Visual Studio 2010 Não Afetarão as Versões Anteriores do Visual Studio
 Ao criar um conjunto de regras no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] que contém um conjunto de regras filho, uma alteração no conjunto de regras filho pode não ser aplicada em execuções de análise de código em computadores que usam uma versão anterior do Visual Studio. Para resolver esse problema, é necessário forçar uma reescrita de conjunto de regras pai, que é o conjunto de regras que contém o conjunto de regras filho.

1. Abra o conjunto de regras pai no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].

2. Faça uma alteração, como adicionar ou remover uma regra e salve o conjunto de regras.

3. Abra o conjunto de regras, reverta a alteração e, em seguida, salve o conjunto de regras novamente.

## <a name="see-also"></a>Consulte também

- [Analisando a qualidade do aplicativo](../code-quality/code-analysis-for-managed-code-overview.md)
- [Analisando a qualidade do código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)
- [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)