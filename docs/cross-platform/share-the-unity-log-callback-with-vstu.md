---
title: Compartilhar o retorno de log do Unity com o VSTU | Microsoft Docs
description: Compartilhe o retorno de chamada do log do Unity com aquele que está registrado com Ferramentas do Visual Studio para Unity (VSTU) para transmitir seu console para o Visual Studio.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 88abc27ad757487ae8f65b8bbb66d4dfee9791cc
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039866"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Compartilhar o retorno de log do Unity com o VSTU
As Ferramentas do Visual Studio para Unity registram um retorno de chamada de log do Unity para transmitir seu console para o Visual Studio. Se os scripts do seu editor também registram um retorno de chamada de log do Unity, o retorno de chamada VSTU pode interferir em seu retorno de chamada. Para evitar essa possibilidade, use o evento `VisualStudioIntegration.LogCallback` para cooperar com VSTU.

## <a name="demonstrates"></a>Demonstra
 Como compartilhar o retorno de chamada de log do Unity criado pelas Ferramentas do Visual Studio para Unity.

## <a name="example"></a>Exemplo

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>Confira também
 [Exemplo: geração de arquivo de projeto](../cross-platform/customize-project-files-created-by-vstu.md)
