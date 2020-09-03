---
title: Opções, Editor de Texto, Básico (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662379"
---
# <a name="options-text-editor-basic-visual-basic"></a>Opções, Editor de Texto, Básico (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A página de propriedades **Específico do VB**, na pasta **Básico** da pasta **Editor de Texto** da caixa de diálogo **Opções** (menu **Ferramentas**) contém as seguintes propriedades:

 **Inserção automática de construtores end** Quando você digita, por exemplo, a primeira linha de uma declaração de procedimento, `Sub Main—`e pressiona Enter, o editor de texto adiciona uma linha `End Sub` correspondente. Da mesma forma, se você adicionar um loop [For](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9), o editor de texto adicionará uma instrução `Next` correspondente. Quando essa opção é selecionada, o editor de código adiciona automaticamente o constructo final.

 **Reformatação automática do código** O editor de texto reformata seu código conforme o necessário. Quando essa opção é selecionada, o editor de códigos:

- Alinhará seu código com a posição correta de guia

- Redefinirá as maiúsculas e minúsculas de palavras-chave, variáveis e objetos para o formato correto

- Adicionará um `Then` ausente a uma instrução `If...Then`

- Adicionará parênteses a chamadas de função

- Adicionará aspas finais faltando a cadeias de caracteres

- Reformatará notação exponencial

- Reformatará datas

  **Habilitar modo de estrutura de tópicos** Ao abrir um arquivo no editor de código, você pode exibir o documento no modo de estrutura de tópicos. Consulte [Estrutura de Tópicos](../../ide/outlining.md) para obter mais informações. Quando essa opção é selecionada, o recurso de estrutura de tópicos é ativado quando você abre um arquivo.

  **Inserção automática de membros de interface e MustOverride** Quando você confirma uma `Implements` instrução ou uma `Inherits` instrução para uma classe, o editor de texto insere protótipos para os membros que precisam ser implementados ou substituídos, respectivamente.

  **Mostrar separadores de linha de procedimento** O editor de texto indica o escopo visual de procedimentos. Uma linha é desenhada nos arquivos de origem .vb do seu projeto nos locais listados na tabela a seguir:

|Local no arquivo de origem .vb|Exemplo de local da linha|
|---------------------------------|------------------------------|
|Após o encerramento de um constructo de declaração de bloco|–   No final de uma classe, estrutura, módulo, interface ou enumeração<br />–   Depois de uma propriedade, função ou sub<br />–   Não entre cláusulas get e set em uma propriedade|
|Depois de um conjunto de constructos de linha única|–   Depois das instruções de importação, antes de uma definição de tipo em um arquivo de classe<br />–   Depois de variáveis declaradas em uma classe, antes de qualquer procedimento|
|Depois de declarações de linha única (declarações de nível não de bloco)|–   Após instruções de importação, instruções de herdar, declarações de variável, declarações de evento, declarações de delegado e instruções de declaração DLL|

 **Habilitar sugestões de correção de erro** O editor de texto pode sugerir soluções para erros comuns e permitir que você selecione a correção apropriada, que é então aplicada ao seu código.

 **Habilitar realce de referências e palavras-chave** O editor de texto pode realçar todas as instâncias de um símbolo ou todas as palavras-chave em uma cláusula, como, `If..Then` `While...End While` ou `Try...Catch...Finally` . Você pode navegar entre referências realçadas ou palavras-chave pressionando CTRL+SHIFT+SETA PARA BAIXO ou CTRL+SHIFT+SETA PARA CIMA.

## <a name="see-also"></a>Consulte Também
 Opções [geral, ambiente, opções da caixa de diálogo](../../ide/reference/general-environment-options-dialog-box.md) [, editor de texto, todos os idiomas, guias](../../ide/reference/options-text-editor-all-languages-tabs.md)
