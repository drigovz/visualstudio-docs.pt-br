---
title: T4 Diretiva de saída
description: Saiba que, nos modelos de texto do Visual Studio, a diretiva output é usada para definir a extensão de nome de arquivo e a codificação do arquivo transformado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58e7c255d767e9b35764e03a76f9cda516dbe606
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899595"
---
# <a name="t4-output-directive"></a>T4 Diretiva de saída

Nos modelos de texto do Visual Studio, a `output` diretiva é usada para definir a extensão de nome de arquivo e a codificação do arquivo transformado.

 Por exemplo, se o seu projeto do Visual Studio inclui um arquivo de modelo chamado **MyTemplate.tt** que contém a seguinte diretiva:

 `<#@output extension=".cs"#>`

 em seguida, o Visual Studio irá gerar um arquivo chamado **MyTemplate.cs**

 A diretiva de `output` não é necessária em um modelo de texto de tempo de execução (pré-processado). Ao invés disso, o aplicativo obtém a cadeia de caracteres gerada ao chamar `TextTransform()`. Para obter mais informações, consulte [geração de texto em tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Usando a Diretiva de Saída

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Não deverá haver mais de uma diretiva de `output` em cada modelo de texto.

## <a name="extension-attribute"></a>atributo de extensão
 Especifica a extensão do nome de arquivo do arquivo de saída do texto gerado.

 O valor padrão é **. cs**

 Exemplos: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Valores aceitáveis: qualquer extensão de nome de arquivo válida.

## <a name="encoding-attribute"></a>atributo de codificação
 Especifica a codificação usada ao gerar o arquivo de saída. Por exemplo:

 `<#@ output encoding="utf-8"#>`

 O valor padrão é a codificação usada pelo arquivo de modelo de texto.

 Valores aceitáveis: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Padrão do sistema)

 Em geral, é possível usar a cadeia de caracteres do WebName ou o número da CodePage de qualquer uma das codificações retornadas por <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
