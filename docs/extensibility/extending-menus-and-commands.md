---
title: Ampliação de menus e comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711806"
---
# <a name="extend-menus-and-commands"></a>Estender menus e comandos
Comandos são a maneira como você adiciona ações e processos ao Visual Studio. Na maioria dos casos, os comandos são exibidos em menus ou barras de ferramentas. O modelo de projeto VSPackage mostra como implementar um comando muito básico. Para uma implementação um pouco mais longa, mas ainda básica, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Para obter mais informações sobre comandos, menus e barras de ferramentas do Visual Studio, consulte [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

 Comandos, menus e barras de ferramentas são definidos no arquivo *.vsct* que faz parte dos projetos VSPackage. Você pode encontrar informações sobre o Visual Studio IDE e o arquivo *.vsct* em [Como vsPackages adicionam elementos de interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Os tópicos a seguir explicam como adicionar diferentes tipos de comandos, menus e barras de ferramentas.

## <a name="in-this-section"></a>Nesta seção
- [Adicione um menu à barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Explica como adicionar um menu à barra de menus do Visual Studio.

- [Vincular atalhos de teclado a itens de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Explica como adicionar um atalho de teclado (como CTRL + 3) a um item do menu.

- [Adicione um submenu a um menu](../extensibility/adding-a-submenu-to-a-menu.md) Explica como adicionar um submenu ao menu superior.

- [Adicione uma lista usada mais recentemente a um submenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Explica como adicionar uma lista usada mais recentemente.

- [Criar grupos reutilizáveis de botões](../extensibility/creating-reusable-groups-of-buttons.md) Descreve como agrupar itens de comando para que eles possam ser incluídos em vários menus.

- [Adicionar ícones aos comandos do menu](../extensibility/adding-icons-to-menu-commands.md) Descreve como adicionar um ícone a um comando em uma barra de ferramentas e um menu.

- [Alterar o texto de um comando menu](../extensibility/changing-the-text-of-a-menu-command.md) Descreve o uso `TextChanges` do sinalizador para permitir que um item do menu seja alterado dinamicamente.

- [Alterar a aparência de um comando](../extensibility/changing-the-appearance-of-a-command.md) Descreve como ativar ou desativar dinamicamente um comando.

- [Atualize a interface do usuário](../extensibility/updating-the-user-interface.md) Descreve como forçar uma atualização da interface do usuário para refletir as mudanças recentes.

- [Menu localize comandos](../extensibility/localizing-menu-commands.md) Explica como localizar comandos de menu.
