---
title: 'Como: usar trechos XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4998fbc530cf4350f4a64b0fd527e0764eafce27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656271"
---
# <a name="how-to-use-xml-snippets"></a>Como: Use snippets XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode chamar snippets XML usando os dois seguintes comandos no menu de atalho do editor XML. O comando **Insert Snippet** insere o trecho XML na posição do cursor. O comando **surround with** encapsula o trecho XML em torno do texto selecionado. Cada snippets XML designou tipos de snippets. Os tipos de trecho determinam se o trecho de código está disponível com o comando **Insert Snippet** , o comando **surround with** ou ambos.

 Depois que o snippet XML foi adicionado ao editor, todos os campos editáveis no snippet estão realçados em amarelo, e o cursor está localizado no primeiro campo editável.

## <a name="insert-snippet"></a>Inserir Snippet
 Os procedimentos a seguir descrevem como acessar o comando **Insert Snippet** .

> [!NOTE]
> O comando **Inserir trecho de código** também está disponível por meio do atalho de teclado (CTRL + K, depois Ctrl + X).

#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Para inserir snippets do menu de atalho

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Clique com o botão direito do mouse e selecione **Inserir trecho**.

     Uma lista de snippets disponíveis XML é exibida.

3. Selecione um snippet de lista usando o mouse, ou digitando o nome do snippet e pressionando TAB ou ENTER.

#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Para inserir snippets usando o menu do IntelliSense

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. No menu **Editar** , aponte para **IntelliSense**e, em seguida, selecione **Inserir trecho de código**.

     Uma lista de snippets disponíveis XML é exibida.

3. Selecione um snippet de lista usando o mouse ou digitando o nome do snippet e pressionando TAB ou ENTRE-O.

#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Para inserir snippets com o IntelliSense concluir a lista de palavras

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Comece a digitar o snippet XML que você deseja adicionar ao seu arquivo. Se o preenchimento automático é ativada, a lista de palavras completo do IntelliSense é exibida. Se não for exibido, para pressionar CTRL+BARRA DE ESPAÇOS para ativar-lo.

3. Selecione o snippet XML da lista de palavras completo.

4. Pressione a tecla TAB, TAB para invocar o snippet XML.

> [!NOTE]
> Pode haver casos quando o snippet XML não é chamado. Por exemplo, se você tentar inserir um elemento de `xs:complexType` dentro de um nó de `xs:element` , o editor não gerencia um snippet XML. Quando um elemento de `xs:complexType` é usado dentro de um nó de `xs:element` , não houver nenhum atributo ou subelements necessário, o editor não tem nenhum dados para inserir.

#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Para inserir snippets usando o nome do atalho

1. Posicionar o cursor onde você deseja inserir o snippet XML.

2. Tipo `<` no painel do editor.

3. Pressione ESC para fechar a lista de palavras completo do IntelliSense.

4. Digite o nome do atalho de snippet, e pressione a tecla TAB para invocar o snippet XML.

## <a name="surround-with"></a>Envolver com
 Os procedimentos a seguir descrevem como acessar o comando **surround with** .

> [!NOTE]
> O comando **surround with** também está disponível por meio do atalho de teclado (CTRL + K, depois Ctrl + S).

#### <a name="to-use-surround-with-from-the-context-menu"></a>Para usar a bordadura com o menu de contexto

1. Selecione o texto para colocar no editor XML.

2. Clique com o botão direito do mouse e selecione **Circundar com**.

     Uma lista de bordadura disponíveis com snippets XML é exibida.

3. Selecione um snippet de lista usando o mouse, ou digitando o nome do snippet e pressionando TAB ou ENTER.

#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Para usar a bordadura com um menu do Intellisense

1. Selecione o texto para colocar no editor XML.

2. No menu **Editar** , aponte para **IntelliSense**e, em seguida, selecione **surround com**.

     Uma lista de bordadura disponíveis com snippets XML é exibida.

3. Selecione um snippet de lista usando o mouse, ou digitando o nome do snippet e pressionando TAB ou ENTER.

## <a name="using-xml-snippets"></a>Usando snippets XML
 Uma vez que você escolher um snippet XML, o texto de snippet de código é inserido automaticamente a posição do cursor. Todos os campos editáveis no snippet são realçadas, e o primeiro campo editável é automaticamente selecionado. O campo selecionado é convertido.

 Quando um campo é selecionado, você pode digitar um novo valor para o campo. Pressione a tecla TAB verificará através dos campos editáveis de snippet; pressionando ciclos de SHIFT+TAB através delass em ordem inversa. Clicando em um campo colocar o cursor no campo, e clique duas vezes em um campo selecioná-lo. Quando um campo é realçado, uma dica de ferramenta pode ser exibido, oferecendo uma descrição do campo.

 Somente a primeira instância de um campo dado é editável. Quando esse campo é realçado, as outras instâncias do campo são descritas. Quando você altera o valor de um campo editável, o campo ele alterado everywhere é usado no snippet.

 Pressionando ENTER ou o ESC cancela a edição de campo e retorna o editor a normal.

 As cores padrão para campos de trecho de código editável podem ser alteradas modificando a configuração do campo de trecho de código no painel **fontes e cores** da caixa de diálogo **Opções** . Para obter mais informações, consulte [como alterar fontes e cores no editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Consulte Também
 [Trechos XML](../xml-tools/xml-snippets.md) [como: gerar um trecho XML de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md) [como criar trechos XML](../xml-tools/how-to-create-xml-snippets.md)
