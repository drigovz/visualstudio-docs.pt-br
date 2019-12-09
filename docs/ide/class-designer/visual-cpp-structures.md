---
title: C++Estruturas no Designer de Classe
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 65fb4738b3124daf48b501c6db416d3803da32ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748914"
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

## <a name="see-also"></a>Consulte também

- [Trabalhando com C++ código](working-with-visual-cpp-code.md)
- [Classes e Structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)