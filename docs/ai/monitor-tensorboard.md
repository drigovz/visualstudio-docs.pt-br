---
title: Monitorar com TensorBoard
description: Saiba como você pode usar o Visual Studio para visualizar o progresso do treinamento do modelo com o TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 650189c4418355ae06b296bac7e16eece0ea88ad
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727249"
---
# <a name="monitor-with-tensorboard"></a>Monitorar com TensorBoard

É possível visualizar o progresso do treinamento de modelo com TensorBoard.

1. Clique com o botão direito do mouse em seu projeto e em **Executar TensorBoard**. Em seguida, selecione o diretório de seus logs do TensorBoard de saída.

    ![Captura de tela do Visual Studio Gerenciador de Soluções com o projeto MNIST selecionado. Um menu de contexto é aberto e o comando Run TensorBoard é selecionado.](media/monitor-tensorboard/run-tensorboard.png)

2. Observe o erro diminuindo com o decorrer do tempo, o que significa que a qualidade está melhorando.

    ![Captura de tela da janela principal do TensorBoard mostrando visualizações gráficas dos dados dos logs do TensorBoard.](media/monitor-tensorboard/tensorboard.png)
