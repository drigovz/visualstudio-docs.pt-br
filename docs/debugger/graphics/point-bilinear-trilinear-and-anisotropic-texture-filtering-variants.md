---
title: Variantes de filtro de textura ponto/interlinear/trilinear/anisotropic
description: Se o custo de desempenho de uma variante de filtragem de textura ponto, bilinear, trilinear ou anisotropic for significativo, você poderá considerar se seu uso vale o custo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7de150064ee493795bdeed579715dbf1370573a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905068"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Variantes de filtragem de textura de ponto, bilinear, trilinear e anisotrópico
Substitui o modo de filtragem em amostras adequadas de textura.

## <a name="interpretation"></a>Interpretação
 Diferentes métodos de amostragem de textura possuem diferentes custos de desempenho e qualidade de imagem. Na ordem crescente de custo, e de qualidade visual, os modos de filtragem são:

1. Filtragem de ponto (mais barata, pior qualidade visual)

2. Filtragem bilinear

3. Filtragem trilinear

4. Filtragem anisotrópica (mais cara, melhor qualidade visual)

   Se o custo de desempenho de cada variante for significativo ou aumentar com modos de filtragem mais intensos, você pode relacionar o custo à melhor qualidade de imagem. Com base em sua avaliação, você pode aceitar custos de desempenho adicionais para aumentar a qualidade visual ou aceitar uma qualidade visual menor para atingir uma taxa de quadro mais alta ou ganhar mais desempenho, que pode ser usado de outras maneiras.

   Se você achar que o custo de desempenho é insignificante ou permanece estável independentemente do modo de filtragem, por exemplo, quando a GPU de destino possui muito rendimento de sombreador ou largura de banda de memória, considere usar a filtragem anisotrópica para alcançar a melhor qualidade de imagem em seu aplicativo.

## <a name="remarks"></a>Comentários
 Essas variantes substituem os estados de amostra em chamadas para `ID3D11DeviceContext::PSSetSamplers` nas quais o modo de filtragem fornecido pelo aplicativo é um dos seguintes:

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  Na variantes de **Filtragem de Textura de Ponto**, o modo de filtragem fornecido pelo aplicativo é substituído por `D3D11_FILTER_MIN_MAG_MIP_POINT`; na variante de **Filtragem de Textura Bilinear**, ele é substituído por `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; e na variante de **Filtragem de Textura Trilinear**, ele é substituído por `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.

  Na variante de **Filtragem de Textura Anisotrópica**, o modo de filtragem fornecido pelo aplicativo é substituído por `D3D11_FILTER_ANISOTROPIC` e a Anisotropia Máxima é definida como 16.

## <a name="restrictions-and-limitations"></a>Restrições e limitações
 No Direct3D, o nível de recurso 9.1 especifica uma anisotropia máxima de 2x. Como a variante de **Filtragem de Textura Anisotrópica** tenta usar a anisotropia de 16x exclusivamente, a reprodução falha quando a análise de quadros é executada em um dispositivo de nível de recurso 9.1. Dispositivos contemporâneos que são afetados por essa limitação incluem os tablets Windows Surface RT e Surface 2 baseados em ARM. GPUs mais antigas que ainda podem ser encontradas em alguns computadores também podem ser afetadas, mas elas são consideradas bastante obsoletas e cada vez mais incomuns.

## <a name="example-1"></a>Exemplo 1
 A variante de **Filtragem de Textura de Ponto** pode ser reproduzida usando códigos da seguinte forma:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-2"></a>Exemplo 2
 A variante de **Filtragem de Textura Bilinear** pode ser reproduzida usando códigos da seguinte forma:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-3"></a>Exemplo 3
 A variante de **Filtragem de Textura Trilinear** pode ser reproduzida usando códigos da seguinte forma:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-4"></a>Exemplo 4
 A variante de **Filtragem de Textura Anisotrópica** pode ser reproduzida usando códigos da seguinte forma:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
