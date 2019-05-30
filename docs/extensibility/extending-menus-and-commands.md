---
title: Estendendo os Menus e comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0810e1fde5b58416b94607dccf2004fe7edb67b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341136"
---
# <a name="extend-menus-and-commands"></a>Ampliar menus e comandos
Comandos são a maneira de adicionar ações e processos no Visual Studio. Na maioria dos casos, comandos são exibidos em menus ou barras de ferramentas. O modelo de projeto de VSPackage mostra como implementar um comando muito básico. Para uma implementação de um pouco maior, mas ainda básica, consulte [criar uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Para obter mais informações sobre comandos, menus e barras de ferramentas do Visual Studio, consulte [comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

 Comandos, menus e barras de ferramentas são definidas na *VSCT* arquivo que é parte dos projetos de VSPackage. Você pode encontrar informações sobre o IDE do Visual Studio e o *VSCT* arquivo no [VSPackages como adicionar elementos da interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Os tópicos a seguir explicam como adicionar tipos diferentes de comandos, menus e barras de ferramentas.

## <a name="in-this-section"></a>Nesta seção
- [Adicionar um menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) explica como adicionar um menu a barra de menus superior do Visual Studio.

- [Associar atalhos de teclado aos itens de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) explica como adicionar um atalho de teclado (por exemplo, CTRL + 3) para um item de menu.

- [Adicionar um submenu a um menu](../extensibility/adding-a-submenu-to-a-menu.md) explica como adicionar um submenu no menu superior.

- [Adicionar uma lista de usados recentemente a um submenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) explica como adicionar uma lista de usados recentemente.

- [Criar grupos reutilizáveis de botões](../extensibility/creating-reusable-groups-of-buttons.md) descreve como agrupar itens de comando para que eles possam ser incluídos em vários menus.

- [Adicionar ícones a comandos de menu](../extensibility/adding-icons-to-menu-commands.md) descreve como adicionar um ícone para um comando em uma barra de ferramentas e um menu.

- [Alterar o texto de um comando de menu](../extensibility/changing-the-text-of-a-menu-command.md) descreve o uso do `TextChanges` sinalizador para ativar um item de menu a ser alterado dinamicamente.

- [Alterar a aparência de um comando](../extensibility/changing-the-appearance-of-a-command.md) descreve como habilitar ou desabilitar um comando.

- [Atualizar a interface do usuário](../extensibility/updating-the-user-interface.md) descreve como forçar uma atualização da interface do usuário para refletir as alterações recentes.

- [Localizar os comandos de menu](../extensibility/localizing-menu-commands.md) explica como localizar os comandos de menu.