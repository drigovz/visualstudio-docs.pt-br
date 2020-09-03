---
title: Estruturas do C++ no Designer de Classe
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590678"
---
# <a name="c-structures-in-class-designer"></a>Estruturas do C++ no Designer de Classe

**Designer de classe** dá suporte a estruturas C++, que são declaradas com a palavra-chave `struct` . A seguir está um exemplo:

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

## <a name="see-also"></a>Confira também

- [Trabalhando com código C++](working-with-visual-cpp-code.md)
- [Classes e structs](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
