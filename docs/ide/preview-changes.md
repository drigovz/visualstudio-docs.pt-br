---
title: Visualizar alterações de código
ms.date: 12/16/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: f45b186153b4cc046d35fd941f6a80e108476fc0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585763"
---
# <a name="preview-changes-window"></a>Janela Visualização de Alterações

Ao usar diversas *ações rápidas* ou ferramentas de *refatoração* no Visual Studio, geralmente é possível visualizar as alterações que serão feitas ao seu projeto antes de aceitá-las. Isso é feito na janela **Visualizar Alterações**.  Por exemplo, aqui está a janela **Visualizar Alterações** mostrando o que será alterado durante uma refatoração de renomeação em um projeto C#:

![Visualizar Alterações](media/previewchanges.png)

A metade superior da janela mostra as linhas específicas que serão alteradas, cada uma com uma caixa de seleção. Você poderá marcar ou desmarcar cada caixa de seleção se você quiser aplicar a refatoração seletivamente, apenas a linhas específicas.

A parte inferior da janela mostra o código formatado do projeto que será alterado, com as áreas afetadas realçadas. Selecionar a linha específica na metade superior da janela realçará a linha correspondente na metade inferior. Isso permite que você pule rapidamente para a linha apropriada e veja o código ao redor.

Depois de revisar as alterações, clique no botão **Aplicar** para confirmar as alterações ou clique no botão **Cancelar** para deixar as coisas como estavam.

## <a name="see-also"></a>Veja também

- [Refatoração no Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Ações rápidas](../ide/quick-actions.md)
