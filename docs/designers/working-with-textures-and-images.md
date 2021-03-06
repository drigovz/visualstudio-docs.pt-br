---
title: Trabalhando com texturas e imagens
description: Aprenda a usar o editor de imagem no Visual Studio para criar e modificar texturas e imagens em formatos como aqueles usados no desenvolvimento de aplicativos DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21d3b402bbffd9528755098131ff9ed1ee636906
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908149"
---
# <a name="work-with-textures-and-images"></a>Trabalhar com texturas e imagens

Você pode usar o Editor de Imagens no Visual Studio para criar e modificar imagens e texturas. O Editor de Imagens dá suporte aos formatos avançados de textura e imagens como aqueles que são usados no desenvolvimento de aplicativos do DirectX.

> [!NOTE]
> O Editor de Imagens não dá suporte a imagens com poucas cores como ícones ou cursores. Para criar ou modificar esses tipos de imagens, use o [Editor de Imagens para ícones (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Texturas e imagens

Texturas e imagens são, em um nível básico, apenas tabelas de dados que são usadas para fornecer detalhes visuais em aplicativos de gráficos. O tipo de detalhe que uma imagem ou textura fornece depende de como ela é usada, mas amostras de cores, valores de alfa (transparência), normais da superfície e valores de altura são exemplos comuns. A principal diferença entre uma textura e uma imagem é que uma textura deve ser usada em conjunto com uma representação de forma — normalmente, um modelo 3D — para expressar uma cena ou objeto completo, mas uma imagem normalmente é uma representação independente do objeto ou cena.

Qualquer textura pode ser codificada e compactada em várias maneiras ortogonais para o tipo de dados que contém uma textura ou para a dimensionalidade ou "forma" da textura. No entanto, os diferentes métodos de compactação e codificação produzem resultados melhores para diferentes tipos de dados.

Você pode usar o Editor de Imagens para criar e modificar texturas e imagens de maneiras semelhantes a outros editores de imagem. O Editor de Imagens também fornece mapeamento MIP e outros recursos para uso com elementos gráficos 3D e é compatível com muitos dos formatos de textura altamente compactados e acelerados por hardware compatíveis com o DirectX.

Os tipos comuns de texturas incluem:

### <a name="texture-maps"></a>Mapas de textura

Os mapas de textura contêm valores de cor que são organizados como matrizes uni, bi e tridimensionais. Eles são usados para fornecer detalhes de cor no objeto afetado. Cores normalmente são codificadas usando os canais de cor RGB (vermelho, verde, azul) e podem incluir um quarto canal, alfa, que representa a transparência. As cores podem ser codificadas em outro esquema de cores, o que é menos comum ou o quarto canal pode conter dados que não são alfa — por exemplo, a altura.

### <a name="normal-maps"></a>Mapas normais

Os mapas normais contêm normais da superfície. Eles são usados para fornecer detalhes de iluminação no objeto afetado. Os normais são usualmente codificados usando os componentes de cor vermelho, verde e azul para armazenar as dimensões x, y e z do vetor. No entanto, existem outras codificações — por exemplo, codificações baseadas em coordenadas polares.

### <a name="height-maps"></a>Mapas de altura

Os mapas de altura contêm dados de campo de altura. Eles são usados para fornecer um formulário de detalhe geométrico no objeto afetado — usando o código do sombreador para calcular o efeito desejado — ou para fornecer pontos de dados para fins como geração de terreno. Os valores de altura normalmente são codificados usando um canal em uma textura.

### <a name="cube-maps"></a>Mapas de cubo

Os mapas de cubo podem conter diferentes tipos de dados — por exemplo, cores ou normais — mas são organizados como seis texturas nas faces de um cubo. Por causa disso, os mapas de cubo não são amostrados fornecendo as coordenadas de textura, mas fornecendo um vetor cuja origem é o centro do cubo. O exemplo é capturado no ponto em que o vetor cruza o cubo. Os mapas de cubo são usados para fornecer uma aproximação do ambiente que pode ser usado para calcular os reflexos — isso é conhecido como *mapeamento de ambiente* — ou para fornecer textura a objetos esféricos com menos distorção do que as texturas básicas e bidimensionais podem fornecer.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Editor de imagem](../designers/image-editor.md)|Descreve como usar o Editor de Imagens para trabalhar com texturas e imagens.|
|[Exemplos do editor de imagem](../designers/how-to-create-a-basic-texture.md)|Fornece links para tópicos que demonstram como usar o Editor de Imagens para executar tarefas de processamento de imagens comuns.|
