---
title: Opções, Editor de texto, XML, Formatação
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1af8ff6f085d744cb58cb3844fced18d3e484494
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673192"
---
# <a name="options-text-editor-xml-formatting"></a>Opções, Editor de texto, XML, Formatação
Use a página de propriedades **Formatação** para especificar como elementos e atributos são formatados nos documentos XML. Para abrir a caixa de diálogo **Opções**, clique no menu **Ferramentas** e clique em **Opções**. Para acessar a página de propriedades **Formatação**, expanda o nó **Editor de texto** > **XML** > **Formatação**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="attributes"></a>Atributos  
**Preservar formatação manual de atributos**  
Não reformate os atributos. Essa é a configuração padrão.  
  
> [!NOTE]  
>  Se os atributos estão em várias linhas, o editor recua cada linha de atributos para coincidir com o recuo de elemento pai.  
  
**Alinhar cada atributo em uma linha separada**  
Alinhe o segundo atributo e os subsequentes verticalmente para coincidir com o recuo do primeiro atributo. O texto a seguir XML é um exemplo de como os atributos seriam alinhados.  
  
```xml
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
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
\</dir>  
```  
## <a name="see-also"></a>Consulte também
- [Como criar documentação XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Geração de código](../code-generation-in-visual-studio.md)
  
