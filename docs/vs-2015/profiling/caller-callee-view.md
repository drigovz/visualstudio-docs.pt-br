---
title: Exibição de chamador-computador chamado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58aca542571066ecfa9328c9600972665e757150
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788935"
---
# <a name="callercallee-view"></a>Exibição Chamador/Receptor da Chamada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição de Chamador/Computador Chamado exibe informações de perfil para uma função selecionada e suas funções pai e filho. A exibição de Chamador/Computador Chamado contém três grades:  
  
 **Função atual** é exibida na grade intermediária e mostra informações de criação de perfil para a função selecionada. Os valores incluem todas as chamadas para a função que foram coletadas na execução de criação de perfil.  
  
 **Funções que chamaram a função atual** são exibidas na grade superior e mostram o número dos valores da função selecionada (atual) gerados por chamadas da função de chamador (pai).  
  
 **Funções que foram chamadas pela função atual** são exibidas na grade inferior e mostram informações de criação de perfil para as funções do computador chamado (filho) da função selecionada quando a função filho foi chamada pela função atual.  
  
 As colunas que estão disponíveis na exibição de Chamador/Computador Chamado dependem do método de criação de perfil (amostragem ou instrumentação) usado para coletar os dados e de se os dados de memória do .NET foram coletados na execução da criação de perfil.  
  
 Você pode selecionar uma função diferente para ser a Função Atual na parte do meio da exibição de Relatório clicando duas vezes em qualquer uma das funções listadas nas outras duas partes da exibição. A exibição de Relatório é atualizada automaticamente para refletir as alterações.  
  
 Você pode classificar os dados clicando em nomes de coluna. Colunas adicionais podem ser incluídas na exibição de Chamador/Computador Chamado. Para obter mais informações, consulte [Como personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de chamador/computador chamado – dados de amostragem](../profiling/caller-callee-view-sampling-data.md)   
 [Exibição de chamador/computador chamado – dados de instrumentação](../profiling/caller-callee-view-instrumentation-data.md)   
 [Exibição Chamador/Receptor da Chamada – dados de instrumentação da memória do .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Exibição Chamador/Receptor da Chamada – dados de amostragem da memória do .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Exibição do chamador/computador chamado – dados de contenção](../profiling/caller-callee-view-contention-data.md)
