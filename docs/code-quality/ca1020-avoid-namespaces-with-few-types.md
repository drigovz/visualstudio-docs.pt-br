---
title: 'CA1020: Evitar namespaces com poucos tipos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236236"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitar namespaces com poucos tipos

|||
|-|-|
|NomeDoTipo|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um namespace diferente do namespace global contém menos de cinco tipos.

## <a name="rule-description"></a>Descrição da regra

Certifique-se de que cada um dos seus namespaces tem uma organização lógica, e que existe uma razão válida para colocar os tipos em um namespace populamente preenchido. Os namespaces devem conter tipos que são usados juntos na maioria dos cenários. Quando seus aplicativos são mutuamente exclusivos, os tipos devem estar localizados em namespaces separados. Por exemplo, o <xref:System.Web.UI> namespace contém tipos que são usados em aplicativos Web e o <xref:System.Windows.Forms> namespace contém tipos que são usados em aplicativos [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]baseados em. Embora os namespaces tenham tipos que controlam aspectos da interface do usuário, esses tipos não são projetados para uso no mesmo aplicativo. Portanto, eles estão localizados em namespaces separados. A organização de namespace cuidadosa também pode ser útil porque aumenta a capacidade de descoberta de um recurso. Examinando a hierarquia de namespace, os consumidores de biblioteca devem ser capazes de localizar os tipos que implementam um recurso.

> [!NOTE]
> Os tipos de tempo de design e as permissões não devem ser mesclados em outros namespaces para obedecer a essa diretriz. Esses tipos pertencem a seus próprios namespaces abaixo do namespace principal, e os namespaces devem terminar em `.Design` e `.Permissions`, respectivamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, tente combinar namespaces que contenham apenas alguns tipos em um único namespace.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra quando o namespace não contém tipos que são usados com os tipos em seus outros namespaces.