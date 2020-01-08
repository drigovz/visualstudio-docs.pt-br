---
title: C++Estruturas no Designer de Classe
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590678"
---
# <a name="c-structures-in-class-designer"></a>C++estruturas no Designer de Classe

O **Designer de Classe** é compatível com estruturas C++ declaradas com a palavra-chave `struct`. Veja um exemplo a seguir:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Para obter mais informações sobre o uso do tipo `struct`, consulte [struct](/cpp/cpp/struct-cpp).

Uma forma de estrutura C++ em um diagrama de classe parece uma forma de classe e funciona como uma, exceto que o rótulo lê **Struct** e tem cantos quadrados em vez de arredondados.

|Elemento de código|Modo de exibição do Designer de Classe|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Estrutura|

## <a name="see-also"></a>Veja também

- [Trabalhando com C++ código](working-with-visual-cpp-code.md)
- [Classes e Structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
