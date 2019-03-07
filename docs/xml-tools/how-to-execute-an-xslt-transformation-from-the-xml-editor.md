---
title: Executar uma transformação XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526367"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Como: Executar uma transformação XSLT do editor XML

O editor XML permite associar uma folha de estilos XSLT com um documento XML, executar a transformação e exibir a saída. A saída resultante de transformação XSLT são exibidas em uma nova janela do documento.

O **saída** propriedade especifica o nome do arquivo para a saída. Se o **saída** propriedade estiver em branco, um nome de arquivo é gerado no diretório temporário. A extensão de arquivo se baseia a `xsl:output` elemento no seu estilo de estilos e pode ser. *XML*,. *txt* ou. *htm*.

Se o **saída** propriedade especifica um nome de arquivo com um. *htm* ou. *HTML* extensão, a saída XSLT é visualizada usando um navegador da web. Todas as outras extensões de arquivo são abertos usando o editor padrão escolhido pelo Visual Studio. Por exemplo, se a extensão de arquivo. *xml*, o Visual Studio usa o editor de XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Executar uma transformação XSLT de um arquivo XML

1. Abra um documento XML no editor de XML.

2. Associar uma folha de estilos XSLT com o documento XML.

    - Adicione uma instrução de processamento de `xml-stylesheet` para o documento XML. Por exemplo, adicione a seguinte linha ao prólogo do documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -ou-

    - Adicione a folha de estilos XSLT usando a **propriedades** janela. Com o arquivo XML aberto no editor, clique com botão direito em qualquer lugar no editor e escolha **propriedades**. No **propriedades** janela, clique no **folha de estilos** do campo e escolha o botão Procurar (...). Selecione a folha de estilos XSLT e, em seguida, escolha **aberto**.

3. Na barra de menus, escolha **XML** > **iniciar sem depuração XSLT**. Ou, pressione **Ctrl**+**Alt**+**F5**.

   A saída de transformação XSLT é exibida em uma nova janela de documento.

   > [!NOTE]
   > Se não houver nenhuma folha de estilos associada com o documento XML, avisos de uma caixa de diálogo você fornecer a folha de estilos ao uso.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Executar uma transformação XSLT de uma folha de estilos XSLT

1. Abra uma folha de estilos XSLT no editor de XML.

2. Especificar um documento XML na **entrada** campo do documento **propriedades** janela.

   > [!NOTE]
   > O documento XML é o documento de entrada usado para a transformação. Se um documento não for especificado quando a transformação XSLT é iniciada, o **abrir arquivo** caixa de diálogo é exibida e você pode especificar um documento no momento.

3. Na barra de menus, escolha **XML** > **iniciar sem depuração XSLT**. Ou, pressione **Ctrl**+**Alt**+**F5**.

   A saída de transformação XSLT é exibida em uma nova janela de documento.

## <a name="specify-an-output-file-name"></a>Especifique um nome de arquivo de saída

Você pode especificar um nome de arquivo de saída para arquivos XML e XSL. Abra o **propriedades** janela e especifique um nome de arquivo na **saída** campo.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)