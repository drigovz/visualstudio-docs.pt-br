---
title: Suporte do assistente para projetos aninhados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 206fd12ea8f198e1659a49ed566e726e49878c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180336"
---
# <a name="wizard-support-for-nested-projects"></a>Suporte do assistente para projetos aninhados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O IDE executa dois assistentes que o projeto pai para projetos aninhados podem implementar: o assistente de **novo projeto** e o assistente para **Adicionar item** .  
  
 Se um usuário iniciar o assistente de **novo projeto** selecionando **Adicionar projeto** e clicando em **novo projeto** no menu arquivo ou selecionando **Adicionar** e clicando com o botão direito em **novo projeto** no Gerenciador de soluções, o IDE executa o comando **AddProject** e a implementação do projeto pai do comando **AddProject** retorna um arquivo de projeto de modelo ou um arquivo de assistente (. vsz) que tem um conjunto de parâmetros de contexto.  
  
 Da mesma forma, a implementação de assistentes de **AddItem** de um projeto pai retorna um arquivo. vsz que tem um conjunto diferente de parâmetros de contexto.  
  
 Para obter mais informações sobre assistentes, consulte [Wizard (. Vsz) arquivo](../../extensibility/internals/wizard-dot-vsz-file.md), [parâmetros de contexto](../../extensibility/internals/context-parameters.md) e [registro de modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Aninhando projetos](../../extensibility/internals/nesting-projects.md)
