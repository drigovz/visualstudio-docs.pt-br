---
title: Exibição de detalhes de recurso – Dados de contenção | Microsoft Docs
description: Saiba como o modo de exibição detalhes do recurso apresenta um gráfico de linha do tempo dos eventos de bloqueio que foram causados por contenções em um recurso selecionado.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 715742221b5d8b21f574e7fb8001bd0a3c56cef5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960202"
---
# <a name="resource-details-view---contention-data"></a>Exibição de detalhes do recurso – Dados de contenção
A exibição de Detalhes do Recurso apresenta um gráfico de linha do tempo dos eventos de bloqueio que foram causados por contenções em um recurso selecionado. Um evento de bloqueio ocorre quando um thread é forçado a suspender a execução porque outro thread bloqueou o acesso ao recurso.

 Este modo de exibição representa a linha do tempo de execução de cada thread como uma barra horizontal e cada evento de bloqueio como uma barra vertical na linha do tempo do thread. Quando necessário, você pode ampliar uma seção da linha do tempo para exibir eventos individuais. Para exibir o caminho de execução (pilha de chamadas) das funções que levou ao evento, clique na barra de evento. As funções aparecem na janela **Pilha de Chamadas**. Quando o código-fonte para uma função estiver disponível, você pode clicar no nome de função para editar o arquivo de origem na interface para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="procedures"></a>Procedimentos

#### <a name="to-magnify-a-timeline-segment"></a>Para ampliar um segmento de linha do tempo

- Arraste o ponteiro do mouse sobre uma área da linha do tempo.

     Quando você soltar o botão do mouse, o modo de exibição ampliará o segmento de tempo selecionado. Você pode repetir o processo para ampliar ainda mais o segmento. A caixa de rolagem na barra de rolagem de tempo representa o tamanho relativo do segmento de tempo que aparece na exibição.

#### <a name="to-zoom-out-on-a-timeline"></a>Para reduzir uma linha do tempo

- Execute uma das seguintes etapas:

  - Clique em **Reduzir** para retornar ao nível de zoom anterior.

  - Clique em **Redefinir Zoom** para mostrar toda a linha do tempo na exibição.

#### <a name="to-view-the-call-stack-of-an-event"></a>Para exibir a pilha de chamadas de um evento

- No gráfico de linha do tempo, clique na barra de eventos.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Para exibir ou editar o código-fonte de uma função na pilha de chamadas

- Na janela **Pilha de Chamadas**, clique no nome da função.

  O código-fonte da função deve fazer parte do projeto atual.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Para exibir a árvore de chamadas de eventos de contenção do recurso

- No gráfico de linha do tempo, clique em **Total**.

     A exibição Contenções aparece para o recurso. Para saber mais, confira [Exibição de contenções de recurso](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Para exibir todos os eventos de contenção de um thread

- No gráfico de linha do tempo, clique no nome ou ID do thread.

     A Exibição de Detalhes de Thread é exibida para o thread selecionado. Para obter mais informações, consulte [Exibição de Detalhes do Thread](../profiling/thread-details-view-contention-data.md).
