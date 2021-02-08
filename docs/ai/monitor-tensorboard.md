---
title: Monitorar com TensorBoard
description: Saiba como você pode usar o Visual Studio para visualizar o progresso do treinamento do modelo com o TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: edb6fe17902ad84ec6d7a6e5b9929bd965e7c29b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841387"
---
# <a name="monitor-with-tensorboard"></a>Monitorar com TensorBoard

É possível visualizar o progresso do treinamento de modelo com TensorBoard.

1. Clique com o botão direito do mouse em seu projeto e em **Executar TensorBoard**. Em seguida, selecione o diretório de seus logs do TensorBoard de saída.

    ![Captura de tela do Visual Studio Gerenciador de Soluções com o projeto MNIST selecionado. Um menu de contexto é aberto e o comando Run TensorBoard é selecionado.](media/monitor-tensorboard/run-tensorboard.png)

2. Observe o erro diminuindo com o decorrer do tempo, o que significa que a qualidade está melhorando.

    ![Captura de tela da janela principal do TensorBoard mostrando visualizações gráficas dos dados dos logs do TensorBoard.](media/monitor-tensorboard/tensorboard.png)
