---
title: Como executar uma transformação XSLT do editor de XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666531"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Como: Executar uma transformação XSLT do editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor XML permite que você associe uma folha de estilos XSLT com um documento XML, execute a transformação, e exibe a saída. A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.

 A propriedade **output** especifica o nome do arquivo para a saída. Se a propriedade de **saída** estiver em branco, um nome de arquivo será gerado no diretório temporário. A extensão de arquivo é baseado no elemento de `xsl:output` na folha de estilos e pode ser .xml, .txt ou .htm.

 Se a propriedade **output** especificar um nome de arquivo com uma extensão. htm ou. html, a saída XSLT será visualizada usando o [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Todas as extensões de arquivo restantes é aberto usando o editor padrão escolhido por [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Por exemplo, se a extensão de arquivo é .xml, o Visual Studio usa o editor XML.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Para executar uma transformação XSLT de um documento XML

1. Abrir um documento XML no editor XML.

2. Associar uma folha de estilos XSLT com o documento XML.

    - Adicione uma instrução de processamento de `xml-stylesheet` para o documento XML. Por exemplo, adicione a seguinte linha `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` ao prólogo do documento.

         - ou -

    - Adicione a folha de estilos XSLT usando a janela **Propriedades** . Na **janela Propriedades**do documento, clique no botão **procurar** do campo **folha** de estilo, selecione a folha de estilos XSLT e clique em **abrir**.

3. Clique no botão **saída de ShowXSL** na barra de ferramentas do editor de **XML** .

    > [!NOTE]
    > Se não houver nenhuma folha de estilos associada com o documento XML, avisos de uma caixa de diálogo você fornecer a folha de estilos ao uso.
    >
    >  A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Para executar uma transformação XSLT de uma folha de estilos XSLT

1. Abra uma folha de estilos XSLT no editor XML.

2. Especifique um documento XML no campo de **entrada** da janela **Propriedades** do documento.

    > [!NOTE]
    > O documento XML é o documento de entrada usado para a transformação. Se um documento não for especificado quando a transformação XSLT for iniciada, a caixa de diálogo **Abrir arquivo** será exibida e você poderá especificar um documento nesse momento.

3. Clique no botão de **saída de imxslt** na barra de ferramentas do **Editor de XML** .

     A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.

### <a name="to-provide-a-different-output-file-name"></a>Para fornecer um nome de arquivo diferente de saída

1. Especifique um nome de arquivo no campo **saída** da janela **Propriedades** do documento.

2. Clique no botão de **saída de imxslt** na barra de ferramentas do **Editor de XML** .

     A saída resultante da transformação XSLT é exibida em uma nova janela de documento e o editor usado na janela de saída depende da extensão de arquivo da sua propriedade de documento de **saída** .

## <a name="see-also"></a>Consulte Também
 [Editor de XML](../xml-tools/xml-editor.md)
