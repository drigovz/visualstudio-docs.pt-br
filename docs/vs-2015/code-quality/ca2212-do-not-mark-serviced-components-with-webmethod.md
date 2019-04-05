---
title: 'CA2212: Não marcar componentes atendidos com WebMethod | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6f2e89705e36407e39103296e3eee70482e3d03f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926507"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Não marcar componentes atendidos com WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método em um tipo que herda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> está marcado com <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Web.Services.WebMethodAttribute> se aplica aos métodos dentro de um serviço Web XML criados usando o ASP.NET; ele torna o método chamável de clientes remotos da Web. O método e a classe devem ser pública e em execução em um aplicativo Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> tipos são hospedados por aplicativos COM+ e podem usar serviços COM+. <xref:System.Web.Services.WebMethodAttribute> não é aplicado a <xref:System.EnterpriseServices.ServicedComponent> porque eles não devem ser os mesmos cenários. Especificamente, adicionando o atributo para o <xref:System.EnterpriseServices.ServicedComponent> método não faz o método que pode ser chamado de clientes remotos da Web. Porque <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.EnterpriseServices.ServicedComponent> método têm comportamentos conflitantes e requisitos para o contexto e fluxo de transações, o comportamento do método estará incorretos em alguns cenários.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o atributo do <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Não há nenhum cenário em que a combinação desses elementos está correto.

## <a name="see-also"></a>Consulte também
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
