---
title: 'Como: Criar trechos de código XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c676032c2d0bc6c47023c5fd43bc759cccff8de
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925061"
---
# <a name="how-to-create-xml-snippets"></a>Como: Criar snippet XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
O editor XML pode ser usado para criar novos snippets XML. O editor inclui um snippet XML, chamado “Snippets”, que é um snippet de texto constante para criar novos snippets XML.  
  
## <a name="to-create-a-new-xml-snippet"></a>Para criar um novo snippet XML  
 Para criar um novo código XML, o trecho de código crie um novo arquivo XML e usar o **Inserir trecho** recurso.  
  
1.  Sobre o **arquivo** menu, clique em **New** e, em seguida, clique em **arquivo**.  
  
2.  Clique em **arquivo XML** e, em seguida, clique em **abrir**.  
  
3.  Clique com botão direito no painel do editor e selecione **Inserir trecho de código**.  
  
4.  Selecione **trecho** na lista e pressione ENTER.  
  
5.  Faça as alterações para o novo snippet.  
  
6.  Dos **arquivo** menu, selecione **salvar XMLFile**.  
  
     O **salvar arquivo como** caixa de diálogo é exibida.  
  
7.  Insira o nome para o novo trecho e selecione **arquivos de trecho** da **Salvar como tipo** janela suspensa.  
  
8.  Use o **salvar no** lista suspensa para alterar o local do arquivo para a pasta de trechos de XML Snippets\XML\My 2005\Code Meus Documentos\Visual Studio e, em seguida, pressione **salvar**.  
  
## <a name="snippet-description"></a>Descrição de snippet  
 Esta seção descreve alguns dos elementos-chave no snippet de texto constante. Para obter mais informações sobre os elementos de esquema usados por trechos XML, consulte [referência de esquema de trechos de código](../ide/code-snippets-schema-reference.md).  
  
### <a name="snippettype-element"></a>Elemento SnippetType  
 Suporte do editor dois tipos de snippet:  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 O `Expansion` tipo determina se o trecho aparece quando você chama o **Inserir trecho** comando. O `SurroundsWith` tipo determina se o trecho aparece quando você chama o **Bordadura com** comando.  
  
### <a name="code-element"></a>Elemento Code  
 O elemento de `Code` define o texto XML que será inserido quando o snippet é chamado.  
  
> [!NOTE]
>  O texto de snippet XML deve ser incluído em uma seção de `<![CDATA[...]]>` .  
  
 O seguinte é o elemento de `Code` que é criado pelo snippet de texto constante.  
  
```  
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```  
  
 O elemento de `Code` inclui três variáveis.  
  
- $name$ variável é definido pelo usuário. Cria um elemento de `name` , que tem um valor editável que usa padrão “para nomear”. As variáveis definidas pelo usuário são definidos usando o elemento de `Literal` .  
  
- $selected$ é uma variável predefinido. Representa o texto que foi selecionado no editor XML antes de chamar o snippet. O posicionamento dessa variável determina onde o texto selecionado aparece no snippet de código que circunda a seleção.  
  
- $end$ é uma variável predefinido. Quando o usuário pressiona ENTER para concluir editar os campos de snippet de código, essa variável determina onde ao acento circunflexo (^) é movido.  
  
  O elemento acima de `Code` insira o seguinte texto XML:  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 O valor do elemento de nome é marcado como uma região editável.  
  
### <a name="literal-element"></a>Elemento Literal  
 O elemento de `Literal` é usado para identificar o texto de substituição que pode ser personalizada depois que é inserido no arquivo. Por exemplo, cadeias de caracteres literais, os valores numéricos, e alguns nomes de variável podem ser declarados como literais. Você pode definir qualquer número do snippet em literais XML e você pode referir-lhes várias vezes dentro de snippet. O código a seguir é um exemplo de um elemento de `Literal` que define um variável de $name$ cujo valor padrão é “nome”.  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 Literais também podem se referir funções. O Editor XML inclui uma função chamada **LookupPrefix**. O **LookupPrefix** função procura o determinado URI de namespace do local no documento XML que este trecho de código é invocado do e retorna o prefixo de namespace é definido para esse namespace, se houver, e ele inclui os dois-pontos (:) Esse nome. A seguir está um exemplo de uma `Literal` elemento que usa o **LookupPrefix** função.  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 A variável de $prefix$ pode então ser usado em qualquer lugar no seu snippet XML.  
  
## <a name="see-also"></a>Consulte também  
 [Trechos de código XML](../xml-tools/xml-snippets.md)   
 [Como: Usar trechos de código XML](../xml-tools/how-to-use-xml-snippets.md)   
 [Como: gerar um snippet de XML de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
