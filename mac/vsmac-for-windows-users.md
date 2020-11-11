---
title: Visual Studio para Mac para usuários do Windows
description: Uma introdução ao Visual Studio para Mac para os desenvolvedores familiarizados com o uso do Visual Studio no sistema operacional Windows.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 880811c675aac34a18a65c6eccb8ee10f3347d4c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493368"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio para Mac para usuários do Windows

A migração de um sistema operacional para outro pode ser assustadora. Geralmente, há diferenças sutis em aplicativos de plataforma cruzada, da interface do usuário até a categorização de itens de menu. Aqui você aprenderá as diferenças mais comuns entre o Visual Studio para Mac e o Visual Studio para Windows. Você também aprenderá algumas convenções diferentes entre o macOS e o Windows.

## <a name="keyboard-shortcuts"></a>Atalhos do teclado

Como desenvolvedores, muitos de vocês estarão acostumados a usar o teclado para suas tarefas e navegação. Algumas chaves no teclado são comuns entre Macs e computadores Windows. Você poderia ser Forgiven para pensar que as ações do teclado, como copiar e colar, usam as mesmas combinações de teclas. Isso nem sempre é o caso. Felizmente, você pode alterar suas associações de chave no Visual Studio para Mac para corresponder à correspondência com as do Visual Studio no Windows.

Na primeira vez que você executar Visual Studio para Mac você verá a janela seleção de atalhos de teclado: ![ janela associações de chave](media/ide-tour-2019-keyboard-shortcut.png)

Se você quiser alterar as associações de teclas mais tarde, poderá encontrar a configuração nas preferências: ![ principais ligações de associações de teclas](media/customizing-the-ide-image10a.png)

É importante observar que o macOS usa diferentes atalhos de todo o sistema para o Windows. A alteração das preferências de associação de chave permitirá que você use atalhos familiares do Windows no Visual Studio para Mac. No entanto, em outras áreas do macOS, você precisará estar familiarizado com atalhos do macOS.

A chave do modificador do comando macOS (⌘) normalmente pode substituir a chave de controle no Windows. Aqui estão alguns exemplos e outros atalhos usados com frequência:

|Tarefa                   |Atalho do Windows         |Atalho do macOS      |
|-----------------------|-------------------------|--------------------|
|Copiar                   |`Ctrl + C`               |`⌘ + C`             |
|Colar                  |`Ctrl + V`               |`⌘ + V`             |
|Recortar                    |`Ctrl + X`               |`⌘ + X`             |
|Desfazer                   |`Ctrl + Z`               |`⌘ + Z`             |
|Refaz                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
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
|Layouts                |Janela > aplicar layout de janela > [selecionar layout]                       |Exibir > de layout de > [selecionar layout]               |
|Atualizações                |Ajuda > verificar se há atualizações                                             |O Visual Studio > verificar se há atualizações... |
|Gerenciador de Pacotes NuGet  |Ferramentas > Gerenciador de pacotes NuGet > gerenciar pacotes NuGet ou solução... |Projeto > gerenciar pacotes NuGet...   |
|Localizar ferramentas             |Editar > localizar e substituir > [selecionar ferramenta]                              |Pesquisar > [selecionar ferramenta]               |
|Sobre o Visual Studio    |Ajuda > sobre Microsoft Visual Studio                                 |Visual Studio > sobre o Visual Studio  

> [!NOTE]
> Você pode encontrar uma visão geral dos recursos mais comuns do Visual Studio para Mac no [Tour do IDE](ide-tour.md)