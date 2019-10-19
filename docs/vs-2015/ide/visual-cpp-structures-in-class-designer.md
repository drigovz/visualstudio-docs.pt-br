---
title: Estruturas do Visual C++ no Designer de Classe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646761"
---
# <a name="visual-c-structures-in-class-designer"></a>Estruturas do Visual C++ no Designer de Classe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Designer de Classe dá suporte a estruturas C++ declaradas com a palavra-chave `struct`. Veja um exemplo a seguir:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Para obter mais informações sobre o uso do tipo `struct`, consulte [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Uma forma de estrutura C++ em um diagrama de classe parece uma forma de classe e funciona como uma, exceto que o rótulo lê **Struct** e tem cantos quadrados em vez de arredondados.

|Elemento de código|Modo de exibição do Designer de Classe|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Estrutura|

## <a name="see-also"></a>Veja também
 [Trabalhando com classes C++ de código Visual (Designer de classe)](../ide/working-with-visual-cpp-code-class-designer.md) [e](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) structs
