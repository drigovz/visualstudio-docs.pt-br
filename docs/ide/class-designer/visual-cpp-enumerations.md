---
title: C++Enumerações no Designer de Classe
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a514d5eb4b7f79e2fd193c79de670b6dd9c14cb5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747986"
---
# <a name="c-enumerations-in-class-designer"></a>C++Enumerações no Designer de Classe

O **Designer de Classe** é compatível com os tipos `enum` e `enum class` no escopo do C++. Veja um exemplo a seguir:

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

- [Trabalhando com C++ código](working-with-visual-cpp-code.md)
- [Enumerações](/cpp/cpp/enumerations-cpp)