---
title: Como usar trechos de código XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4a56249c0a87b2516dc233818208f7c7c4b696e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002060"
---
# <a name="how-to-use-xml-snippets"></a>Como: Usar snippets XML

Você pode chamar trechos XML usando dois comandos a seguir no menu de atalho do editor de XML. O **Inserir trecho** comando insere o trecho XML a posição do cursor. O **envolver com** comando encapsula o trecho XML ao redor do texto selecionado. Cada snippets XML designou tipos de snippets. Os tipos de trecho determinam se o trecho de código está disponível com o **Inserir trecho** comando, o **envolver com** , ou ambos.

Depois que o snippet XML foi adicionado ao editor, todos os campos editáveis no snippet estão realçados em amarelo, e o cursor está localizado no primeiro campo editável.

## <a name="insert-snippet"></a>Inserir Snippet

Os procedimentos a seguir descrevem como acessar o **Inserir trecho** comando.

> [!NOTE]
> O **Inserir trecho** comando também está disponível por meio do atalho de teclado (**Ctrl**+**K**, em seguida, **Ctrl** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Para inserir snippets do menu de atalho

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Clique com botão direito e selecione **Inserir trecho de código**.

   Uma lista de snippets disponíveis XML é exibida.

3. Selecione um trecho de lista usando o mouse ou digitando o nome do trecho de código e pressionar **guia** ou **Enter**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Para inserir snippets usando o menu do IntelliSense

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Dos **edite** , aponte para **IntelliSense**e, em seguida, selecione **Inserir trecho de código**.

   Uma lista de snippets disponíveis XML é exibida.

3. Selecione um trecho de lista usando o mouse ou digitando o nome do trecho de código e pressionar **guia** ou **Enter**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Para inserir trechos com a lista de palavras completo do IntelliSense

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Comece a digitar o snippet XML que você deseja adicionar ao seu arquivo. Se o preenchimento automático é ativada, a lista de palavras completo do IntelliSense é exibida. Se não for exibida, pressione **Ctrl**+**espaço** para ativá-lo.

3. Selecione o snippet XML da lista de palavras completo.

4. Pressione **guia**, **guia** para invocar o trecho XML.

> [!NOTE]
> Pode haver casos quando o snippet XML não é chamado. Por exemplo, se você tentar inserir um elemento de `xs:complexType` dentro de um nó de `xs:element` , o editor não gerencia um snippet XML. Quando um elemento de `xs:complexType` é usado dentro de um nó de `xs:element` , não houver nenhum atributo ou subelements necessário, o editor não tem nenhum dados para inserir.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Para inserir snippets usando o nome do atalho

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Tipo `<` no painel do editor.

3. Pressione **Esc** para fechar a lista de palavras completo do IntelliSense.

4. Digite o nome do atalho de trecho e pressione **guia** para invocar o trecho XML.

## <a name="surround-with"></a>Envolver com

Os procedimentos a seguir descrevem como acessar o **envolver com** comando.

> [!NOTE]
> O **envolver com** comando também está disponível por meio do atalho de teclado (**Ctrl**+**K**, em seguida, **Ctrl** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Usar Surround With no menu de contexto

1. Selecione o texto para colocar no editor de XML.

2. Clique com botão direito e selecione **envolver com**.

   Uma lista de bordadura disponíveis com snippets XML é exibida.

3. Selecione um trecho de lista usando o mouse ou digitando o nome do trecho de código e pressionar **guia** ou **Enter**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Usar Surround With no menu IntelliSense

1. Selecione o texto para colocar no editor de XML.

2. Dos **edite** , aponte para **IntelliSense**e, em seguida, selecione **Surround With**.

   Uma lista de bordadura disponíveis com snippets XML é exibida.

3. Selecione um trecho de lista usando o mouse ou digitando o nome do trecho de código e pressionar **guia** ou **Enter**.

## <a name="use-xml-snippets"></a>Usar snippets XML

Uma vez que você escolher um snippet XML, o texto de snippet de código é inserido automaticamente a posição do cursor. Todos os campos editáveis no snippet são realçadas, e o primeiro campo editável é automaticamente selecionado. O campo selecionado é convertido.

Quando um campo é selecionado, você pode digitar um novo valor para o campo. Pressionar **guia** ciclos através dos campos editáveis do trecho; pressionando **Shift**+**guia** percorre-las na ordem inversa. Clicando em um campo colocar o cursor no campo, e clique duas vezes em um campo selecioná-lo. Quando um campo é realçado, uma dica de ferramenta pode ser exibido, oferecendo uma descrição do campo.

Somente a primeira instância de um campo dado é editável. Quando esse campo é realçado, as outras instâncias do campo são descritas. Quando você altera o valor de um campo editável, o campo ele alterado everywhere é usado no snippet.

Pressionar **Enter** ou **Esc** cancela a edição de campos e retorna o editor a normal.

As cores padrão para campos de trecho de código editável podem ser alteradas modificando o **campo de trecho de código** definindo na **fontes e cores** painel da **opções** caixa de diálogo. Para obter mais informações, confira [Como: Alterar fontes e cores no editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Consulte também

- [Trechos de código XML](../xml-tools/xml-snippets.md)
- [Como: Gerar um trecho XML a partir de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Como: Criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md)