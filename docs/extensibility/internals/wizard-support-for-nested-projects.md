---
title: Suporte do assistente para projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721427"
---
# <a name="wizard-support-for-nested-projects"></a>Suporte do assistente para projetos aninhados
O IDE executa dois assistentes que o projeto pai para projetos aninhados podem implementar: o assistente de **novo projeto** e o assistente para **Adicionar item** .

 Se um usuário iniciar o assistente de **novo projeto** selecionando **Adicionar projeto** e clicando em **novo projeto** no menu arquivo ou selecionando **Adicionar** e clicando com o botão direito do mouse em **novo projeto** no Gerenciador de soluções, o IDE executa o **AddProject** o comando e a implementação do projeto pai do comando **AddProject** retornam um arquivo de projeto de modelo ou um arquivo de assistente (. vsz) que tem um conjunto de parâmetros de contexto.

 Da mesma forma, a implementação de assistentes de **AddItem** de um projeto pai retorna um arquivo. vsz que tem um conjunto diferente de parâmetros de contexto.

 Para obter mais informações sobre assistentes, consulte [Wizard (. Vsz) arquivo](../../extensibility/internals/wizard-dot-vsz-file.md), [parâmetros de contexto](../../extensibility/internals/context-parameters.md) e [registro de modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Aninhar projetos](../../extensibility/internals/nesting-projects.md)