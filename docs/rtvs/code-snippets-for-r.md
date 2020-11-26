---
title: Snippets de código para R
description: Os snippets de código para R no Visual Studio fornecem atalhos para inserir rapidamente os blocos de código de comprimento arbitrário, ajudando a evitar a necessidade de digitar novamente códigos semelhantes.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 31dfa975cea519d4d064856090a265b844f265f6
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189102"
---
# <a name="code-snippets-for-r"></a>Snippets de código para R

Os snippets de código no Visual Studio fornecem atalhos para inserir rapidamente os blocos de código de comprimento arbitrário, ajudando a evitar a necessidade de digitar novamente códigos semelhantes. As RTVS (Ferramentas do R para Visual Studio) adicionam dezenas de snippets do R úteis na coleção do Visual Studio.

Para inserir um trecho de código, digite o nome abreviado do trecho de código (o IntelliSense é fornecido) e pressione **Tab** para inserir.

Alguns exemplos simples:

- digite `=` e, em seguida, pressione Tab e as RTVS o expandirão para o operador de atribuição `<-`.
- digite `>` e, em seguida, pressione Tab e as RTVS o expandirão para o operador de pipe `%>%`.

Snippets podem ser muito mais do que apenas preenchimento de caracteres. Um snippet para ler um arquivo .CSV com a função `read.csv`, por exemplo, pode poupar você de precisar lembrar dos nomes ou parâmetros:

![Animação do uso de um snippet de código para inserir uma chamada de read.csv](media/code-snippet-expansion.gif)

Nesse caso, à medida que você digita `readc`, o IntelliSense exibe uma lista de conclusão. Selecionar essa conclusão na lista suspensa e pressionar **Tab** seleciona `readc` e pressionar **Tab** novamente expande o trecho de código. (Por esse motivo, a expansão de snippet geralmente é considerada como "digitar o snippet e pressionar a tecla Tab duas vezes"). Na maioria dos casos, a primeira Tab preenche a seleção do IntelliSense e a segunda Tab dispara a expansão.

Para ver todos os trechos disponíveis, abra a **Tools**  >  caixa de diálogo **Gerenciador de trechos de código** de ferramentas (**Ctrl** + **K**,**B**) e selecione **R** para **linguagem**. Expanda os grupos e selecione snippets individuais para ver uma descrição e o texto de atalho:

![Caixa de diálogo de snippets de código para R](media/code-snippet-dialog.png)

Para criar snippets de código personalizados, siga as instruções em [Passo a passo: Criar um snippet de código](../ide/walkthrough-creating-a-code-snippet.md). Por fim, um snippet de código é apenas um arquivo XML. Por exemplo, o código a seguir é o snippet de código para a operação de pipe (atalho `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Os arquivos XML de todos os snippets de código são instalados com as RTVS; o campo **Local** no **Gerenciador de snippets de código** fornece o caminho. Você também pode encontrá-los no código-fonte das RTVS no GitHub em [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
