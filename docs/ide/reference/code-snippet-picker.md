---
title: Seletor de snippet de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03503c2ea708dd9093e4ee7b3490879724c3f7d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887640"
---
# <a name="code-snippet-picker"></a>Seletor de snippet de código

O Editor de Códigos do Visual Studio fornece um **Seletor de Snippet de Código** que permite inserir blocos de código prontos no documento ativo com alguns cliques do mouse.

O procedimento para exibir o **Seletor de Snippet de Código** varia de acordo com a linguagem que você está usando.

- Visual Basic – clique com o botão direito do mouse no local desejado no Editor de Códigos para exibir o menu de atalho e selecione **Inserir Snippet de Código**.

- C# – clique com o botão direito do mouse no local desejado no Editor de Códigos para exibir o menu de atalho e selecione **Inserir Snippet de Código** ou **Envolver Com**.

- C++ – o **Seletor de Snippet de Código** não está disponível.

- F# – o **Seletor de Snippet de Código** não está disponível.

- JavaScript – clique com o botão direito do mouse no local desejado no Editor de Códigos para exibir o menu de atalho e selecione **Inserir Snippet de Código** ou **Envolver Com**.

- XML – Clique com o botão direito do mouse no local desejado no Editor de Códigos para exibir o menu de atalho e selecione **Inserir Snippet** ou **Envolver com**.

- HTML – Clique com o botão direito do mouse no local desejado no Editor de Códigos para exibir o menu de atalho e selecione **Inserir Snippet** ou **Envolver com**.

- SQL – Clique com o botão direito do mouse no local desejado no Editor de Códigos para exibir o menu de atalho e selecione **Inserir Snippet**.

Na maioria das linguagens de desenvolvimento do Visual Studio, é possível usar o **Gerenciador de Snippets de Código** para adicionar pastas à lista de pastas que o **Seletor de Snippet de Código** examina em busca de arquivos com snippet XML. Você também pode criar seus próprios snippets para adicionar à lista. Para obter mais informações, confira [Passo a passo: Inserindo um snippet de código](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Lista UIElement

Nome do Item

Um campo de texto editável que exibe o nome do item selecionado na **Lista de Itens**. Para executar uma pesquisa incremental do item que você deseja, comece digitando seu nome neste campo. Continue adicionando letras até que o item desejado seja selecionado na **Lista de Itens**.

Lista de Itens

Uma lista de snippets de código disponíveis para inserção ou uma lista de pastas que contêm snippets de código. Para inserir um snippet ou expandir uma pasta, selecione o item desejado e pressione Enter.

## <a name="see-also"></a>Consulte também

- [Melhores práticas para usar snippets de código](../../ide/best-practices-for-using-code-snippets.md)
- [Snippets de Código do Visual Basic IntelliSense](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Configurando identificadores no código](../../ide/setting-bookmarks-in-code.md)
- [Como: Usar snippets de código surround-with](../../ide/how-to-use-surround-with-code-snippets.md)