---
title: Projeto de arquivos diversos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179781"
---
# <a name="miscellaneous-files-project"></a>Projeto arquivos diversos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando um usuário abre itens de projeto, o IDE é atribuído ao projeto de arquivos diversos quaisquer itens que não sejam membros de nenhum projeto em uma solução.  
  
 Os projetos desempenham uma função significativa para determinar qual editor é usado quando um usuário abre um item de projeto. Um projeto pode ser criado para abrir determinados arquivos usando um editor específico do projeto ou um editor padrão.  
  
 Um editor específico de projeto normalmente requer que o usuário tenha conhecimento especial ou use interfaces especiais do projeto. Para obter mais informações, consulte [como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Um editor padrão pode abrir qualquer arquivo de uma extensão específica em qualquer projeto. O usuário pode personalizar alguns editores padrão, como o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Editor de texto, para projetos, mas ainda manter seu caractere público. Os editores padrão são criados usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método.  
  
 Se nenhum projeto na solução responder que pode abrir um item de projeto, o IDE fornece um projeto especial chamado projeto de arquivos diversos que abre qualquer arquivo.  
  
 Esse projeto especial fornece a abertura de um arquivo fora do contexto de um projeto. Durante o processamento do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método, o projeto de arquivos diversos sempre responde com uma prioridade muito baixa. Portanto, o projeto de arquivos diversos sempre gera qualquer projeto de prioridade mais alta que pode abrir arquivos.  
  
 O projeto de arquivos diversos não exige que o usuário o crie explicitamente com a caixa de diálogo **novo projeto** . Além disso, o projeto de arquivos diversos não gerencia permanentemente uma lista de membros do projeto. Ele usa um recurso opcional para registrar uma lista de arquivos usados mais recentemente para cada usuário.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Como: abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)   
 [Adicionando projetos e modelos de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
