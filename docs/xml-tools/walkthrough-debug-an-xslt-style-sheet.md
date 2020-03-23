---
title: Depurar folhas de estilo XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301716"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Passo a passo: Depurar uma folha de estilos XSLT

As etapas nessa explicação passo a passo demonstra como usar o depurador XSLT. As etapas incluem variáveis de exibição, pontos de interrupção, e percorrendo o código. O depurador permite que você execute uma linha de código de cada vez.

Para se preparar para este passo a passo, primeiro copie os dois [arquivos de amostra](#sample-files) para o seu computador local. Uma é a folha de estilos, e uma é o arquivo XML que usaremos como entrada para a folha de estilos. Neste passo a passo, a folha de estilo que usamos encontra todos os livros cujo custo está abaixo do preço médio do livro.

> [!NOTE]
> O depurador XSLT só está disponível na edição Enterprise do Visual Studio.

## <a name="start-debugging"></a>Iniciar a depuração

1. No menu **Arquivo,** escolha **Abrir** > **arquivo**.

2. Localize o arquivo *abaixo da média.xsl* e escolha **Abrir**.

   A folha de estilo é aberta no editor XML.

3. Clique no botão de navegação **(...**) no campo **entrada** da janela propriedades do documento. (Se a janela **Propriedades** não estiver visível, clique com o botão direito do mouse em qualquer lugar no arquivo aberto no editor e, em seguida, escolha **Propriedades**.)

4. Localize o arquivo *books.xml* e escolha **Abrir**.

   Isso define o arquivo de documento de origem usado para a transformação XSLT.

5. Defina um [ponto de breakpoint](../debugger/using-breakpoints.md) na linha 12 de abaixo da *média.xsl*. Você pode fazer isso de várias maneiras:

   - Clique na margem do editor na linha 12.

   - Clique em qualquer lugar na linha 12 e, em seguida, pressione **F9**.

   - Clique com `xsl:if` o botão direito do mouse na tag inicial e, em seguida, escolha **Breakpoint** > **Insert Breakpoint**.

      ![Inserir ponto de ruptura no arquivo XSL no Visual Studio](media/insert-breakpoint.PNG)

6. Na barra de menu, escolha **XML** > **Start XSLT Debugging** (ou, pressione **Alt**+**F5**).

   O processo de depuração começa.

   No editor, o depurador é `xsl:if` posicionado sobre o elemento da folha de estilos. Outro arquivo nomeado *abaixo da média.xml* é aberto no editor; este é o arquivo de saída que será preenchido à medida que cada nó no arquivo de entrada *books.xml* é processado.

   As **janelas Autos**, **Locals**e **Watch 1** aparecem na parte inferior da janela do Visual Studio. A janela **Locals** exibe todas as variáveis locais e seus valores atuais. Isso inclui variáveis definidos na folha de estilos e também variáveis que o depurador usa para controlar os nós que estão atualmente no contexto.

## <a name="watch-window"></a>Janela Inspecionar

Vamos adicionar duas variáveis à janela **do Relógio 1** para que possamos examinar seus valores à medida que o arquivo de entrada é processado. (Você também pode usar a janela **Locais** para examinar valores se as variáveis que você deseja assistir já estiverem lá.)

1. No menu **Debug,** escolha **o Windows** > **Watch** > Watch**1**.

   A janela **do Relógio 1** torna-se visível.

2. Digite `$bookAverage` o **campo Nome** e, em seguida, **pressione Enter**.

   O valor `$bookAverage` da variável é exibido no campo **Valor.**

3. Na próxima linha, `self::node()` digite no campo **Nome** e, em seguida, **pressione Enter**.

   `self::node()`é uma expressão XPath que avalia o nó de contexto atual. O valor da expressão XPath de `self::node()` é o primeiro nó de livro. Isso é alterado como nós progredimos com a transformação.

4. Expanda `self::node()` o nó e, em seguida, expanda o valor `price`do nó.

   ![Janela de relógio durante a depuração xslt no Visual Studio](media/xslt-debugging-watch-window.png)

   Você pode ver o valor do preço do livro para `$bookAverage` o nó do livro atual e compará-lo com o valor. Como o preço do livro `xsl:if` está abaixo da média, a condição deve ter sucesso quando você continuar o processo de depuração.

## <a name="step-through-the-code"></a>Passe o código

1. Pressione **F5** para continuar.

   Como o primeiro nó `xsl:if` do livro satisfez a condição, o nó do livro é adicionado ao arquivo de saída abaixo da *média.xml.* O depurador continuará a ser executado até que está localizado novamente no elemento de `xsl:if` na folha de estilos. O depurador está agora posicionado no segundo nó do livro no arquivo *books.xml.*

   Na janela **Relógio 1,** o `self::node()` valor muda para o segundo nó do livro. Examinando o valor do elemento de preço, você pode determinar que o preço está acima da média, então a condição de `xsl:if` deve falhar.

2. Pressione **F5** para continuar.

   Como o segundo nó do `xsl:if` livro não atende à condição, o nó do livro não é adicionado ao arquivo de saída abaixo da *média.xml.* O depurador continua a ser executado até que `xsl:if` esteja posicionado novamente sobre o elemento na folha de estilos. O depurador está agora posicionado `book` no terceiro nó no arquivo *books.xml.*

   Na janela **Relógio 1,** o `self::node()` valor muda para o nó do terceiro livro. Ao examinar o valor `price` do elemento, você pode determinar que o preço está abaixo da média. A `xsl:if` condição deve ter sucesso.

3. Pressione **F5** para continuar.

   Como `xsl:if` a condição foi satisfeita, o terceiro livro é adicionado ao arquivo de saída abaixo da *média.xml.* Todos os livros no documento XML foram processados e paradas do depurador.

## <a name="sample-files"></a>Arquivos de exemplo

Os seguintes dois arquivos são usados por passo a passo.

### <a name="below-averagexsl"></a>abaixo da média.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Confira também

- [Depuração de XSLT](../xml-tools/debugging-xslt.md)
