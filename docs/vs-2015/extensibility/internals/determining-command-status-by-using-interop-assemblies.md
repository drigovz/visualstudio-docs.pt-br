---
title: Determinando o status do comando usando assemblies de interoperabilidade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196784"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinar o status do comando usando assemblies de interoperabilidade
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um VSPackage deve acompanhar o estado dos comandos que ele pode manipular. O ambiente não pode determinar quando um comando manipulado em seu VSPackage se torna habilitado ou desabilitado. É responsabilidade do seu VSPackage informar o ambiente sobre os Estados de comando, por exemplo, o estado de comandos gerais, como **recortar**, **copiar**e **colar**.  
  
## <a name="status-notification-sources"></a>Fontes de notificação de status  
 O ambiente recebe informações sobre comandos por meio do método VSPackages ' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , que faz parte da implementação da interface do VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . O ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método de VSPackage em duas condições:  
  
- Quando um usuário abre um menu principal ou um menu de contexto (clicando com o botão direito do mouse), o ambiente executa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método em todos os comandos nesse menu para determinar seu estado.  
  
- Quando o VSPackage solicita que o ambiente atualize a interface do usuário atual (IU). Isso ocorre como comandos que estão visíveis no momento para o usuário, como o agrupamento **recortar**, **copiar**e **colar** na barra de ferramentas padrão, são habilitados e desabilitados em resposta ao contexto e às ações do usuário.  
  
  Como o Shell hospeda vários VSPackages, o desempenho do Shell seria inaceitável se fosse necessário para sondar cada VSPackage para determinar o status do comando. Em vez disso, seu VSPackage deve notificar o ambiente ativamente quando sua interface do usuário é alterada no momento da alteração. Para obter mais informações sobre a notificação de atualização, consulte [atualizando a interface do usuário](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Falha na notificação de status  
 Falha de seu VSPackage para notificar o ambiente de uma alteração de estado de comando pode posicionar a interface do usuário em um estado inconsistente. Lembre-se de que qualquer um dos comandos menu ou menu de contexto pode ser colocado em uma barra de ferramentas pelo usuário. Portanto, atualizar a interface do usuário somente quando um menu ou menu de contexto é aberto não é suficiente.  
  
## <a name="see-also"></a>Consulte Também  
 [Como VSPackages adicionar elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementação](../../extensibility/internals/command-implementation.md)
