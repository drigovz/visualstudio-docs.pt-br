---
title: '&lt;Elemento Schedules &gt; (Bootstrapper) | Microsoft Docs'
description: O elemento Schedules contém elementos Schedule, que definem horários específicos nos quais os comandos definidos pelo elemento Command devem ser executados.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0154816985076373c3ced4981aa714971a9ded29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949643"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Elemento Schedules &gt; (Bootstrapper)
O `Schedules` elemento contém `Schedule` elementos, que definem horários específicos nos quais os comandos definidos pelo `Command` elemento devem ser executados.

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
 O `Schedules` elemento é um filho do `Product` elemento. Cada `Product` elemento pode ter no máximo um `Schedules` elemento. O `Schedules` elemento não tem atributos.

## <a name="schedule"></a>Agenda
 O `Schedule` elemento é um filho do `Schedules` elemento. Um `Schedules` elemento deve ter pelo menos um `Schedule` elemento.

 `Schedule` tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Obrigatórios. O nome do item de agendamento. Isso corresponde à `ScheduleName` Propriedade do `Command` elemento. Quando uma `Command` referência à agenda nomeada, ela só será executada no momento indicado por esse `Schedule` elemento. Os agendamentos também podem ser associados `FailIf` aos `BypassIf` elementos e, que restringem a execução desses testes condicionais no agendamento especificado. Para obter mais informações, consulte [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|

 Um determinado `Schedule` elemento pode ter exatamente um dos seguintes filhos.

## <a name="buildlist"></a>BuildList
 O `BuildList` elemento instrui o instalador a executar um comando imediatamente após o aplicativo de inicialização ser iniciado.

## <a name="beforepackage"></a>BeforePackage
 O `BeforePackage` elemento instrui o instalador a executar um comando antes da instalação do pacote especificado.

## <a name="afterpackage"></a>AfterPackage
 O `AfterPackage` elemento instrui o instalador a executar um comando após a instalação do pacote especificado.

## <a name="see-also"></a>Consulte também
- [\<Product> elementos](../deployment/product-element-bootstrapper.md)
- [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)