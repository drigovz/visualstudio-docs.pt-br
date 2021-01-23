---
title: Relatório de Marcadores | Microsoft Docs
description: Saiba como o relatório de marcadores lista os marcadores no período de tempo exibido e como a panorâmica ou o zoom pode fazer com que os marcadores apareçam ou desapareçam.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e95cf3b14f804c481ff03ec6fbf72b360efedc7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722107"
---
# <a name="markers-report"></a>Relatório de marcadores
O Relatório de Marcadores lista os marcadores no período de tempo exibido.  A movimentação panorâmica, a aplicação de zoom ou a ocultação de pistas pode fazer com que os marcadores apareçam ou desapareçam. O relatório contém informações sobre cada marcador:

- A hora em que ele foi iniciado, com relação ao começo do rastreamento.

- Sua duração. A duração é zero para mensagens e sinalizadores porque eles representam um instante.

- A ID do thread que o gerou.

- O provedor ETW (Acompanhamento de Eventos para Windows) que o gerou.

- A série de marcadores da qual ele foi escrito.

- A categoria de eventos à qual ele pertence.

- Seu nível de importância.

- Seu tipo (extensão, sinalizador ou mensagem).

- Uma descrição detalhada do que ele representa

  Escolha o botão **Exportar** para salvar o Relatório de Marcadores como um arquivo CSV. Você pode usar os dados no arquivo CSV com outros aplicativos ou ferramentas.

> [!NOTE]
> O Relatório de Marcadores pode exibir 1.000 marcadores. Para ver todos os marcadores, exporte o relatório completo para um arquivo CSV.