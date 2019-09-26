---
title: Visual Studio para Mac para usuários do Windows
description: Introdução dos recursos de acessibilidade no Visual Studio para Mac e como eles podem ser habilitados.
author: alclark
ms.author: alcl
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 3306cdec93b501ad2006bbee2ceca3bf42514fe9
ms.sourcegitcommit: 7739f36507b4762eea83c692102bdc5188460f28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71314482"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio para Mac para usuários do Windows

A migração de um sistema operacional para outro pode ser assustadora. Geralmente, há diferenças sutis em aplicativos de plataforma cruzada, da interface do usuário até a categorização de itens de menu. Os usuários também terão a curva de aprendizado de acclimatizing para a interface do usuário do novo sistema operacional. Aqui você aprenderá as diferenças mais comuns entre o Visual Studio para Mac e o Visual Studio para Windows. Você também aprenderá algumas convenções diferentes entre o macOS e o Windows.

## <a name="keyboard-shortcuts"></a>Atalhos de teclado

Como desenvolvedores, muitos de vocês estarão acostumados a usar o teclado para suas tarefas e navegação. Algumas chaves no teclado são comuns entre Macs e computadores Windows. Você poderia ser Forgiven para pensar que as ações do teclado, como copiar e colar, usam as mesmas combinações de teclas. Isso nem sempre é o caso. Felizmente, você pode alterar suas associações de chave no Visual Studio para Mac para corresponder à correspondência com as do Visual Studio no Windows.

Na primeira vez que você executar Visual Studio para Mac você verá a janela seleção de atalhos de teclado: ![Janela associações de chave](media/ide-tour-2019-keyboard-shortcut.png)

Se você quiser alterar as associações de teclas mais tarde, poderá encontrar a configuração nas preferências: ![Preferências de associações de teclas](media/customizing-the-ide-image10a.png)

É importante observar que o macOS usa diferentes atalhos de todo o sistema para o Windows. A alteração das preferências de associação de chave permitirá que você use atalhos familiares do Windows no Visual Studio para Mac. No entanto, em outras áreas do macOS, você precisará estar familiarizado com atalhos do macOS.

A chave do modificador do comando macOS (⌘) normalmente pode substituir a chave de controle no Windows. Aqui estão alguns exemplos e outros atalhos usados com frequência:

|Tarefa                   |Atalho do Windows         |Atalho do macOS      |
|-----------------------|-------------------------|--------------------|
|Copiar                   |`Ctrl + C`               |`⌘ + C`             |
|Colar                  |`Ctrl + V`               |`⌘ + V`             |
|Recortar                    |`Ctrl + X`               |`⌘ + X`             |
|Desfazer                   |`Ctrl + Z`               |`⌘ + Z`             |
|Refazer                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Excluir à direita do cursor |`Delete`                 |`fn + Backspace`    |
|Excluir palavra            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Você pode encontrar uma lista abrangente de atalhos do macOS no [site de suporte da Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menus

Os menus no macOS são organizados de forma diferente dos menus no Windows. Visual Studio para Mac não é exceção. Você pode encontrar algumas das opções de menu mais comuns aqui:

|Tarefa                   |Visual Studio (Windows)                                              |Visual Studio para Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferências (opções)  |Ferramentas > opções...                                                   |Preferências de > do Visual Studio...       |
|Extensões             |Extensões > gerenciar extensões                                       |Extensões de > do Visual Studio...        |
|Layouts                |Janela > aplicar layout de janela > [selecionar layout]                       |Exibir > [selecionar layout]               |
|Atualizações                |Ajuda > verificar se há atualizações                                             |O Visual Studio > verificar se há atualizações... |
|Gerenciador de pacotes do NuGet  |Ferramentas > Gerenciador de pacotes NuGet > gerenciar pacotes NuGet ou solução... |Projeto > gerenciar pacotes NuGet...   |
|Pads/janelas         |Exibir > [selecionar painel/janela]                                         |Exibir painéis de > > [selecionar painel/janela]  |
|Localizar ferramentas             |Editar > localizar e substituir > [selecionar ferramenta]                              |Pesquisar > [selecionar ferramenta]               |
|Sobre o Visual Studio    |Ajuda > sobre Microsoft Visual Studio                                 |Visual Studio > sobre o Visual Studio  

> [!NOTE]
> Você pode encontrar uma visão geral dos recursos mais comuns do Visual Studio para Mac no [Tour do IDE](ide-tour.md)