---
title: Visual Studio para Usuários de Mac para Usuários windows
description: Introdução de recursos de acessibilidade no Visual Studio para Mac e como eles podem ser habilitados.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984265"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio para Usuários de Mac para Usuários windows

Migrar de um sistema operacional para outro pode ser assustador. Muitas vezes há diferenças sutis em aplicativos multiplataforma, desde a interface do usuário até a categorização dos itens do menu. Os usuários também terão a curva de aprendizado de aclimatação à interface de usuário do novo sistema operacional. Aqui você aprenderá as diferenças mais comuns entre o Visual Studio para Mac e o Visual Studio para Windows. Você também aprenderá algumas convenções diferentes entre macOS e Windows.

## <a name="keyboard-shortcuts"></a>Atalhos do teclado

Como desenvolvedores, muitos de vocês estarão acostumados a usar o teclado para suas tarefas e navegação. Algumas teclas no teclado são comuns entre Macs e PCs windows. Você pode ser perdoado por pensar que ações de teclado, como copiar e colar, usam as mesmas combinações de teclas. Nem sempre é assim. Felizmente, você pode alterar suas ligações principais no Visual Studio para Mac para combinar de perto com as do Visual Studio no Windows.

A primeira vez que você executar o Visual Studio para ![Mac, você verá a janela de seleção de atalhos de teclado: Janela de vinculações de teclas](media/ide-tour-2019-keyboard-shortcut.png)

Se você quiser alterar as vinculações de tecla mais tarde, você pode encontrar a configuração nas preferências: ![Principais vinculações preferências](media/customizing-the-ide-image10a.png)

É importante notar que o macOS usa diferentes atalhos em todo o sistema para o Windows. Alterar as principais preferências de vinculação permitirá que você use atalhos conhecidos do Windows no Visual Studio para Mac. No entanto, em outras áreas do macOS você precisará estar familiarizado com os atalhos do macOS.

A chave modificadora do comando macOS pode substituir comumente a tecla Control no Windows. Aqui estão alguns exemplos e outros atalhos comumente usados:

|Tarefa                   |Atalho do Windows         |atalho macOS      |
|-----------------------|-------------------------|--------------------|
|Cópia                   |`Ctrl + C`               |`⌘ + C`             |
|Colar                  |`Ctrl + V`               |`⌘ + V`             |
|Recortar                    |`Ctrl + X`               |`⌘ + X`             |
|Desfazer                   |`Ctrl + Z`               |`⌘ + Z`             |
|Refaz                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Excluir o direito do cursor |`Delete`                 |`fn + Backspace`    |
|Excluir palavra            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Você pode encontrar uma lista abrangente de atalhos para macOS no [site de suporte da Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menus

Os menus no macOS são organizados de forma diferente dos menus do Windows. Visual Studio para Mac não é exceção. Você pode encontrar algumas das opções de menu mais comuns aqui:

|Tarefa                   |Visual Studio (Windows)                                              |Visual Studio para Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferências (Opções)  |Ferramentas > Opções...                                                   |Visual Studio > Preferências...       |
|Extensões             |Extensões > gerenciar extensões                                       |Visual Studio > Extensões...        |
|Layouts                |> de janela aplicar > de layout de janela [Selecionar layout]                       |Exibir > [Selecionar layout]               |
|Atualizações                |Ajuda > verificar atualizações                                             |Visual Studio > Check for Updates... |
|Gerenciador de Pacotes NuGet  |Ferramentas > NuGet Package Manager > gerenciar pacotes ou solução nuget... |Projeto > Gerenciar pacotes NuGet...   |
|Pads / Windows         |Exibir > [Selecionar Pad / janela]                                         |Ver > Pads > [Selecionar almofada / janela]  |
|Encontre ferramentas             |Editar > Encontrar e Substituir > [Ferramenta Selecionar]                              |Pesquisar > [Selecionar ferramenta]               |
|Sobre o Visual Studio    |Ajude-> sobre o Microsoft Visual Studio                                 |Visual Studio > Sobre Visual Studio  

> [!NOTE]
> Você pode encontrar uma visão geral dos recursos mais comuns no Visual Studio for Mac no [IDE Tour](ide-tour.md)