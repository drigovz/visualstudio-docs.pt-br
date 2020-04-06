---
title: Prioridade do Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706416"
---
# <a name="project-priority"></a>Prioridade do projeto
Um item do projeto geralmente é membro de apenas um projeto na solução. Portanto, o IDE pode facilmente determinar qual projeto é usado para abrir o item. No entanto, se um item é membro de mais de um projeto, o IDE usa um esquema prioritário para determinar o melhor projeto para abrir o item.

 A lista a seguir mostra o esquema de prioridade do projeto:

- O IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> chama o método para cada projeto na solução para determinar se o documento é membro desse projeto.

- Se o documento for membro do projeto, o projeto responde com prioridade que o projeto atribui de acordo com sua tramitação desse documento. Por exemplo, um projeto de idioma responde com uma alta prioridade para seus arquivos de origem de idioma, mas responde com uma menor prioridade para um tipo de arquivo não reconhecido que não é usado como parte de seu processo de compilação.

- Projetos que fornecem editores ou designers personalizados, específicos para projetos para um documento também recebem uma alta prioridade.

- A <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração fornece os valores prioritários do documento.

- O projeto que especifica a maior prioridade recebe o contexto para abrir o documento. Se dois projetos retornarem valores de prioridade iguais, o projeto ativo é preferido. Se nenhum projeto na solução responder que ele pode abrir o documento, o IDE coloca o documento no projeto Arquivos Diversos. Para obter mais informações, consulte Projeto arquivos [diversos](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Confira também
- [Projeto arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)
- [Como abrir editores para documentos abertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
