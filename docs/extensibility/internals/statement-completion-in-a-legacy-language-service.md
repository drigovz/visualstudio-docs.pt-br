---
title: Conclusão da declaração em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704936"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Preenchimento de declaração em um serviço de linguagem herdado
A conclusão da declaração é o processo pelo qual o serviço de idiomas ajuda os usuários a terminar uma palavra-chave ou elemento de idioma que eles começaram a digitar no editor principal. Este tópico discute como funciona a conclusão da declaração e como implementá-la em seu serviço de idiomas.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova forma de implementar a conclusão da declaração, consulte [Passo a Passo: Exibindo conclusão da declaração](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="implementing-statement-completion"></a>Implementando a conclusão da declaração
 No editor principal, a conclusão da declaração ativa uma ui especial que, interativamente, ajuda você a escrever código com mais facilidade e rapidez. A conclusão da instrução ajuda a exibir objetos ou classes pertinentes quando eles são necessários, o que evita que você tenha que se lembrar de elementos específicos ou ter que procurá-los em um tópico de referência de Ajuda.

 Para implementar a conclusão da declaração, seu idioma deve ter um gatilho de conclusão de declaração, que pode ser analisado. Por exemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usa um operador de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] dot (.) enquanto usa um operador de seta (->). Um serviço de idiomas pode usar mais de um gatilho para iniciar a conclusão da declaração. Estes gatilhos são programados no filtro de comando.

## <a name="command-filters-and-triggers"></a>Filtros e gatilhos de comando
 Filtros de comando interceptam ocorrências do gatilho ou dos gatilhos. Para adicionar o filtro de comando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> à exibição, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> a interface e anexe-a à exibição chamando o método. Você pode usar o<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>mesmo filtro de comando ( ) para todos os aspectos do serviço de idioma, como conclusão de declaração, marcadores de erro e dicas de método. Para obter mais informações, consulte [Intercepting Legacy Language Service Commands](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Quando o gatilho é inserido no editor — especificamente, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> buffer de texto — seu serviço de idioma então chama o método. Isso faz com que o editor traga a ui para que o usuário possa escolher entre os candidatos de conclusão da declaração. Este método exige <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> que <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> você implemente e as bandeiras como parâmetros. A lista de itens de conclusão aparece em uma caixa de lista de rolagem. À medida que o usuário continua digitando, a seleção dentro da caixa de lista é atualizada para refletir a correspondência mais próxima dos caracteres mais recentes digitados. O editor principal implementa a interface do usuário para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> conclusão da declaração, mas o serviço de idiomas deve implementar a interface para definir um conjunto de itens de conclusão do candidato para a declaração.

## <a name="see-also"></a>Confira também
- [Interceptando comandos do serviço de linguagem herdado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
