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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592471"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Walkthrough: Depurar uma folha de estilos XSLT

As etapas nessa explicação passo a passo demonstra como usar o depurador XSLT. As etapas incluem variáveis de exibição, pontos de interrupção, e percorrendo o código. O depurador permite que você execute o código uma linha por vez.

Para se preparar para este passo a passos, primeiro copie os dois [arquivos de exemplo](#sample-files) para o computador local. Um é a folha de estilo e um é o arquivo XML que usaremos como entrada para a folha de estilos. Neste tutorial, a folha de estilos que usamos localiza todos os livros cujo custo está abaixo do preço médio do livro.

> [!NOTE]
> O depurador XSLT só está disponível na edição Enterprise do Visual Studio.

## <a name="start-debugging"></a>Iniciar a depuração

1. No menu **arquivo** , escolha **abrir** **arquivo**de > .

2. Localize o arquivo *below-Average. xsl* e escolha **abrir**.

   A folha de estilos é aberta no editor de XML.

3. Clique no botão procurar ( **...** ) no campo de **entrada** da janela Propriedades do documento. (Se a janela **Propriedades** não estiver visível, clique com o botão direito do mouse em qualquer lugar do arquivo aberto no editor e escolha **Propriedades**.)

4. Localize o arquivo *Books. xml* e, em seguida, escolha **abrir**.

   Isso define o arquivo de documento de origem que é usado para a transformação XSLT.

5. Defina um [ponto de interrupção](../debugger/using-breakpoints.md) na linha 12 de *below-Average. xsl*. Você pode fazer isso de várias maneiras:

   - Clique na margem do editor na linha 12.

   - Clique em qualquer lugar na linha 12 e pressione **F9**.

   - Clique com o botão direito do mouse na marca de início `xsl:if` e escolha **ponto de interrupção** > **Inserir ponto de interrupção**.

      ![Inserir ponto de interrupção no arquivo XSL no Visual Studio](media/insert-breakpoint.PNG)

6. Na barra de menus, escolha **XML** > **Iniciar Depuração XSLT** (ou pressione **ALT**+**F5**).

   O processo de depuração é iniciado.

   No editor, o depurador é posicionado no elemento `xsl:if` da folha de estilos. Outro arquivo chamado *below-Average. xml* é aberto no editor; Esse é o arquivo de saída que será preenchido como cada nó no arquivo de entrada *Books. xml* é processado.

   As janelas **automáticos**, **locais**e **inspecionar 1** aparecem na parte inferior da janela do Visual Studio. A janela **locais** exibe todas as variáveis locais e seus valores atuais. Isso inclui variáveis definidos na folha de estilos e também variáveis que o depurador usa para controlar os nós que estão atualmente no contexto.

## <a name="watch-window"></a>Janela de inspeção

Adicionaremos duas variáveis à janela **Watch 1** para que possamos examinar seus valores à medida que o arquivo de entrada for processado. (Você também pode usar a janela **locais** para examinar valores se as variáveis que você deseja observar já estiverem lá.)

1. No menu **depurar** , escolha **Windows** > **assistir** > **Watch 1**.

   A janela **Watch 1** torna-se visível.

2. Digite `$bookAverage` no campo **nome** e pressione **Enter**.

   O valor da variável `$bookAverage` é exibido no campo **valor** .

3. Na próxima linha, digite `self::node()` no campo **nome** e pressione **Enter**.

   `self::node()` é uma expressão XPath que é avaliada como o nó de contexto atual. O valor da expressão XPath de `self::node()` é o primeiro nó de livro. Isso é alterado como nós progredimos com a transformação.

4. Expanda o nó `self::node()` e, em seguida, expanda o valor do nó que é `price`.

   ![janela Inspeção durante a depuração XSLT no Visual Studio](media/xslt-debugging-watch-window.png)

   Você pode ver o valor do preço do livro para o nó do livro atual e compará-lo com o valor `$bookAverage`. Como o preço do livro está abaixo da média, a condição de `xsl:if` deve ter sucesso quando você continua o processo de depuração.

## <a name="step-through-the-code"></a>Percorrer o código

1. Pressione **F5** para continuar.

   Como o primeiro nó de livro satisfez a condição de `xsl:if`, o nó de livro é adicionado ao arquivo de saída *below-Average. xml* . O depurador continuará a ser executado até que está localizado novamente no elemento de `xsl:if` na folha de estilos. O depurador agora está posicionado no segundo nó de livro no arquivo *Books. xml* .

   Na janela **Watch 1** , o valor de `self::node()` muda para o segundo nó de livro. Examinando o valor do elemento de preço, você pode determinar que o preço está acima da média, então a condição de `xsl:if` deve falhar.

2. Pressione **F5** para continuar.

   Como o segundo nó de livro não atende à condição de `xsl:if`, o nó de livro não é adicionado ao arquivo de saída *below-Average. xml* . O depurador continuará a ser executado até ser posicionado novamente no elemento `xsl:if` na folha de estilos. O depurador agora está posicionado no terceiro nó `book` no arquivo *Books. xml* .

   Na janela **Watch 1** , o valor de `self::node()` muda para o terceiro nó de livro. Ao examinar o valor do elemento `price`, você pode determinar que o preço está abaixo da média. A condição de `xsl:if` deve ter sucesso.

3. Pressione **F5** para continuar.

   Como a condição de `xsl:if` foi satisfeita, o terceiro livro é adicionado ao arquivo de saída *below-Average. xml* . Todos os livros no documento XML foram processados e paradas do depurador.

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

## <a name="see-also"></a>Veja também

- [Depuração de XSLT](../xml-tools/debugging-xslt.md)
