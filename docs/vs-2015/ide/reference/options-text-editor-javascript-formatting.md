---
title: Opções, Editor de Texto, JavaScript, formatação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dcfa4a2fb15ed8f4abfff24aa8e78c2b08eb8412
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662241"
---
# <a name="options-text-editor-javascript-formatting"></a>Opções, Editor de Texto, JavaScript, Formatação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a página **Formatação** da caixa de diálogo **Opções** para definir opções para formatar código no Editor de Código. Para acessar essa página, na barra de menus, escolha **Ferramentas**, **Opções** e, em seguida, expanda **Editor de Texto**, **JavaScript**, e **Formatação**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="automatic-formatting"></a>Formatação automática
 Essas opções determinam quando ocorre a formatação na exibição **Fonte**.

## <a name="uielement-list"></a>Lista UIElement

|Opção|DESCRIÇÃO|
|------------|-----------------|
|**Formatar linha completa ao pressionar Enter**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla Enter.|
|**Formatar instrução concluída em ;**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla de ponto-e-vírgula.|
|**Formatar bloco concluído em }**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla de chave de fechamento.|
|**Formatar ao colar**|Quando essa opção é selecionada, o Editor de Código reformata o código quando você o cola no editor. O editor usa as regras de formatação definidas no momento. Se essa opção não estiver selecionada, o editor usará a formatação original do código colado.|

## <a name="new-lines"></a>Novas Linhas
 Essas opções determinam se o Editor de Código coloca uma chave de abertura para funções e blocos de controle em uma nova linha.

## <a name="uielement-list"></a>Lista UIElement

|Opção|DESCRIÇÃO|
|------------|-----------------|
|**Colocar chave de abertura em nova linha para funções**|Quando essa opção é selecionada, o Editor de Código move a chave de abertura associada a uma função para uma nova linha.|
|**Colocar chave de abertura na nova linha para blocos de controle**|Quando essa opção é selecionada, o Editor de Código move a chave de abertura associada a um bloco de controle (por exemplo, os blocos de controle `if` e `while`) para uma nova linha.|

## <a name="spacing"></a>Espaçamento
 Essas opções determinam como os espaços são inseridos na exibição do **Código-fonte**.

## <a name="uielement-list"></a>Lista UIElement

|Opção|DESCRIÇÃO|
|------------|-----------------|
|**Inserir espaço após delimitador de vírgula**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço depois dos delimitadores de vírgulas.|
|**Inserir espaço após ponto e vírgula na instrução "for"**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço depois de cada ponto-e-vírgula na primeira linha de um loop `for`.|
|**Inserir espaço antes e depois de operadores binários**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço antes e depois de operadores binários (por exemplo, +, -, &&, &#124;&#124;).|
|**Inserir espaço após palavras-chaves em instruções de fluxo de controle**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço depois das palavras-chave JavaScript nas instruções de fluxo de controle.|
|**Inserir espaço após a palavra-chave de função para funções anônimas.**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço após a palavra-chave `function` para funções anônimas.|
|**Inserir espaço após a abertura e antes de fechar parênteses não vazios**|Quando essa opção é selecionada, o Editor de Código adicionará um espaço após o parêntese de abertura e antes do parêntese de fechamento se houver caracteres não vazios dentro dos parênteses.|

## <a name="see-also"></a>Veja também
 [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
