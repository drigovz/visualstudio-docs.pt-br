---
title: Formatação, XML, Editor de texto, caixa de diálogo Opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 588bf415a801a9244cd9a046e0c503c0b238db58
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417411"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatação, XML, editor de texto, a caixa de diálogo opções
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta caixa de diálogo permite que você especifique as configurações de formatação para o editor XML. Você pode acessar o **opções** caixa de diálogo do **ferramentas** menu.  
  
> [!NOTE]
> Essas configurações estão disponíveis quando você seleciona os **Editor de texto** pasta, o **XML** pasta e, em seguida, o **formatação** opção o **opções** caixa de diálogo.  
  
## <a name="attributes"></a>Atributos  
 **Preservar formatação manual de atributos**  
 Os atributos não são reformatados. Esse é o padrão.  
  
> [!NOTE]
> Se os atributos estão em várias linhas, o editor recua cada linha de atributos para coincidir com o recuo de elemento pai.  
  
 **Alinhar cada atributo em sua própria linha**  
 Alinha os segundos e atributos subsequentes verticalmente para coincidir com o recuo do primeiro atributo. O texto a seguir XML é um exemplo de como os atributos seriam alinhados.  
  
```  
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
 **Conteúdo misturado preserve por padrão**  
 Determina se o editor reformate conteúdo misturado. Por padrão, o editor tenta reformatar conteúdo misturado, a não ser que quando o conteúdo for encontrado em um escopo de `xml:space="preserve"` .  
  
 Se um elemento contém uma mistura de texto e de marcação, os conteúdos são consideradas conteúdo misturado. O código a seguir é um exemplo de um elemento com conteúdo misturado.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Componentes do editor de XML](../xml-tools/xml-editor-components.md)
