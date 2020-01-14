---
title: 'DA0006: substituir Equals() para tipos de valor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaba2f099f2a4d04574acd5bcdd2ba8f8f44b4ce
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852360"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: substituir Equals() para tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID da regra | DA0006 |  
| Categoria |. Uso do .NET Framework |  
| Métodos Profiiling | Amostragem |  
| Mensagem | Substituir Equals e operador de igualdade em tipos de valor. |  
| Tipo de mensagens das | Aviso |  
  
## <a name="cause"></a>Causa  
 Chamadas para o método Equals ou os operadores de igualdade de um tipo de valor público são uma parte significativa dos dados de criação de perfil. Considere a implementação de um método mais eficiente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Para tipos de valor, a implementação herdada de Equals usa a biblioteca <xref:System.Reflection> e compara o conteúdo de todos os campos do tipo. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias ou as usem como chaves de tabela de hash, o tipo de valor deverá implementar Equals. Se a linguagem de programação der suporte à sobrecarga de operador, também é necessário fornecer uma implementação dos operadores de igualdade e desigualdade.  
  
 Para obter mais informações sobre como substituir Equals e os operadores de igualdade, consulte [Diretrizes para Implementação de Equals e o Operador de Igualdade (= =)](https://msdn.microsoft.com/library/7h9bszxx.aspx).  
  
## <a name="how-to-investigate-a-warning"></a>Como investigar um aviso  
 Para obter um exemplo de implementação de Equals e operadores de igualdade, consulte a regra de análise de código [CA1815: substituir Equals e operador Equals em tipos de valor](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)
