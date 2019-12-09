---
title: 'CA2212: não marcar componentes atendidos com WebMethod | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662943"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: não marcar componentes atendidos com WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método em um tipo que herda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> é marcado com <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Web.Services.WebMethodAttribute> se aplica a métodos em um serviço Web XML que foram criados usando ASP.NET; Ele torna o método que possa ser chamado por clientes Web remotos. O método e a classe devem ser públicos e em execução em um aplicativo Web ASP.NET. os tipos <xref:System.EnterpriseServices.ServicedComponent> são hospedados por aplicativos COM+ e podem usar serviços COM+. <xref:System.Web.Services.WebMethodAttribute> não é aplicado a tipos <xref:System.EnterpriseServices.ServicedComponent> porque eles não se destinam aos mesmos cenários. Especificamente, a adição do atributo ao método <xref:System.EnterpriseServices.ServicedComponent> não torna o método que possa ser chamado por clientes Web remotos. Como <xref:System.Web.Services.WebMethodAttribute> e um método <xref:System.EnterpriseServices.ServicedComponent> têm comportamentos e requisitos conflitantes para o contexto e o fluxo de transações, o comportamento do método estará incorreto em alguns cenários.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o atributo do método <xref:System.EnterpriseServices.ServicedComponent>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Não há cenários em que a combinação desses elementos esteja correta.

## <a name="see-also"></a>Consulte também
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
