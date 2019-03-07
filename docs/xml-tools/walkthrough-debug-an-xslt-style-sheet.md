---
title: Depurar folhas de estilos XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526627"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Passo a passo: Depurar uma folha de estilos XSLT

As etapas nessa explicação passo a passo demonstra como usar o depurador XSLT. As etapas incluem variáveis de exibição, pontos de interrupção, e percorrendo o código. O depurador permite que você execute o código uma linha por vez.

Para preparar para este passo a passo, primeiro copie as duas [arquivos de exemplo](#sample-files) em seu computador local. Uma é a folha de estilos, e um é o arquivo XML que vamos usar como entrada para a folha de estilos. Neste passo a passo, podemos usar a folha de estilos localiza todos os livros cujo custo é o preço médio de livro abaixo.

> [!NOTE]
> O depurador XSLT só está disponível na edição Enterprise do Visual Studio.

## <a name="start-debugging"></a>Iniciar a depuração

1. Dos **arquivo** menu, escolha **abra** > **arquivo**.

2. Localize o *abaixo average.xsl* do arquivo e escolha **abrir**.

   Abre a folha de estilos no editor de XML.

3. Clique no botão Procurar (**...** ) sobre o **entrada** campo da janela de propriedades do documento. (Se o **propriedades** janela não estiver visível, clique com botão direito em qualquer lugar no arquivo aberto no editor e, em seguida, escolha **propriedades**.)

4. Localize o *Books* file e, em seguida, escolha **abrir**.

   Isso define o arquivo de documento de origem que é usado para a transformação XSLT.

5. Definir um [ponto de interrupção](../debugger/using-breakpoints.md) na linha 12 das *abaixo average.xsl*. Você pode fazer isso de várias maneiras:

   - Clique na margem do editor na linha 12.

   - Clique em qualquer lugar na linha 12 e, em seguida, pressione **F9**.

   - Clique com botão direito do `xsl:if` marca de início e, em seguida, escolha **ponto de interrupção** > **Inserir ponto de interrupção**.

      ![Inserir ponto de interrupção no arquivo XSL no Visual Studio](media/insert-breakpoint.PNG)

6. Na barra de menus, escolha **XML** > **iniciar depuração de XSLT** (ou pressione **Alt**+**F5**).

   Inicia o processo de depuração.

   No editor, o depurador é posicionado sobre o `xsl:if` elemento da folha de estilos. Outro arquivo denominado *abaixo average.xml* é aberto no editor; esse é o arquivo de saída será preenchido como cada nó no arquivo de entrada *Books* é processado.

   O **automóveis**, **Locals**, e **inspeção 1** janelas são exibidas na parte inferior da janela do Visual Studio. O **Locals** janela exibe todas as variáveis locais e seus valores atuais. Isso inclui variáveis definidos na folha de estilos e também variáveis que o depurador usa para controlar os nós que estão atualmente no contexto.

## <a name="watch-window"></a>Janela Inspecionar

Vamos adicionar duas variáveis para o **inspeção 1** janela, portanto, podemos examinar seus valores conforme o arquivo de entrada é processado. (Você também pode usar o **Locals** janela para examinar os valores se as variáveis que você deseja assistir já estão lá.)

1. Dos **Debug** menu, escolha **Windows** > **inspeção** > **inspeção 1**.

   O **inspeção 1** janela fica visível.

2. Tipo de `$bookAverage` no **nome** campo e, em seguida, pressione **Enter**.

   O valor da `$bookAverage` variável exibe a **valor** campo.

3. Na próxima linha, digite `self::node()` no **nome** campo e, em seguida, pressione **Enter**.

   `self::node()` é uma expressão XPath que avalia ao nó atual de contexto. O valor da expressão XPath de `self::node()` é o primeiro nó de livro. Isso é alterado como nós progredimos com a transformação.

4. Expanda o `self::node()` nó e, em seguida, expanda o nó que tem o valor é `price`.

   ![Janela de inspeção durante a depuração de XSLT no Visual Studio](media/xslt-debugging-watch-window.png)

   Você pode ver o valor do preço de catálogo para o nó atual do livro e compará-la para o `$bookAverage` valor. Porque o custo de livro está abaixo da média, o `xsl:if` condição deve obterá êxito quando você continuar o processo de depuração.

## <a name="step-through-the-code"></a>Percorrer o código

1. Pressione **F5** para continuar.

   Porque o primeiro nó de livro satisfeita a `xsl:if` condição, o nó de livro é adicionado para o *abaixo average.xml* arquivo de saída. O depurador continuará a ser executado até que está localizado novamente no elemento de `xsl:if` na folha de estilos. O depurador é posicionado agora no segundo nó de livro na *Books* arquivo.

   No **inspecionar 1** janela, o `self::node()` valor muda para o segundo nó de livro. Examinando o valor do elemento de preço, você pode determinar que o preço está acima da média, então a condição de `xsl:if` deve falhar.

2. Pressione **F5** para continuar.

   Porque o segundo nó de livro não atende o `xsl:if` condição, o nó de livro não é adicionado para o *abaixo average.xml* arquivo de saída. O depurador continua sendo executado até que ele está localizado novamente no `xsl:if` elemento na folha de estilos. O depurador é posicionado agora no terceiro `book` nó o *Books* arquivo.

   No **inspecionar 1** janela, o `self::node()` valor muda para o terceiro nó de livro. Examinando o valor da `price` elemento, você pode determinar que o preço está abaixo da média. O `xsl:if` condição deve ser bem-sucedida.

3. Pressione **F5** para continuar.

   Porque o `xsl:if` condição foi atendida, o terceiro livro é adicionado para o *abaixo average.xml* arquivo de saída. Todos os livros no documento XML foram processados e paradas do depurador.

## <a name="sample-files"></a>Arquivos de exemplo

Os seguintes dois arquivos são usados por passo a passo.

### <a name="below-averagexsl"></a>below-average.xsl

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

## <a name="see-also"></a>Consulte também

- [Depuração de XSLT](../xml-tools/debugging-xslt.md)