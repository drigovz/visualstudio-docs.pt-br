---
title: 'CA2212: Não marcar componentes atendidos com WebMethod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231663"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Não marcar componentes atendidos com WebMethod

|||
|-|-|
|NomeDoTipo|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Categoria|Microsoft.Usage|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um método em um tipo que herda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> é marcado com <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da regra

<xref:System.Web.Services.WebMethodAttribute>aplica-se a métodos em um serviço Web XML que foram criados usando ASP.NET; Ele torna o método que possa ser chamado por clientes Web remotos. O método e a classe devem ser públicos e em execução em um aplicativo Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>os tipos são hospedados por aplicativos COM+ e podem usar serviços COM+. <xref:System.Web.Services.WebMethodAttribute>Não é aplicado a <xref:System.EnterpriseServices.ServicedComponent> tipos porque eles não se destinam aos mesmos cenários. Especificamente, a adição do atributo ao <xref:System.EnterpriseServices.ServicedComponent> método não torna o método que possa ser chamado por clientes Web remotos. Como <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.EnterpriseServices.ServicedComponent> método tem comportamentos conflitantes e requisitos de contexto e fluxo de transações, o comportamento do método estará incorreto em alguns cenários.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o atributo do <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Não há cenários em que a combinação desses elementos esteja correta.

## <a name="see-also"></a>Consulte também

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>