---
title: Persistência e a tabela de documentos em execução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706714"
---
# <a name="persistence-and-the-running-document-table"></a>Persistência e a tabela de documentos em execução
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, os projetos são completamente responsáveis por gerenciar a persistência de seus itens <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>de projeto, que realizam utilizando o serviço, . Os documentos são a unidade básica de persistência no ambiente do Visual Studio. Os projetos coordenam a abertura, a poupança e a renomeação de documentos com a tabela de documentos em execução (RDT), um recurso que rastreia o estado de todos os documentos abertos.

## <a name="managing-persistence"></a>Gerenciamento da persistência
 Os projetos controlam o serviço de persistência <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> do ambiente implementando a interface. Embora o ambiente nunca peça diretamente que um documento persista, ele pede ao projeto de dono (ou hierarquia) para salvar o documento. Isso torna possível que o projeto salve os dados do item do projeto em arquivos locais, arquivos remotos, um banco de dados, um repositório ou outro meio.

 O ambiente global mantém o RDT. O ambiente mantém entradas para todas as janelas abertas e documentos no RDT, o que permite que eles recebam notificações especiais, como quando uma solução é fechada. Além disso, o RDT permite que o ambiente rastreie seus nós correspondentes no **Solution Explorer**. O RDT mantém um registro por objeto aberto e persistente, incluindo arquivos de projeto e documentos de item de projeto.

## <a name="see-also"></a>Confira também
- [Tabela de documento em execução](../../extensibility/internals/running-document-table.md)
- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
