---
title: 'DA0503: Conjunto de trabalho médio em bytes para o processo do qual o perfil está sendo criado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2453b73d7dae0a6a53130156cdb1ce35d38d43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935982"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Média de Conjunto de Trabalho em Bytes para o Processo cujo perfil está sendo criado

|||
|-|-|
|ID de regra|DA0503|
|Categoria|Monitoramento de recursos|
|Método de criação de perfil|Todos|
|Mensagem|Essas informações foram coletadas apenas para fins informativos. O contador Conjunto de trabalho do processo mede o uso de memória física do processo do qual está sendo criado o perfil. O valor relatado é a média calculada de todos os intervalos de medição.|
|Tipo de regra|Informações|

 Ao criar o perfil usando a amostragem, a memória do .NET ou métodos de contenção de recursos, é necessário coletar pelo menos 10 amostras para disparar essa regra.

## <a name="rule-description"></a>Descrição da regra
 Essa mensagem relata a quantidade média de memória física que o processo está usando em bytes (o conjunto de trabalho). O conjunto de trabalho do processo representa páginas do espaço de endereço do processo que atualmente residem na memória física.

 O valor relatado inclui páginas residentes de segmentos de memória compartilhada referenciados pelo processo. DLLs compartilhadas que o processo referencia estão incluídas nos segmentos de memória compartilhada contados. O valor do conjunto de trabalho do processo pode ser maior que a quantidade de memória virtual que o processo alocou devido a segmentos de memória compartilhada.

 O valor relatado é a média de todos os intervalos de medição em que o processo do qual o perfil está sendo criado estava ativo.

 O tamanho do conjunto de trabalho do processo reflete a quantidade de memória virtual que o processo está usando de forma ativa. Ele também é afetado pela quantidade de memória física (ou RAM) disponível para executar o aplicativo e a contenção para a memória física de outros processos em execução. Se a memória física for restrita, o valor do conjunto de trabalho do processo estará apto a variar de forma considerável, conforme o sistema operacional tenta equilibrar o uso de memória entre os processos ativos cortando periodicamente as páginas razoavelmente inativas dos conjuntos de trabalho do processo.

 Para obter mais informações sobre conjuntos de trabalho do processo, consulte [Conjunto de trabalho](http://go.microsoft.com/fwlink/?LinkId=177830) na documentação do Gerenciamento de memória do Windows do MSDN.

## <a name="how-to-use-rule-data"></a>Como usar dados de regra
 Use o valor da regra para comparar o desempenho de diferentes versões ou compilações do programa ou para entender o desempenho do aplicativo em diferentes cenários de criação de perfil.

 Clique duas vezes na mensagem da janela Lista de Erros para navegar para a [Exibição de Marcas](../profiling/marks-view.md) dos dados de criação de perfil. Encontre as colunas **Processo\Conjunto de trabalho** e **Memória\Páginas/s**. Compare as duas colunas e determine se há fases específicas da execução do programa que parecem estar associadas a um aumento da atividade de E/S de paginação.