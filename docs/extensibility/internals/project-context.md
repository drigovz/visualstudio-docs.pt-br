---
title: Contexto do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725767"
---
# <a name="project-context"></a>Contexto do projeto
Quando o usuário adiciona ou trabalha com projetos e itens de projeto, o IDE usa a noção do contexto do projeto para determinar como várias operações devem ser executadas.

 Normalmente, os arquivos são os objetos de projeto padrão que o usuário cria explicitamente selecionando o comando **novo projeto** ou disponibilizando-o selecionando o comando **Abrir projeto** no menu **arquivo** . Nesses casos, os arquivos são criados e abertos no contexto de um projeto e o tipo de projeto define o contexto para editar o documento.

 Alguns projetos fornecem um contexto muito rico. Por exemplo, o projeto gerencia um namespace de escopo de projeto, programático ou conexão de banco de dados com escopo de projeto para associação de dado. O usuário pode abrir com frequência arquivos ou conexões de banco de dados diretamente usando um objeto de projeto específico, como um item de projeto exibido no Gerenciador de Soluções.

 Em outras ocasiões, o contexto do projeto de um item não é especificado explicitamente. Por exemplo, o contexto de um item não está disponível quando o usuário abre um arquivo selecionando o comando **Abrir arquivo existente** no menu **arquivo** , quando o depurador opera em um arquivo ou quando o usuário clica no comando **Localizar em arquivos** no  **Caixa de diálogo Localizar e substituir** . Para lidar com essas situações, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para gerenciar o processo de localização do melhor projeto para abrir um documento.

## <a name="see-also"></a>Consulte também
- [Prioridade do projeto](../../extensibility/internals/project-priority.md)
- [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)