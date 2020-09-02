---
title: Como gerenciar modos do editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a188e90d3feeb903eb8b4efceb91eb53cac3bdce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651841"
---
# <a name="how-to-manage-editor-modes"></a>Como gerenciar modos do editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível exibir o Editor de Código do Visual Studio em vários modos de exibição.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="enabling-full-screen-mode"></a>Habilitando o modo de tela inteira
 Você pode optar por ocultar todas as janelas de ferramentas e exibir apenas janelas de documentos habilitando o modo de **tela inteira** .

#### <a name="to-enable-full-screen-mode"></a>Para habilitar o modo de tela inteira

- Pressione ALT + SHIFT + ENTER para entrar ou sair do modo de **tela inteira** .

     -- ou --

- Emita o comando `View.Fullscreen` na janela **Comando**.

## <a name="enabling-virtual-space-mode"></a>Habilitando o modo Espaço virtual
 No modo **Espaço virtual**, os espaços são inseridos no final de cada linha de código. Selecione essa opção para posicionar comentários em um ponto consistente ao lado do seu código.

#### <a name="to-enable-virtual-space-mode"></a>Para habilitar o modo Espaço Virtual

1. Selecione **Opções** no menu **Ferramentas**.

2. Expanda a pasta **Editor de Texto** e escolha **Todas as Linguagens** para definir essa opção globalmente ou escolha uma pasta de idioma específico. (Por exemplo, para ativar os números de linha apenas no Visual Basic, escolha as opções Basic, Editor de Texto.)

3. Selecione as opções **Gerais** e, em **Configurações**, selecione **Habilitar Espaço virtual**.

    > [!NOTE]
    > O **Espaço virtual** está habilitado no modo **Seleção de Coluna**. Quando o modo **Espaço virtual** não está habilitado, o ponto de inserção é movido do final de uma linha diretamente para o primeiro caractere da próxima.

## <a name="see-also"></a>Consulte Também
 [Personalizando o editor](../ide/customizing-the-editor.md) [como organizar e encaixar](../misc/how-to-arrange-and-dock-windows.md) [fontes e cores do Windows, caixa de diálogo ambiente, opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
