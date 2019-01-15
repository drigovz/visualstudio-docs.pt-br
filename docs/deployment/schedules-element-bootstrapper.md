---
title: '&lt;Agendas&gt; elemento (Bootstrapper) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 850c94274f783c306fe31fde4d86c9563c928adf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894292"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Agendas&gt; elemento (bootstrapper)
O `Schedules` elemento contém `Schedule` elementos, que definem a horários específicos em quais comandos definidos pelo `Command` elemento deve ser executado.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `Schedules` um filho do elemento é o `Product` elemento. Cada `Product` elemento pode ter no máximo um `Schedules` elemento. O `Schedules` elemento não tem atributos.  
  
## <a name="schedule"></a>Agendamento  
 O `Schedule` um filho do elemento é o `Schedules` elemento. Um `Schedules` elemento deve ter pelo menos um `Schedule` elemento.  
  
 `Schedule` tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O nome do item de agenda. Isso corresponde do `ScheduleName` propriedade do `Command` elemento. Quando um `Command` faz referência a agenda nomeada, ele será executado somente no período indicado pelo que `Schedule` elemento. Agendas também podem ser associadas com o `FailIf` e `BypassIf` elementos, que restringem esses testes condicionais para execução no agendamento especificado. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 Uma determinada `Schedule` elemento pode ter exatamente um dos seguintes filhos.  
  
## <a name="buildlist"></a>BuildList  
 O `BuildList` elemento instrui o instalador para executar um comando imediatamente após o aplicativo de inicialização é iniciado.  
  
## <a name="beforepackage"></a>BeforePackage  
 O `BeforePackage` elemento instrui o instalador para executar um comando antes de instalar o pacote especificado.  
  
## <a name="afterpackage"></a>AfterPackage  
 O `AfterPackage` elemento instrui o instalador para executar um comando depois de instalar o pacote especificado.  
  
## <a name="see-also"></a>Consulte também  
 [\<Produto > elemento](../deployment/product-element-bootstrapper.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)