---
title: Usar sequências de escape para gerar modelos de modelos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1460b03a027a2b33844edc7d617f8b5f21208772
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594637"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Como gerar modelos a partir de modelos usando sequências de escape
Você pode criar um modelo de texto que cria outro modelo de texto como a saída de texto gerada. Para fazer isso, você deve usar sequências de escape para delinear as marcas de modelo de texto. Se você não usar sequências de escape, o modelo de texto gerado terá um significado predefinido. Para obter mais informações sobre como usar sequências de escape em modelos de texto, consulte [usando sequências de escape em modelos de texto](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Para gerar um modelo de texto de dentro de um modelo de texto

- Use a barra invertida (\\) como um caractere de escape para produzir as marcas de marcação necessárias no modelo de texto para diretivas, instruções, expressões e recursos de classe em um arquivo de modelo de texto separado.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Exemplo
 O exemplo a seguir usa caracteres de escape para produzir um modelo de texto a partir de um modelo de texto. A diretiva `output` define o tipo de arquivo de destino como o tipo de arquivo de modelo de texto (. TT).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 A saída de texto gerada é um modelo de texto.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```
