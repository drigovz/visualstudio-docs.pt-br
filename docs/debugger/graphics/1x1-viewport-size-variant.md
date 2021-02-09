---
title: Variante de tamanho do visor 1x1 | Microsoft Docs
description: Aplique a variante de tamanho do visor 1x1 para reduzir as dimensões do visor em todos os destinos de renderização para 1x1 pixels.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc96decdc8e61e1d8c1f5b60195d7644222dbd51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874594"
---
# <a name="1x1-viewport-size-variant"></a>Variação de tamanho do visor 1x1
Reduz as dimensões do visor em todos os destinos de renderização para 1 x 1 pixels.

## <a name="interpretation"></a>Interpretação
 Um visor menor reduz o número de pixels que você precisa sombrear. Mas, um visor menor não reduz o número de vértices que você precisa processar. Ao definir as dimensões do visor para 1 × 1, você elimina o sombreamento dos pixels de seu aplicativo.

 Se essa variante mostrar um grande lucro de desempenho, isso pode indicar que seu aplicativo consome muita taxa de preenchimento. Além disso, sua resolução pode ser muito alta para a plataforma de destino ou seu aplicativo pode gastar pixels de sombreamento de tempo significativos que são substituídos posteriormente, também conhecidos como *sobreempates*. Um buffer de quadro menor ou a redução da quantidade de excesso de empates melhorará o desempenho do aplicativo.

## <a name="remarks"></a>Comentários
 As dimensões do visor são redefinidas para 1 × 1 pixel após cada chamada de `ID3D11DeviceContext::OMSetRenderTargets` ou `ID3D11DeviceContext::RSSetViewports`.

## <a name="example"></a>Exemplo
 Essa variante pode ser reproduzida com o seguinte código:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
