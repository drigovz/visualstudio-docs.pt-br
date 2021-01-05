---
title: Projeto de arquivos diversos | Microsoft Docs
description: Saiba mais sobre os dois tipos de editores que podem ser usados para abrir arquivos em um projeto do Visual Studio e a função do projeto para determinar qual editor deve ser usado.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a963b4d452a5d8ea9e0556b232f488e93dc0a29c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876773"
---
# <a name="miscellaneous-files-project"></a>Projeto arquivos diversos
Quando um usuário abre itens de projeto, o IDE é atribuído ao projeto de arquivos diversos quaisquer itens que não sejam membros de nenhum projeto em uma solução.

 Os projetos desempenham uma função significativa para determinar qual editor é usado quando um usuário abre um item de projeto. Um projeto pode ser criado para abrir determinados arquivos usando um editor específico do projeto ou um editor padrão.

 Um editor específico de projeto normalmente requer que o usuário tenha conhecimento especial ou use interfaces especiais do projeto. Para obter mais informações, consulte [como: abrir editores de Project-Specific](../../extensibility/how-to-open-project-specific-editors.md).

 Um editor padrão pode abrir qualquer arquivo de uma extensão específica em qualquer projeto. O usuário pode personalizar alguns editores padrão, como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Editor de texto, para projetos, mas ainda manter seu caractere público. Os editores padrão são criados usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método.

 Se nenhum projeto na solução responder que pode abrir um item de projeto, o IDE fornece um projeto especial chamado projeto de arquivos diversos que abre qualquer arquivo.

 Esse projeto especial fornece a abertura de um arquivo fora do contexto de um projeto. Durante o processamento do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método, o projeto de arquivos diversos sempre responde com uma prioridade muito baixa. Portanto, o projeto de arquivos diversos sempre gera qualquer projeto de prioridade mais alta que pode abrir arquivos.

 O projeto de arquivos diversos não exige que o usuário o crie explicitamente com a caixa de diálogo **novo projeto** . Além disso, o projeto de arquivos diversos não gerencia permanentemente uma lista de membros do projeto. Ele usa um recurso opcional para registrar uma lista de arquivos usados mais recentemente para cada usuário.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Como abrir editores específicos a um projeto](../../extensibility/how-to-open-project-specific-editors.md)
- [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
