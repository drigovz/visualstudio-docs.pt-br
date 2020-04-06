---
title: Suporte de assistente para projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703202"
---
# <a name="wizard-support-for-nested-projects"></a>Suporte do assistente para projetos aninhados
O IDE executa dois assistentes que o projeto pai para projetos aninhados pode implementar: o assistente **Novo projeto** e o assistente **Adicionar item.**

 Se um usuário iniciar o assistente **Novo projeto** selecionando **Adicionar projeto** e clicando em **Novo Projeto** no menu Arquivo ou selecionando **Adicionar** e clicar com o botão direito do mouse novo **projeto** no Explorador de soluções, o IDE executa o comando **AddProject** e a implementação do projeto pai do comando **AddProject** retorna um arquivo de projeto de modelo ou um arquivo assistente (.vsz) que tem um conjunto de parâmetros de contexto.

 Da mesma forma, a implementação de um projeto pai de **assistentes AddItem** retorna um arquivo .vsz que tem um conjunto diferente de parâmetros de contexto.

 Para obter mais informações sobre assistentes, consulte [Wizard (. Vsz) Arquivo,](../../extensibility/internals/wizard-dot-vsz-file.md) [Parâmetros de Contexto](../../extensibility/internals/context-parameters.md) e [Modelos de Projeto e Itens de Registro.](../../extensibility/internals/registering-project-and-item-templates.md)

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Aninhando projetos](../../extensibility/internals/nesting-projects.md)
