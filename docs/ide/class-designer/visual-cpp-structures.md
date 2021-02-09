---
title: Estruturas do C++ no Designer de Classe
description: Saiba mais sobre como Designer de Classe dá suporte a estruturas C++ declaradas com a estrutura de palavras-chave.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca35f9e1c3c1340330ddbbe36ede540fe1e547d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879950"
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
