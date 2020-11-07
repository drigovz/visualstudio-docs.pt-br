---
title: Como personalizar os arquivos de projeto criados por VSTU | Microsoft Docs
description: Saiba como personalizar arquivos de projeto criados pelo Ferramentas do Visual Studio para Unity (VSTU). Examine um exemplo de código C#.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 071dc7a9f12dcfeb5fff9e59bbbf34dc64f61cf5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341506"
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizar arquivos de projeto criados pelo VSTU
As ferramentas do Visual Studio para Unity fornecem um retorno de chamada de estilo Unity durante a geração do arquivo de projeto. Registre com o evento `VisualStudioIntegration.ProjectFileGeneration` para modificar o arquivo de projeto sempre que ele for gerado novamente.

## <a name="demonstrates"></a>Demonstra
 Como personalizar os arquivos de projeto do Visual Studio gerados pelas Ferramentas do Visual Studio para Unity.

## <a name="example"></a>Exemplo

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>Confira também
 [Exemplo: retorno de chamada de log](/cross-platform/share-the-unity-log-callback-with-vstu.md)
