---
title: Diretiva de saída do T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652308"
---
# <a name="t4-output-directive"></a>T4 Diretiva de saída
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em modelos de texto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a diretiva de `output` é usada pare definir a extensão do nome de arquivo e a codificação do arquivo transformado.

 Por exemplo, se seu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeto inclui um arquivo de modelo chamado **MyTemplate.tt** que contém a seguinte diretiva:

 `<#@output extension=".cs"#>`

 em seguida, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] irá gerar um arquivo chamado **MyTemplate.cs**

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
