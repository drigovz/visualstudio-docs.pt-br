---
title: Seletor de snippet de código
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84a93ed9cac1c3f352b3e658f28da4b492612338
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953199"
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