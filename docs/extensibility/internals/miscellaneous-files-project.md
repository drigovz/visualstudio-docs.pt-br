---
title: Projeto arquivos diversos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707092"
---
# <a name="miscellaneous-files-project"></a>Projeto arquivos diversos
Quando um usuário abre itens de projeto, o IDE atribui ao projeto Arquivos Diversos quaisquer itens que não sejam membros de nenhum projeto em uma solução.

 Os projetos desempenham um papel significativo na determinação de qual editor é usado quando um usuário abre um item do projeto. Um projeto pode ser projetado para abrir certos arquivos usando um editor específico de projeto ou um editor padrão.

 Um editor específico de projeto normalmente exige que o usuário tenha conhecimento especial ou use interfaces especiais do projeto. Para obter mais informações, consulte [Como: Abrir editores específicos de projetos.](../../extensibility/how-to-open-project-specific-editors.md)

 Um editor padrão pode abrir qualquer arquivo de uma extensão específica em qualquer projeto. O usuário pode personalizar alguns editores padrão, como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor de texto, para projetos, mas ainda manter seu caráter público. Os editores padrão são <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> criados usando o método.

 Se nenhum projeto na solução responder que pode abrir um item do projeto, o IDE fornece um projeto especial chamado projeto Arquivos Diversos que abre qualquer arquivo.

 Este projeto especial prevê a abertura de um arquivo fora do contexto de um projeto. Durante o processamento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> do método, o projeto Arquivos Diversos sempre responde com uma prioridade muito baixa. Portanto, o projeto Arquivos Diversos sempre cede a qualquer projeto de maior prioridade que possa abrir arquivos.

 O projeto Arquivos Diversos não exige que o usuário o crie explicitamente com a caixa de diálogo **Novo Projeto.** Além disso, o projeto Arquivos Diversos não gerencia permanentemente uma lista de membros do projeto. Ele usa um recurso opcional para gravar uma lista dos arquivos mais usados recentemente para cada usuário.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Como abrir editores específicos a um projeto](../../extensibility/how-to-open-project-specific-editors.md)
- [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
