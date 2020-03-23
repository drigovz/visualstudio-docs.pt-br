---
title: Como especificar opções de instrumentação adicionais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2d1f7e912ed5960c52e3f0bfa40fe9b87e91a2e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778694"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Como especificar opções de instrumentação adicionais

Você pode instrumentar binários usando o IDE do Visual Studio ou usando ferramentas de linha de comando. Se você instrumentar um binário do IDE, será possível controlar o volume de dados coletados durante a instrumentação, especificando opções de instrumentação adicionais para a ferramenta [VSInstr](../profiling/vsinstr.md). Essas opções estão disponíveis no nível de sessão ou de destino. Por exemplo, para incluir ou excluir funções específicas durante o processo de instrumentação, use a opção adicional de instrumentação no nível de destino.

> [!IMPORTANT]
> Cada investigação que é inserida modifica ligeiramente o comportamento do programa original. Essa modificação gera sobrecarga no tempo de análise. Mesmo que uma aproximação dessa sobrecarga seja subtraída, ela ainda tem efeitos de temporização sutis em aplicativos com multithread. As opções de ferramenta [VSInstr](../profiling/vsinstr.md) ajudam a controlar a coleta de dados durante a criação de perfil.

## <a name="to-specify-additional-instrumentation-option"></a>Como especificar opções de instrumentação adicionais

1. No **Gerenciador de Desempenho**, selecione a **Sessão de Desempenho** e, em seguida, clique com o botão direito do mouse em **Propriedades**.

2. Nas **Páginas de Propriedades**, clique nas propriedades **Avançadas**.

3. Digite opções na caixa **Opções de instrumentação adicionais**.

     Por exemplo, use /CONTROL:THREAD para especificar o nível de criação de perfil. Para obter uma lista completa das opções, consulte [VSInstr](../profiling/vsinstr.md).

4. Clique em **OK**.

## <a name="see-also"></a>Confira também

[Configure o](../profiling/configuring-performance-sessions.md)
perfil das sessões[de desempenho a partir da linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
