---
title: Formatação, XML, editor de texto, caixa de diálogo opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670966"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatação, XML, editor de texto, a caixa de diálogo opções
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta caixa de diálogo permite que você especifique as configurações de formatação para o editor XML. Você pode acessar a caixa de diálogo **Opções** no menu **ferramentas** .

> [!NOTE]
> Essas configurações estão disponíveis quando você seleciona a pasta do **Editor de texto** , a pasta **XML** e a opção de **formatação** na caixa de diálogo **Opções** .

## <a name="attributes"></a>Atributos
 **Preservar formatação de atributo manual** Os atributos não são reformatados. Esse é o padrão.

> [!NOTE]
> Se os atributos estão em várias linhas, o editor recua cada linha de atributos para coincidir com o recuo de elemento pai.

 **Alinhar atributos cada em sua própria linha** Alinha o segundo e os atributos subsequentes verticalmente para corresponder ao recuo do primeiro atributo. O texto a seguir XML é um exemplo de como os atributos seriam alinhados.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Reformatação Automática
 **Ao colar da área de transferência** Reformata o texto XML colado da área de transferência.

 **Na conclusão da marca de fim** Reformate o elemento quando a marca de fim é concluída.

## <a name="mixed-content"></a>Conteúdo Misto
 **Preservar conteúdo misto por padrão** Determina se o editor reformata o conteúdo misto. Por padrão, o editor tenta reformatar conteúdo misturado, a não ser que quando o conteúdo for encontrado em um escopo de `xml:space="preserve"` .

 Se um elemento contém uma mistura de texto e de marcação, os conteúdos são consideradas conteúdo misturado. O código a seguir é um exemplo de um elemento com conteúdo misturado.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Consulte também
 [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md) [componentes do editor XML](../xml-tools/xml-editor-components.md)
