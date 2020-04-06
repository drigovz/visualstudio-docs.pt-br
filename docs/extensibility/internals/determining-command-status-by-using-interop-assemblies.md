---
title: Determinando o status do comando usando montagens interop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708707"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determine o status do comando usando conjuntos interop
Um VSPackage deve acompanhar o estado dos comandos que ele pode manusear. O ambiente não pode determinar quando um comando manipulado dentro do vsPackage fica ativado ou desativado. É responsabilidade do seu VSPackage informar o ambiente sobre estados de comando, por exemplo, o estado dos comandos gerais como **Cut,** **Copy**e **Paste**.

## <a name="status-notification-sources"></a>Fontes de notificação de status
 O ambiente recebe informações sobre comandos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> através do método VSPackages, que faz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> parte da implementação da interface do VSPackage. O ambiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chama o método do VSPackage em duas condições:

- Quando um usuário abre um menu principal ou um menu de contexto <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (clicando com o botão direito), o ambiente executa o método em todos os comandos desse menu para determinar seu estado.

- Quando o VSPackage solicita que o ambiente atualize a interface de usuário atual (UI). Essa atualização ocorre como comandos que estão atualmente visíveis para o usuário, como o agrupamento **Cut**, **Copy**e **Paste** na barra de ferramentas padrão, tornam-se ativados e desativados em resposta às ações de contexto e usuário.

  Uma vez que o shell hospeda vários VSPackages, o desempenho do shell seria inaceitávelmente degradado se fosse necessário sondar cada VSPackage para determinar o status do comando. Em vez disso, o VSPackage deve notificar ativamente o ambiente quando sua iu muda no momento da alteração. Para obter mais informações sobre a notificação de atualização, consulte [Atualizar a interface do usuário](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Falha na notificação de status
 A falha do seu VSPackage em notificar o ambiente de uma alteração de estado de comando pode colocar a ui em um estado inconsistente. Lembre-se que qualquer um dos seus comandos de menu ou menu de contexto pode ser colocado em uma barra de ferramentas pelo usuário. Portanto, atualizar a interface do usuário somente quando um menu ou menu de contexto é aberto não é suficiente.

## <a name="see-also"></a>Confira também
- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementação](../../extensibility/internals/command-implementation.md)
