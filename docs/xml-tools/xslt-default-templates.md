---
title: Modelos de opção XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2910a9f81a8bf4bf1e5f25245ad9a3b02adffe1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807693"
---
# <a name="xslt-default-templates"></a>Modelos padrão XSLT

Um modelo padrão será usado durante XSLT que processa quando não há nenhuma regra explícita modelo correspondente da folha de estilos. O modelo padrão, também conhecido como regra de modelo interno, é definido na seção 5,8 de recomendação W3C XSLT 1,0. O modelo padrão permite que o processador XSLT processe um nó, mesmo que não haja nenhuma regra explícita de modelo que corresponde a ele. Entretanto, porque a regra de modelo interno não é explicitamente definida na folha de estilos, isso pode levar a resultados inesperados ou confundindo de transformação XSLT.

O depurador XSLT agora exibe o código de modelos de opção XSLT. Quando você percorre uma transformação XSLT, se um modelo padrão é usado, o depurador exibe o modelo padrão em uma janela. Isso permite que você percorrer o código de modelo padrão e os pontos de interrupção em suas declarações.

## <a name="see-also"></a>Consulte também

- [Depuração de XSLT](../xml-tools/debugging-xslt.md)