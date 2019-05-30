---
title: Considerações para descarregar e recarregar projetos de aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a45cf72f09ddf4e5ac1d68b59c2b13e64982744
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335549"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregar e recarregar projetos aninhados

Quando você implementa os tipos de projeto aninhado, você deve executar etapas adicionais quando você descarrega e recarregar os projetos. Para notificar os ouvintes de eventos de solução corretamente, você deverá gerar corretamente os `OnBeforeUnloadProject` e `OnAfterLoadProject` eventos.

Um motivo para acionar esses eventos é para controle do código-fonte (SCC). Você não quer SCC excluir os itens do servidor e, em seguida, adicioná-los como *novos* se não houver um `Get` operação do SCC. Nesse caso, um novo arquivo seria carregado fora do SCC. Você teria que descarregar e recarregar todos os arquivos caso eles são diferentes.

Chamadas de controle do código de origem `ReloadItem`. Implemente a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface para chamar `OnBeforeUnloadProject` e `OnAfterLoadProject` para excluir o projeto e recriá-la. Quando você implementa a interface dessa maneira, SCC é informado de que o projeto foi excluído e adicionado novamente temporariamente. Portanto, o SCC não funciona no projeto como se o projeto tiver sido *realmente* excluído e adicionado novamente.

## <a name="reload-projects"></a>Recarregar projetos

Para dar suporte a recarregamento de projetos aninhados, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Em sua implementação de `ReloadItem`, feche os projetos aninhados e, em seguida, recriá-los.

Normalmente quando um projeto é recarregado, o IDE gera o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> eventos. No entanto, para projetos aninhados que são excluídos e recarregados, o projeto pai inicia o processo, não do IDE. Como o projeto pai não geram eventos de solução, e o IDE não possui informações sobre a inicialização do processo, os eventos não são gerados.

Para lidar com esse processo, as chamadas de projeto pai `QueryInterface` sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface. `IVsFireSolutionEvents` tem funções que mandar o IDE para gerar o `OnBeforeUnloadProject` evento para descarregar o projeto aninhado e, em seguida, gerar o `OnAfterLoadProject` evento para recarregar o projeto mesmo.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projetos de aninhamento](../../extensibility/internals/nesting-projects.md)