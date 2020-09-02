---
title: 'DA0003: muitas amostras de kernel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158710"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Muitas amostras de kernel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID da regra | DA0003 |  
| Categoria | Uso de Ferramentas de Criação de Perfil |  
| Métodos de criação de perfil | Amostragem |  
| Mensagem | Você tem uma alta proporção de exemplos no modo kernel. Isso pode indicar um alto volume de atividade de E/S ou uma taxa alta de alternância de contexto. Considere a criação de perfil para o aplicativo novamente usando o Modo de Instrumentação.|  
| Tipo de regra | Informações |  
  
## <a name="cause"></a>Causa  
 Uma parte significativa dos exemplos de pilha de chamadas coletados para o aplicativo estavam sendo executados em modo kernel. Considere a criação de perfil para o aplicativo usando um método de criação de perfil diferente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 No Windows, o código pode ser executado no modo kernel ou no modo de usuário. (O modo kernel também é chamado de modo privilegiado.) Somente o código do sistema de nível baixo, como drivers de dispositivo, é executado no modo kernel. Um aplicativo de modo de usuário pode fazer a transição para o modo kernel para executar operações de E/S, aguardar os primitivos de sincronização de thread ou de processo ou fazer chamadas do sistema.  
  
 A amostragem é a maneira mais eficaz ao criar perfis para aplicativos que passam a maior parte do tempo em modo de usuário. O número de amostras coletadas quando o aplicativo estava sendo executado no modo kernel pode indicar operações de E/S frequentes ou que esse alternâncias de contexto estão ocorrendo. Nenhuma dessas operações podem ser investigadas usando o método de amostragem. Caso muitas amostras do modo kernel forem usadas, os dados de amostragem podem não conter amostras suficientes de modo de usuário para serem estatisticamente significativos.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Considere criar um novo perfil para o aplicativo usando uma das opções a seguir:  
  
- Crie perfis usando o método de instrumentação.  
  
- Aumente a taxa de amostragem para coletar mais amostras no modo de usuário.
