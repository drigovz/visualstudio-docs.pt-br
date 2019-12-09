---
title: Diretiva de importação T4
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1165a966a532dcb9f07bbc1e46f08a1cb26de161
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748198"
---
# <a name="t4-import-directive"></a>Diretiva de importação T4

Nos blocos de código de um modelo de texto do T4 do Visual Studio, a diretiva `import` permite que você faça referência a elementos em outro namespace sem fornecer um nome totalmente qualificado. É o equivalente de `using` em C# ou `imports` em [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Para obter uma visão geral da escrita de modelos de texto T4, consulte [escrevendo um modelo de texto T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-import-directive"></a>Usando a diretiva de importação

```
<#@ import namespace="namespace" #>
```

 Neste exemplo, o código do modelo pode omitir um namespace explícito para membros de System.IO:

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Importações padrão
 O seguinte namespace é importado automaticamente, para que não seja necessário gravar uma diretiva de importação para ele:

- `System`

  Além disso, se você usar uma diretiva personalizada, o processador de diretriz pode importar alguns namespaces automaticamente.

  Por exemplo, se você gravar modelos para uma linguagem específica do domínio (DSL), você não precisa gravar diretivas de importação para os namespaces a seguir:

- `Microsoft.VisualStudio.Modeling`

- Namespace de sua DSL

## <a name="see-also"></a>Consulte também

- [Diretiva de assembly T4](../modeling/t4-assembly-directive.md)