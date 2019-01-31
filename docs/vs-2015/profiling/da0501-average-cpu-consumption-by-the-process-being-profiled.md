---
title: 'DA0501: Consumo médio de CPU pelo Processo cujo perfil está sendo criado. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771948"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Consumo médio de CPU pelo Processo cujo perfil está sendo criado.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id da regra | DA501 |  
| Categoria | Monitoramento de recursos |  
| Método de criação de perfil | Todos os |  
| Mensagem | Média de consumo da CPU pelo processo que está sendo analisado. |  
| Tipo de regra | Informações |  
  
 Ao criar o perfil usando a amostragem, a memória do .NET ou métodos de contenção de recursos, é necessário coletar pelo menos 10 amostras para disparar essa regra.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa mensagem relata o percentual de tempo que um processador esteve ocupado executando instruções do aplicativo. O valor relatado é a média de todos os intervalos de medição em que o processo do qual o perfil está sendo criado estava ativo. O valor do valor pode ser maior que 100% em um computador com mais de um processador.  
  
## <a name="how-to-use-rule-data"></a>Como usar dados de regra  
 Use o valor da regra para comparar o desempenho de diferentes versões ou compilações do programa ou para entender o desempenho do aplicativo em diferentes cenários de teste.
