---
title: Cenários de depuração sem suporte no Designer de Fluxo de Trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdbe68b416560b85580e3dd30e5f8138b7cd08fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606931"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Cenários sem suporte de depuração no Designer de Fluxo de Trabalho
Designer de Fluxo de Trabalho em [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] adicionou muitos novos recursos, mas ainda há alguns cenários de depuração que não oferece suporte. Este documento detalha Designer de Fluxo de Trabalho sem suporte a depuração cenários.

- A execução não pode ser continuada após o código foi editado.

- A execução não pode ser continuada de um ponto arbitrário no fluxo de trabalho (definido em seguida).

- A execução não pode ser continuada até que o cursor seja alcançado (execução ao cursor).

- O designer de fluxo de trabalho não pode ser usado para criar fluxos de trabalho criados em código sem o uso de designer.

- Fluxos de trabalho criados em versões anteriores de [!INCLUDE[wf](../includes/wf-md.md)] não podem ser depurado no designer de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

- Os pontos de interrupção não podem ser definidos nos links entre atividades ou nós de <xref:System.Activities.Statements.Flowchart> .

- A área de transferência não estão disponíveis durante a depuração.

- Os pontos de interrupção não são mantidas quando as atividades são copiadas ou coladas.

- Os pontos de interrupção de fluxo de trabalho não podem ser definidos na janela de pilha de chamadas.

- Ao criar pontos de interrupção no designer, as configurações de **linha** e **caractere** na caixa de diálogo **novo ponto de interrupção** não são usadas.

- A janela ou o menu de atalho do ponto de interrupção não suportam as seguintes colunas ou opções para depuração de fluxo de trabalho:

  - Condição

  - Contagem de Ocorrências

  - Quando Visitado

  - Função

  - Dados

  - Processo

  - Vá para a desmontagem
