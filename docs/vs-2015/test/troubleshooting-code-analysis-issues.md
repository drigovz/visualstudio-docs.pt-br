---
title: Solução de problemas de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4816783edabbd93fbb536c94f2638fcb4f8d6bb3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043049"
---
# <a name="troubleshooting-code-analysis-issues"></a>Solucionando problemas de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico contém informações de solução de problemas para os seguintes problemas de análise de código do Visual Studio.  
  
- [Alterações em uma Regra do Visual Studio 2010 Não Afetarão as Versões Anteriores do Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
## <a name="ChildRuleSetChangesInPreviousVersions"></a> Alterações em uma Regra do Visual Studio 2010 Não Afetarão as Versões Anteriores do Visual Studio  
 Ao criar um conjunto de regras no [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] que contém um conjunto de regras filho, uma alteração no conjunto de regras filho pode não ser aplicada em execuções de análise de código em computadores que usam uma versão anterior do Visual Studio. Para resolver esse problema, é necessário forçar uma reescrita de conjunto de regras pai, que é o conjunto de regras que contém o conjunto de regras filho.  
  
1. Abra o conjunto de regras pai no [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2. Faça uma alteração, como adicionar ou remover uma regra e salve o conjunto de regras.  
  
3. Abra o conjunto de regras, reverta a alteração e, em seguida, salve o conjunto de regras novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Analisando a Qualidade do Aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analisando a Qualidade do Código Gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
