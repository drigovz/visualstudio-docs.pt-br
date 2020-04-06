---
title: Contexto do Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706592"
---
# <a name="project-context"></a>Contexto do projeto
Quando o usuário adiciona ou trabalha com projetos e itens de projeto, o IDE usa a noção de contexto do projeto para determinar como várias operações devem ser realizadas.

 Normalmente, os arquivos são os objetos padrão do projeto que o usuário cria explicitamente selecionando o comando **Novo projeto** ou disponibiliza, selecionando o comando **Projeto Aberto** no menu **Arquivo.** Nesses casos, os arquivos são criados e abertos no contexto de um projeto e o tipo de projeto define o contexto para a edição do documento.

 Alguns projetos proporcionam um contexto muito rico. Por exemplo, o projeto gerencia um namespace programático com escopo de projeto ou conexão de banco de dados com escopo de projeto para vinculação de dados. O usuário pode frequentemente abrir arquivos ou conexões de banco de dados diretamente usando um objeto de projeto específico, como um item de projeto exibido no Solution Explorer.

 Em outros momentos, o contexto do projeto de um item não é explicitamente especificado. Por exemplo, o contexto de um item não está disponível quando o usuário abre um arquivo selecionando o comando **Abrir arquivo existente** no menu **Arquivo,** quando o depurador opera em um arquivo ou quando o usuário clica no comando **Encontrar em Arquivos** na caixa de diálogo Encontrar e **Substituir.** Para lidar com essas situações, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para gerenciar o processo de encontrar o melhor projeto para abrir um documento.

## <a name="see-also"></a>Confira também
- [Prioridade do projeto](../../extensibility/internals/project-priority.md)
- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
