---
title: Trabalhando com sombreadores
description: Saiba como criar efeitos de sombreador personalizados usando o designer de sombreador baseado em grafo no Visual Studio. Você pode usar sombreadores em seu jogo ou aplicativo baseado em DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bff5aee4337a464498fc4ac027eb05b2da912b61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844886"
---
# <a name="work-with-shaders"></a>Trabalhar com sombreadores

Você pode usar o Designer de Sombreadores baseado em gráfico no Visual Studio para criar efeitos de sombreamento personalizados. Você pode usar esses sombreadores em seu jogo ou aplicativo baseado no DirectX.

## <a name="shaders"></a>Sombreadores

A *sombreador* é um programa de computador que executa cálculos de gráficos — por exemplo, transformações de vértice ou cor do pixel — e normalmente é executado em uma unidade de processamento gráfico (GPU) em vez da CPU. Porque a maioria dos estágios de pipeline gráfica tradicional, função fixa agora são executados por programas de sombreador, você pode usá-los para criar um pipeline é específico para as necessidades de seu aplicativo.

Os tipos mais comuns de sombreadores são *sombreadores de vértices*, que executam cálculos por vértice e substituir a transformação de função fixa e circuitos de iluminação no hardware de gráficos não programável, e *sombreadores de pixel*, que executam cálculos por pixel que determinam a cor de um pixel e substitua os circuitos de combinador de cores de função fixa em hardware de gráficos não programáveis. O hardware de gráficos moderno tornou ainda mais tipos de sombreadores possíveis —*sombreadores convexos*, *sombreadores de domínio* e *sombreadores de geometria* para cálculos de gráficos e *sombreadores de computação* para cálculos não gráficos. Nenhum desses estágios está disponível no hardware de gráficos não programável. Sombreadores foram criados usando uma linguagem semelhante ao assembly fornecido paralela de dados (SIMD) e instruções centrados em gráficos (produto de ponto). Agora, sombreadores normalmente são criados usando linguagens de alto nível, como C como HLSL (linguagem de sombreador de alto nível).

Você pode usar o Designer de Sombreadores criar sombreadores de pixel interativamente em vez de inserir e compilar o código. No Designer de Sombreadores, um sombreador é definido por um número de nós que representam conexões entre nós que representam o fluxo de valores de dados e os resultados intermediários por meio do sombreador e operações e dados. Usando essa abordagem e a visualização em tempo real no Designer de Sombreadores, você pode visualizar a execução do sombreador mais facilmente e variações de sombreador interessante por meio de experimentação "descobrir".

## <a name="dgsl-documents"></a>Documentos DGSL

O Designer de Sombreadores salva sombreadores no formato de linguagem de sombreador gráfico direcionado (DGSL), que é um formato XML que se baseia em direcionadas gráfico Markup Language (DGML). Você pode aplicar os sombreadores DGSL diretamente a modelos 3D no Editor de Modelos. No entanto, antes de usar um sombreador DGSL em seu aplicativo, você deve exportá-lo em um formato que compreende DirectX — por exemplo, HLSL.

Como DGSL é compatível com DGML, você pode usar ferramentas projetadas para analisar documentos DGML para analisar seus sombreadores DGSL. Para saber mais sobre DGML, veja [Noções básicas sobre DGML (Directed Graph Markup Language)](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Designer de sombreador](../designers/shader-designer.md)|Descreve como usar o Designer de Sombreador do Visual Studio para trabalhar com sombreadores.|
|[Nós do designer do sombreador](../designers/shader-designer-nodes.md)|Discute os tipos de nós de Designer de Sombreadores que você pode usar para obter efeitos gráficos.|
|[Exemplos do designer de sombreador](../designers/how-to-create-a-basic-color-shader.md)|Fornece links para tópicos que demonstram como usar o Designer do sombreador para atingir efeitos gráficos comuns.|
