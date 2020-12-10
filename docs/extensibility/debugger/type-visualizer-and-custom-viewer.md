---
title: Visualizer de tipo e visualizador personalizado | Microsoft Docs
description: Saiba mais sobre os componentes do Visualizador de tipos e os visualizadores personalizados, que exibem dados em um formato específico e as diferenças entre eles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac759dd245da8d803cb943dd6398d9ae642aaf23
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995935"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizer de tipo e visualizador personalizado
Um visualizador de tipo é um componente que exibe uma parte dos dados em um formato específico. O formato é inteiramente o que implementa o visualizador, seja o usuário final ou um fornecedor de visualizadores de terceiros.

 Um visualizador personalizado é a parte de um avaliador de expressão personalizado que exibe uma parte dos dados em um formato específico. Esse formato é inteiramente o implementador do visualizador personalizado, o que significa que o formato é até o implementador do avaliador de expressão (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Suporte para visualizadores de tipo em um avaliador de expressão
 Um EE dá suporte a visualizadores de tipo ao dar suporte a um conjunto de interfaces acessíveis para visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). No entanto, o EE não é responsável por implementar o próprio visualizador de tipo: o EE simplesmente permite que os visualizadores externos acessem suas informações de tipo. Esses visualizadores podem ser enviados junto com o EE e instalados no local apropriado no Visual Studio, fornecidos por outro fornecedor de terceiros ou até mesmo pelo usuário final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Suporte para visualizadores personalizados em um avaliador de expressão
 Um EE também pode dar suporte a visualizadores personalizados nos quais o próprio EE fornece o código para exibir o tipo de dados. Um visualizador personalizado implementa a interface [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , que manipula todas as tarefas de mostrar os dados em qualquer formato desejado; o visualizador tem controle total sobre a exibição e pode até mesmo permitir que os dados sejam modificados. Todos os visualizadores personalizados fornecidos pelo EE vêm com o EE quando o produto é enviado.

## <a name="see-also"></a>Confira também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
- [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md)
- [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
