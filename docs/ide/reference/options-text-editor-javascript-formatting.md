---
title: Opções, Editor de Texto, JavaScript, Formatação
description: Saiba como usar a página formatação da caixa de diálogo opções para definir opções de formatação de código no editor de códigos.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a127263bc9bf94997585d07bff1b8d317b282e91
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947733"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Caixa de diálogo opções: \> formatação JavaScript do editor de texto \>

Use a página **Formatação** da caixa de diálogo **Opções** para definir opções para formatar código no Editor de Código. Para acessar essa página, na barra de menus, escolha **ferramentas**  >  **Opções**e expanda formatação do **Editor de texto**  >  **JavaScript/TypeScript**  >  **Formatting**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Formatação automática

Essas opções determinam quando ocorre a formatação na exibição **Fonte**.

### <a name="uielement-list"></a>Lista de elementos de interface do usuário

|Opção|Descrição|
|------------|-----------------|
|**Formatar linha completa ao pressionar Enter**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla Enter.|
|**Formatar instrução concluída em ;**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla de ponto-e-vírgula.|
|**Formatar bloco aberto em {**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla de chave de abertura.|
|**Formatar bloco concluído em }**|Quando essa opção é selecionada, o Editor de Código formata automaticamente a linha quando você escolhe a tecla de chave de fechamento.|
|**Formatar ao colar**|Quando essa opção é selecionada, o Editor de Código reformata o código quando você o cola no editor. O editor usa as regras de formatação definidas no momento. Se essa opção não estiver selecionada, o editor usará a formatação original do código colado.|

## <a name="new-lines"></a>Novas Linhas

Essas opções determinam se o Editor de Código coloca uma chave de abertura para funções e blocos de controle em uma nova linha.

### <a name="uielement-list"></a>Lista de elementos de interface do usuário

|Opção|Descrição|
|------------|-----------------|
|**Colocar chave de abertura em nova linha para funções**|Quando essa opção é selecionada, o Editor de Código move a chave de abertura associada a uma função para uma nova linha.|
|**Colocar chave de abertura na nova linha para blocos de controle**|Quando essa opção é selecionada, o Editor de Código move a chave de abertura associada a um bloco de controle (por exemplo, os blocos de controle `if` e `while`) para uma nova linha.|

## <a name="spacing"></a>Espaçamento

Essas opções determinam como os espaços são inseridos na exibição do **Código-fonte**.

### <a name="uielement-list"></a>Lista de elementos de interface do usuário

|Opção|Descrição|
|------------|-----------------|
|**Inserir espaço após delimitador de vírgula**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço depois dos delimitadores de vírgulas.|
|**Inserir espaço após ponto e vírgula nas instruções "for"**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço depois de cada ponto-e-vírgula na primeira linha de um loop `for`.|
|**Inserir espaço antes e depois de operadores binários**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço antes e depois de operadores binários (por exemplo, +, -, &&, &#124;&#124;).|
|**Inserir espaço após palavras-chaves em instruções de fluxo de controle**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço depois das palavras-chave JavaScript nas instruções de fluxo de controle.|
|**Inserir espaço após palavra-chave Function para funções anônimas**|Quando essa opção é selecionada, o Editor de Código adiciona um espaço após a palavra-chave `function` para funções anônimas.|
|**Inserir espaço após a abertura e antes de fechar parênteses não vazios**|Quando essa opção é selecionada, o Editor de Código adicionará um espaço após o parêntese de abertura e antes do parêntese de fechamento se houver caracteres não vazios dentro dos parênteses.|

## <a name="see-also"></a>Veja também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)