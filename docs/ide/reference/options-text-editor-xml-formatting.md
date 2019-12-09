---
title: Opções, Editor de texto, XML, Formatação
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ccd5fdee974e7222d1009b508b7ef90758fafcb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666600"
---
# <a name="options-text-editor-xml-formatting"></a>Opções, Editor de texto, XML, Formatação

Use a página de opções de **Formatação** para especificar como elementos e atributos são formatados nos documentos XML. Para acessar as opções de formatação de XML, escolha **Ferramentas** > **Opções** > **Editor de texto** > **XML** e, em seguida, escolha **Formatação**.

## <a name="attributes"></a>Atributos

**Preservar formatação manual de atributos**

Não reformate os atributos. Essa é a configuração padrão.

> [!NOTE]
> Se os atributos estão em várias linhas, o editor recua cada linha de atributos para coincidir com o recuo de elemento pai.

**Alinhar cada atributo em uma linha separada**

Alinhe o segundo atributo e os subsequentes verticalmente para coincidir com o recuo do primeiro atributo. O texto XML a seguir é um exemplo de como os atributos seriam alinhados:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Reformatação Automática

**Ao colar da área de transferência**

Reformatar o texto XML colado da área de transferência.

**Na conclusão de marca de fim**

Reformatar o elemento quando a marca de fim é concluída.

## <a name="mixed-content"></a>Conteúdo Misto

**Formatar conteúdo misto por padrão.**

Tente reformatar o conteúdo misto, exceto quando o conteúdo é encontrado em um escopo de `xml:space="preserve"`. Essa é a configuração padrão.

Se um elemento contém uma mistura de texto e de marcação, os conteúdos são consideradas conteúdo misturado. Veja a seguir um exemplo de um elemento com conteúdo misto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Consulte também

- [Opções de XML – Diversos](options-text-editor-xml-miscellaneous.md)
- [Ferramentas XML no Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)