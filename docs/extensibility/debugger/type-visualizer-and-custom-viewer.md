---
title: Visualizador de tipo e visualizador personalizado | Microsoft Docs
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
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712462"
---
# <a name="type-visualizer-and-custom-viewer"></a>Digite visualizador e visualizador personalizado
Um visualizador de tipo é um componente que exibe um pedaço de dados em um formato específico. O formato depende inteiramente de quem implementa o visualizador, seja o usuário final ou um fornecedor de visualizadores de terceiros.

 Um visualizador personalizado é a parte de um avaliador de expressão personalizado que exibe um pedaço de dados em um formato específico. Esse formato depende inteiramente do implementador do visualizador personalizado, o que significa que o formato cabe ao implementador do avaliador de expressão (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Suporte para visualizadores de tipo em um avaliador de expressão
 Um EE suporta visualizadores de tipo, suportando um conjunto de interfaces acessíveis a visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). No entanto, o EE não é responsável pela implementação do próprio visualizador de tipo: o EE apenas permite que visualizadores externos tenham acesso às suas informações de tipo. Tais visualizadores podem ser enviados juntamente com o EE e instalados no local apropriado no Visual Studio, fornecidos por outro fornecedor terceirizado ou até mesmo pelo usuário final.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Suporte para espectadores personalizados em um avaliador de expressão
 Um EE também pode suportar visualizadores personalizados nos quais o próprio EE fornece o código para visualização do tipo de dados. Um visualizador personalizado implementa a interface [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) que lida com todas as funções de mostrar os dados em qualquer formato desejado; o espectador tem controle total sobre o display e pode até mesmo deixar os dados serem modificados. Todos os espectadores personalizados fornecidos pelo EE vêm com o EE quando o produto é enviado.

## <a name="see-also"></a>Confira também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
- [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md)
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
