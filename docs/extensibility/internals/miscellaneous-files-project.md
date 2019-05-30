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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3cf792b10905d0f124266601e791dc91259ce2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349283"
---
# <a name="miscellaneous-files-project"></a>Projeto arquivos diversos
Quando um usuário abre itens do projeto, o IDE atribui ao projeto arquivos diversos todos os itens que não são membros de quaisquer projetos em uma solução.

 Projetos desempenham um papel importante na determinação de qual editor é usado quando um usuário abre um item de projeto. Um projeto pode ser criado para abrir determinados arquivos usando um editor específico do projeto ou um editor padrão.

 Normalmente, um editor específico do projeto requer que o usuário tivesse conhecimento especial ou usar interfaces especiais do projeto. Para obter mais informações, confira [Como: Abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md).

 Um editor padrão pode abrir qualquer arquivo de uma extensão específica em qualquer projeto. O usuário pode personalizar alguns editores padrão, como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor de texto, para projetos, mas ainda manter seus caracteres pública. Editores padrão é criado usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método.

 Se nenhum projeto na solução responde que ele pode abrir um item de projeto, o IDE fornece um projeto especial chamado projeto arquivos diversos que abre qualquer arquivo.

 Este projeto especial fornece para abertura de um arquivo fora do contexto de um projeto. Durante o processamento do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método, o projeto arquivos diversos sempre responde com uma prioridade muito baixa. Portanto, os arquivos diversos projeto sempre produz a qualquer projeto de prioridade mais alta que possa abrir arquivos.

 O projeto arquivos diversos requer que o usuário explicitamente criá-la com o **novo projeto** caixa de diálogo. Além disso, o projeto arquivos diversos não gerencia permanentemente uma lista de membros do projeto. Ele usa um recurso opcional para registrar uma lista dos arquivos usados mais recentemente para cada usuário.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Como: abrir editores específicos a um projeto](../../extensibility/how-to-open-project-specific-editors.md)
- [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
- [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)