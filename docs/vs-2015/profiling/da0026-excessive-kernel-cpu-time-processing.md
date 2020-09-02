---
title: 'DA0026: excesso de processamento de tempo de CPU do kernel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef0a3c42be1057bd1217ec676ae43b220d80345
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152666"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Processamento de tempo de CPU do kernel excessivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID da regra | TODO |  
| Categoria | Uso de Ferramentas de Criação de Perfil |  
| Método de criação de perfil | Amostragem |  
| Mensagem | Uma quantidade relativamente alta de tempo de CPU de modo kernel foi medida. Considere a investigação da fonte com a amostragem de SysCall habilitada.|  
| Tipo de regra | Informações |  
  
 Ao criar o perfil usando a amostragem, a memória do .NET ou métodos de contenção de recursos, é necessário coletar pelo menos 10 amostras para disparar essa regra.  
  
## <a name="cause"></a>Causa  
 A proporção de tempo da CPU que foi executada em modo kernel excedeu o tempo gasto no modo de usuário. Considere uma nova criação de perfil e a amostragem do número de chamadas do sistema (syscalls) para determinar a causa dos altos tempos de execução de modo do kernel.  
  
## <a name="rule-description"></a>Descrição da Regra  
 A proporção relativamente alta de tempo gasto pelo aplicativo na execução em modo kernel pode garantir uma investigação adicional. Um aplicativo de modo de usuário faz a transição para o modo de kernel para executar operações de E/S, aguardar os primitivos de sincronização de thread ou de processo ou fazer chamadas do sistema. É possível investigar os tipos de chamadas do sistema feitas pelo aplicativo e quais funções são responsáveis por elas ao selecionar a opção para coletar as pilhas de chamadas de amostra com base em chamadas do Sistema.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para investigar os tipos de chamadas do sistema feitas pelo aplicativo, execute o perfil novamente e selecione a opção para coletar amostras com base em chamadas do sistema. Consulte [Como escolher eventos de amostragem](../profiling/how-to-choose-sampling-events.md) se estiver executando as ferramentas de criação de perfil na IDE para obter mais informações. Se você estiver executando as ferramentas de criação de perfil por meio da linha de comando, consulte a seção **Opções de intervalo de amostragem** do tópico [VSPerfCmd](../profiling/vsperfcmd.md) na referência das ferramentas de linha de comando das Ferramentas de Criação de Perfil.
