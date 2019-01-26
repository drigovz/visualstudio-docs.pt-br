---
title: Referência de API não gerenciada (desenvolvimento do Office no Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f61f764028959cce4015834c53d6ca74bde46bed
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863533"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referência de API não gerenciada (desenvolvimento do Office no Visual Studio)
  Começando com o 2007 Microsoft Office system, aplicativos do Office usam as [interface IManagedAddin](../vsto/imanagedaddin-interface.md) interface para chamar em um suplemento do VSTO carregador componente que está incluído com o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Esse componente é usado para ajudar a carga gerenciado VSTO Add-ins. Você pode criar seu próprio componente de carregador de suplemento do VSTO ao implementar essa interface.  
  
> [!NOTE]  
>  Interessado em desenvolver soluções que estendem a experiência do Office em toda [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com soluções e suplementos do VSTO, e você pode criá-los usando quase qualquer tecnologia, como HTML5, JavaScript, CSS3 e XML de programação da web.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Uma interface COM que você pode implementar para carregar e descarregar gerenciado VSTO Add-ins em aplicativos do Office.  
