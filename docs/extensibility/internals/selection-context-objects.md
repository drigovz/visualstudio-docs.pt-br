---
title: Objetos de contexto de seleção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705504"
---
# <a name="selection-context-objects"></a>Objetos de contexto da seleção
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) usa um objeto de contexto de seleção global para determinar o que deve ser exibido no IDE. Cada janela no IDE pode ter seu próprio objeto de contexto de seleção empurrado para o contexto global de seleção. O IDE atualiza o contexto de seleção global com valores de uma janela quando essa janela tem o foco. Para obter mais informações, consulte [Feedback ao Usuário](../../extensibility/internals/feedback-to-the-user.md).

 Cada quadro de janela ou site no <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE tem um serviço chamado . O objeto criado pelo seu VSPackage que está situado `QueryService` no quadro da <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> janela deve chamar o método para obter um ponteiro para a interface.

 As janelas de quadro podem impedir que partes de suas informações de contexto de seleção sejam propagadas para o contexto de seleção global quando são iniciadas. Essa habilidade é útil para janelas de ferramentas que podem ter que começar com uma seleção vazia.

 Modificar o contexto global de seleção desencadeia eventos que o VSPackages pode monitorar. Os VSPackages podem executar as `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> seguintes tarefas implementando e interfaces:

- Atualize o arquivo ativo atualmente em uma hierarquia.

- Monitore alterações em certos tipos de elementos. Por exemplo, se o vsPackage usar uma janela **Propriedades** especiais, você poderá monitorar alterações na janela **Propriedades** ativas e reiniciar a sua quando necessário.

  A seqüência a seguir mostra o curso típico de rastreamento de seleção.

1. O IDE recupera o contexto de seleção da janela recém-aberta e o coloca no contexto de seleção global. Se o contexto de seleção usa HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, essa informação não é propagada para o contexto global. Para obter mais informações, consulte [Feedback ao Usuário](../../extensibility/internals/feedback-to-the-user.md).

2. Os eventos de notificação são transmitidos para qualquer VSPackage que os solicitou.

3. O VSPackage atua nos eventos que recebe realizando atividades como atualizar uma hierarquia, reativar uma ferramenta ou outras tarefas semelhantes.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Tipos de projeto](../../extensibility/internals/project-types.md)
