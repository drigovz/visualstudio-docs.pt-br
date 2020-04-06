---
title: Considerações para descarregar e recarregar projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709299"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregar e recarregar projetos aninhados

Ao implementar tipos de projeto aninhados, você deve executar etapas adicionais ao descarregar e recarregar os projetos. Para notificar corretamente os ouvintes para eventos `OnBeforeUnloadProject` `OnAfterLoadProject` de solução, você deve levantar corretamente os eventos.

Uma das razões para levantar esses eventos é o controle de código fonte (CCS). Você não quer que o SCC exclua os itens do *new* servidor e, em `Get` seguida, adicione-os de volta como novos se houver uma operação do SCC. Nesse caso, um novo arquivo seria carregado fora do CCS. Você teria que descarregar e recarregar todos os arquivos no caso de eles serem diferentes.

Chamadas de `ReloadItem`controle de código fonte . Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> a `OnBeforeUnloadProject` interface `OnAfterLoadProject` para chamar e excluir o projeto e recriá-lo. Quando você implementa a interface desta forma, o SCC é informado de que o projeto foi temporariamente excluído e adicionado novamente. Portanto, o SCC não opera no projeto como se o projeto fosse *realmente* excluído e readicionado.

## <a name="reload-projects"></a>Projetos de recarga

Para suportar a recarga de projetos <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> aninhados, você implementa o método. Na sua `ReloadItem`implementação, você fecha os projetos aninhados e depois os recria.

Normalmente, quando um projeto é recarregado, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> o IDE levanta os eventos. No entanto, para projetos aninhados que são excluídos e recarregados, o projeto pai inicia o processo, não o IDE. Como o projeto pai não levanta eventos de solução, e o IDE não tem informações sobre a inicialização do processo, os eventos não são levantados.

Para lidar com esse processo, o projeto pai solicita `QueryInterface` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface. `IVsFireSolutionEvents`tem funções que dizem ao `OnBeforeUnloadProject` IDE para levantar o evento para `OnAfterLoadProject` descarregar o projeto aninhado e, em seguida, levantar o evento para recarregar o mesmo projeto.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projetos nest](../../extensibility/internals/nesting-projects.md)
