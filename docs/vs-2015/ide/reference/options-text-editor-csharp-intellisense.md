---
title: Opções, Editor de Texto, C#, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662293"
---
# <a name="options-text-editor-c-intellisense"></a>Opções, Editor de Texto, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a página de propriedades **IntelliSense** para modificar as configurações que afetam o comportamento do IntelliSense no Visual C#. É possível acessar a página de propriedades **IntelliSense** clicando em **Opções** no menu **Ferramentas**, clicando em **C#** na pasta **Editor de Texto** e, em seguida, em **IntelliSense.**

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 A página de propriedades **IntelliSense** contém as seguintes propriedades:

## <a name="completion-lists"></a>Listas de Conclusão
 **Mostrar lista de conclusão depois que um caractere é digitado** Quando essa opção é selecionada, o IntelliSense exibe automaticamente a lista de conclusão quando você começa a digitar. Quando essa opção não estiver selecionada, a conclusão do IntelliSense ainda estará disponível no menu do **IntelliSense** ou pressionando CTRL + espaço.

 **Coloque palavras-chave em listas de conclusão** Quando essa opção é selecionada, o IntelliSense adiciona palavras-chave C#, por exemplo, [classe](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690)à lista de conclusão.

 **Coloque trechos de código em listas de conclusão** Quando essa opção é selecionada, o IntelliSense adiciona aliases para trechos de código C# à lista de conclusão. Caso o alias do snippet de código seja igual a uma palavra-chave, por exemplo, [classe](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), a palavra-chave será substituída pelo atalho. Para obter mais informações, consulte [Snippets de código do Visual C#](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Seleção em listas de preenchimento
 **Confirmado digitando os seguintes caracteres:** Especifica todos os caracteres que executam a conclusão automática do IntelliSense para o item selecionado na lista de conclusão, depois que eles são digitados.

 **Confirmado com o pressionamento da barra de espaço** Especifica para incluir a ação de pressionar a barra de espaço para executar a conclusão automática do IntelliSense para o item selecionado na lista de conclusão.

 **Adicionar nova linha ao inserir no final da palavra totalmente digitada** Especifica que, se você digitar todos os caracteres de uma entrada na lista de conclusão e pressionar ENTER, uma nova linha será criada automaticamente e o cursor se moverá para a nova linha.

 Por exemplo, se você digitar `else` e pressionar ENTER, isto será exibido no editor:

 `else`

 `|` (local do cursor)

 No entanto, se você digitar apenas `el` e pressionar ENTER, isto será exibido no editor:

 `else|` (local do cursor)

## <a name="intellisense-member-selection"></a>Seleção de Membro IntelliSense
 **Seleciona previamente o membro usado mais recentemente** Quando essa opção é selecionada, o IntelliSense seleciona previamente os membros que você selecionou recentemente na caixa Membros da lista pop-up para a conclusão automática do nome do objeto, durante a sessão atual no ambiente de desenvolvimento integrado (IDE). O histórico dos membros mais usados recentemente é limpo entre cada sessão no IDE. Para obter mais informações, consulte [IntelliSense para membros usados mais recentemente](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Consulte Também
 [Geral, ambiente, opções caixa de diálogo](../../ide/reference/general-environment-options-dialog-box.md) [XML Comentários de documentação](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [usando o IntelliSense](../../ide/using-intellisense.md)
