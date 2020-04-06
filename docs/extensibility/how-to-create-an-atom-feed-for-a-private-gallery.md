---
title: 'Como: Criar um feed de átomos para uma galeria privada | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711007"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Como: Criar um feed de átomo para uma galeria privada
Você pode criar um feed Atom (RSS) para um local de intranet que contém extensões e adicionar o feed a **Extensões e Atualizações** como uma galeria privada. Saiba mais em [Galerias privadas](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Criar um feed átomo
 Para criar um feed do Átomo como uma galeria privada, primeiro você recolhe suas extensões *(.vsix* arquivos) em uma pasta. Você pode organizá-los em subpastas, se quiser. Você também precisará dos seguintes recursos:

- Um arquivo *atom.xml* que disponibiliza as extensões como uma galeria privada. Para obter informações sobre como conectar o arquivo *atom.xml* a **extensões e atualizações,** consulte [Galerias privadas](../extensibility/private-galleries.md).

- Uma pasta que contém quaisquer arquivos de imagem que foram extraídos das extensões (por exemplo, capturas de tela). O arquivo *atom.xml* contém links relativos a essas imagens para que estejam disponíveis em **Extensões e Atualizações**.

  Por exemplo, suponha que você reuniu as duas extensões a seguir em uma pasta:

- *Template_Wizard_239.vsix*, que é um modelo de projeto VSIX vazio.

- *SelectionHighlight.vsix*, que é uma ferramenta para destacar todas as instâncias de uma palavra selecionada.

  O conteúdo do arquivo *atom.xml* se assemelharia ao seguinte exemplo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Observe que as duas tags de link referem-se a capturas de tela na pasta gerada de imagens.

## <a name="see-also"></a>Confira também
- [Galerias privadas](../extensibility/private-galleries.md)
