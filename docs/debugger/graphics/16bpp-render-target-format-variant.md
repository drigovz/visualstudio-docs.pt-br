---
title: Variante de formato de destino de renderização 16bpp | Microsoft Docs
description: Aplique a variante de formato de destino de renderização de 16 bits por pixel (BPP) definindo o formato de pixel como DXGI_FORMAT_B5G6R5_UNORM para todos os destinos de renderização e buffers de fundo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa73637244469d781ac77acba362886b5656f8d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728038"
---
# <a name="16-bpp-render-target-format-variant"></a>Variante de formato de destino de renderização de 16 BPP
Define o formato de pixel como DXGI_FORMAT_B5G6R5_UNORM para todos os destinos de renderização e buffers de fundo.

## <a name="interpretation"></a>Interpretação
 Um destino de renderização ou um buffer de fundo geralmente usa um formato de 32 bpp (32 bits por pixel), como B8G8R8A8_UNORM. os formatos 32-bpp podem consumir uma grande quantidade de largura de banda de memória. Como o formato de B5G6R5_UNORM é um formato de 16-bpp que é metade do tamanho dos formatos 32-bpp, usá-lo pode aliviar a pressão na largura de banda da memória, mas ao custo da fidelidade de cor reduzida.

 Se essa variante tiver um ganho de desempenho considerável, é provável que o aplicativo consuma muita largura de banda da memória. Você pode obter uma melhoria significativa no desempenho, especialmente quando o quadro com perfil tem uma quantidade significativa de sobreempates ou de mistura de alfa.

Um formato de destino de renderização de 16-bpp pode reduzir a banda de memória com uso quando o aplicativo tem as seguintes condições:
- Não requer reprodução de cores de alta fidelidade.
- Não requer um canal alfa.
- Geralmente não tem gradientes suaves (que são suscetíveis a artefatos de faixa sob fidelidade de cor reduzida).

Outras estratégias para reduzir a largura de banda da memória incluem:
- Reduza a quantidade de excesso de empates ou de mistura de alfa.
- Reduza as dimensões do buffer de quadros.
- Reduza dimensões de recursos de textura.
- Reduza a compactação de recursos de textura.

Como sempre, você precisa levar em consideração as concessões em termos de qualidade de imagem que acompanham todas essas otimizações.

Os aplicativos que fazem parte de uma cadeia de permuta têm um formato de buffer de fundo (DXGI_FORMAT_B5G6R5_UNORM) que não dá suporte a 16 BPP. Essas cadeias de permuta são criadas usando o `D3D11CreateDeviceAndSwapChain` ou o `IDXGIFactory::CreateSwapChain` . Para contornar essa limitação, execute as seguintes etapas:
1. Crie um B5G6R5_UNORM formato de renderização de destino usando `CreateTexture2D` e renderizar para esse destino.
2. Copie o destino de renderização para o BackBuffer de cadeia de permuta desenhando um quádruplo de tela inteira com o destino de renderização como sua textura de origem.
3. Chame presente na sua cadeia de permuta.

   Se essa estratégia salvar mais largura de banda do que é consumida copiando o destino de renderização para o BackBuffer de cadeia de permuta, o desempenho de renderização será melhorado.

   As arquiteturas de GPU que usam técnicas de renderização de ladrilhos podem ver benefícios de desempenho significativos usando um formato de buffer de quadro de 16 BPP. Essa melhoria ocorre porque uma parte maior do buffer de quadro pode se ajustar ao cache de buffer de quadro local de cada bloco. As arquiteturas de renderização lado a lado podem ser encontradas em GPUs de dispositivos móveis e tablet. Elas raramente são encontradas em outros tipos de dispositivos.

## <a name="remarks"></a>Comentários
 O formato do destino de renderização é redefinido como DXGI_FORMAT_B5G6R5_UNORM em todas as chamadas de `ID3D11Device::CreateTexture2D` que criam um destino de renderização. O formato é substituído especificamente quando o objeto D3D11_TEXTURE2D_DESC apresentado a pDesc descreve um destino de renderização, ou seja:

- O membro BindFlags tem o sinalizador D3D11_BIND_REDNER_TARGET definido.

- O membro BindFlags tem o sinalizador D3D11_BIND_DEPTH_STENCIL desmarcado.

- O membro Uso está definido como D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restrições e limitações
 Como o formato B5G6R5 não tem um canal alfa, o conteúdo alfa não é preservado por essa variante. Se a renderização do aplicativo necessitar de um canal alfa no destino de renderização, você não poderá simplesmente alternar para o formato B5G6R5.

## <a name="example"></a>Exemplo
 A variante de **formato de destino de renderização de 16 bpp** pode ser reproduzida para destinos de renderização criados usando um `CreateTexture2D` código como este:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
