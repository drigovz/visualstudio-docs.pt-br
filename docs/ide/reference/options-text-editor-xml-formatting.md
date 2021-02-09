---
title: Opções, Editor de texto, XML, Formatação
description: Saiba como usar a página formatação na seção XML para para especificar como os elementos e atributos são formatados em seus documentos XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: b5e3674c955b229c4c517db5d1dab3d36830da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932313"
---
# <a name="options-text-editor-xml-formatting"></a>Opções, Editor de texto, XML, Formatação

Use a página de opções de **Formatação** para especificar como elementos e atributos são formatados nos documentos XML. Para acessar opções de formatação XML, escolha **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **XML** e, em seguida, escolha **formatação**.

## <a name="attributes"></a>Atributos

**Preservar formatação manual de atributos**

Não reformate os atributos. Esta é a configuração padrão.

> [!NOTE]
> Se os atributos estiverem em linhas múltiplas, o editor recua cada linha de atributos para corresponder ao recuo do elemento pai.

**Alinhar cada atributo em uma linha separada**

Alinha o segundo e os atributos subsequentes verticalmente para corresponder ao recuo do primeiro atributo. O texto XML a seguir é um exemplo de como os atributos seriam alinhados:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Reformatação Automática

**Ao colar da área de transferência**

Reformata o texto XML colado da área de transferência.

**Ao concluir a marca final**

Reformata o elemento quando a marca final é concluída.

## <a name="mixed-content"></a>Conteúdo Misto

**Formatar conteúdo misto por padrão.**

Tenta reformatar conteúdo misto, exceto quando o conteúdo encontra-se em um escopo `xml:space="preserve"`. Esta é a configuração padrão.

Se um elemento contiver uma mistura de texto e marcação, os conteúdos serão considerados de conteúdo misto. A seguir há um exemplo de um elemento com conteúdo misto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Consulte também

- [Opções de XML – Diversos](options-text-editor-xml-miscellaneous.md)
- [Ferramentas XML no Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
