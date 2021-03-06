---
title: Cenários de depuração sem suporte
description: Saiba mais sobre cenários de depuração sem suporte no Designer de Fluxo de Trabalho, por exemplo, "a execução não pode continuar após a edição do código".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 70620528bd3e2d50b85d67eef5990d9843ea5178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875127"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Cenários sem suporte de depuração no Designer de Fluxo de Trabalho

O Designer de Fluxo de Trabalho não oferece suporte aos seguintes cenários de depuração:

- A execução não pode ser continuada após o código foi editado.

- A execução não pode ser continuada de um ponto arbitrário no fluxo de trabalho (definido em seguida).

- A execução não pode ser continuada até que o cursor seja alcançado (execução ao cursor).

- O designer de fluxo de trabalho não pode ser usado para criar fluxos de trabalho criados em código sem o uso de designer.

- Os fluxos de trabalho criados em versões anteriores do Windows Workflow Foundation (WF) não podem ser depurados no .NET Framework 4 ou posterior.

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

  - Processar

  - Vá para a desmontagem
