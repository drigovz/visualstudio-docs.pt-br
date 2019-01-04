---
title: Suporte do Assistente para projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3231dd48cea43f517a5e59f33c80df655032ec0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990117"
---
# <a name="wizard-support-for-nested-projects"></a>Suporte do assistente para projetos aninhados
O IDE executa dois assistentes que o projeto pai para projetos aninhados pode implementar: o **novo projeto** assistente e o **Add Item** assistente.  
  
 Se um usuário inicia o **novo projeto** do assistente selecionando **Add Project** e clicando em **novo projeto** no menu arquivo ou selecionando **adicionar** e o botão direito do mouse **novo projeto** no Gerenciador de soluções, o IDE executa o **AddProject** comando e a implementação do projeto pai o **AddProject**comando retorna um arquivo de projeto de modelo ou um arquivo do assistente (. vsz) que tem um conjunto de parâmetros de contexto.  
  
 Da mesma forma, a implementação do projeto pai da **AddItem** assistentes retorna um arquivo. vsz que tem um conjunto diferente de parâmetros de contexto.  
  
 Para obter mais informações sobre assistentes, consulte [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parâmetros de contexto](../../extensibility/internals/context-parameters.md) e [registrar modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Aninhar projetos](../../extensibility/internals/nesting-projects.md)