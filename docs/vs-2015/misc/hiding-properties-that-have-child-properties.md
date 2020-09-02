---
title: Ocultando propriedades que têm propriedades filho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822380"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ocultar propriedades que têm propriedades filho
Você desejaria ocultar propriedades que têm propriedades filho:  
  
- Se você aninhar projetos em que o projeto pai controla programaticamente alguns aspectos do projeto filho.  
  
- Se você usar um controle com um designer especializado e não desejar conceder aos desenvolvedores acesso completo a todas as propriedades do controle.  
  
- Se você tiver a propriedade de escopo de um objeto e quiser limitar a exibição das propriedades.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Para ocultar propriedades que têm propriedades filho  
  
1. Defina o `pfDisplay` parâmetro em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> para `FALSE` .  
  
2. Defina o `pfHide` parâmetro em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> para `TRUE` .  
  
## <a name="see-also"></a>Consulte Também  
 [Grade de exibição de propriedades](../extensibility/internals/properties-display-grid.md)