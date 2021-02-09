---
title: Enumerações C++ no Designer de Classe
description: Saiba mais sobre como Designer de Classe dá suporte a enumeração C++ e tipos de classe enum com escopo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88675bb7593a901805cc156bbb36a2f49d69ec29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852551"
---
# <a name="c-enumerations-in-class-designer"></a>Enumerações C++ no Designer de Classe

O **Designer de classe** dá suporte a `enum` tipos de C++ e com escopo `enum class` . A seguir está um exemplo:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Uma forma de enumeração do C++ em um diagrama de classes parece e funciona como uma forma de estrutura, exceto pelo seguinte: o rótulo exibe **Enum** ou **Enum class**, ele é rosa em vez de azul e tem uma borda colorida nas margens esquerda e superior. As formas de enumeração e formas de estrutura tem cantos quadrados.

Para obter mais informações sobre o uso do tipo `enum`, consulte [Enumerações](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Consulte também

- [Trabalhando com código C++](working-with-visual-cpp-code.md)
- [Enumerações](/cpp/cpp/enumerations-cpp)
