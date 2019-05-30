---
title: Prioridade do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1badd483690ae22f9e314c0f9eb4ac3033d82e4a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328270"
---
# <a name="project-priority"></a>Prioridade do projeto
Um item de projeto geralmente é um membro de apenas um projeto na solução. Portanto, o IDE pode facilmente determinar qual projeto é usado para abrir o item. No entanto, se um item for um membro de mais de um projeto, o IDE usa um esquema de prioridade para determinar o melhor projeto para abrir o item.

 A lista a seguir mostra o esquema de prioridade do projeto:

- As chamadas IDE a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> método para cada projeto na solução para determinar se o documento é um membro desse projeto.

- Se o documento é um membro do projeto, o projeto responde com uma prioridade que o projeto atribui acordo com seu tratamento desse documento. Por exemplo, um projeto de linguagem responde com uma prioridade alta para seus arquivos de origem do idioma, mas responde com uma prioridade mais baixa para um tipo de arquivo não reconhecido que não é usado como parte do processo de compilação.

- Projetos que oferecem designers ou editores personalizados, específicos do projeto para um documento também recebem uma prioridade alta.

- O <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração fornece o documento de valores de prioridade.

- O projeto que especifica a prioridade mais alta é considerando o contexto para abrir o documento. Se dois projetos retornam valores de prioridade igual, o projeto ativo é preferencial. Se nenhum projeto na solução responde que ele pode abrir o documento, o IDE coloca o documento no projeto arquivos diversos. Para obter mais informações, consulte [projeto arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Consulte também
- [Projeto de arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)
- [Como: abrir editores para documentos abertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)