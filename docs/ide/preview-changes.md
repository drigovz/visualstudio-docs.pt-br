---
title: Visualizar alterações de código
ms.date: 12/16/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: 485a127faa8228ce5ef17a6208e9cc4e7e50e1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666793"
---
# <a name="preview-changes-window"></a>Janela Visualização de Alterações

Ao usar diversas *ações rápidas* ou ferramentas de *refatoração* no Visual Studio, geralmente é possível visualizar as alterações que serão feitas ao seu projeto antes de aceitá-las. Isso é feito na janela **Visualizar Alterações**.  Por exemplo, aqui está a janela **Visualizar Alterações** mostrando o que será alterado durante uma refatoração de renomeação em um projeto C#:

![Visualizar Alterações](media/previewchanges.png)

A metade superior da janela mostra as linhas específicas que serão alteradas, cada uma com uma caixa de seleção. Você poderá marcar ou desmarcar cada caixa de seleção se você quiser aplicar a refatoração seletivamente, apenas a linhas específicas.

A parte inferior da janela mostra o código formatado do projeto que será alterado, com as áreas afetadas realçadas. Selecionar a linha específica na metade superior da janela realçará a linha correspondente na metade inferior. Isso permite que você pule rapidamente para a linha apropriada e veja o código ao redor.

Depois de revisar as alterações, clique no botão **Aplicar** para confirmar as alterações ou clique no botão **Cancelar** para deixar as coisas como estavam.

## <a name="see-also"></a>Consulte também

- [Refatoração no Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Ações rápidas](../ide/quick-actions.md)
