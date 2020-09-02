---
title: Contexto do projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429932"
---
# <a name="project-context"></a>Contexto do projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando o usuário adiciona ou trabalha com projetos e itens de projeto, o IDE usa a noção do contexto do projeto para determinar como várias operações devem ser executadas.  
  
 Normalmente, os arquivos são os objetos de projeto padrão que o usuário cria explicitamente selecionando o comando **novo projeto** ou disponibilizando-o selecionando o comando **Abrir projeto** no menu **arquivo** . Nesses casos, os arquivos são criados e abertos no contexto de um projeto e o tipo de projeto define o contexto para editar o documento.  
  
 Alguns projetos fornecem um contexto muito rico. Por exemplo, o projeto gerencia um namespace de escopo de projeto, programático ou conexão de banco de dados com escopo de projeto para associação de dado. O usuário pode abrir com frequência arquivos ou conexões de banco de dados diretamente usando um objeto de projeto específico, como um item de projeto exibido no Gerenciador de Soluções.  
  
 Em outras ocasiões, o contexto do projeto de um item não é especificado explicitamente. Por exemplo, o contexto de um item não está disponível quando o usuário abre um arquivo selecionando o comando **Abrir arquivo existente** no menu **arquivo** , quando o depurador opera em um arquivo ou quando o usuário clica no comando **localizar nos arquivos** na caixa de diálogo **Localizar e substituir** . Para lidar com essas situações, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para gerenciar o processo de localização do melhor projeto para abrir um documento.  
  
## <a name="see-also"></a>Consulte Também  
 [Prioridade do projeto](../../extensibility/internals/project-priority.md)   
 [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
