---
title: Ocultar propriedades que têm propriedades filho | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822380"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ocultar propriedades que têm propriedades filho
Você gostaria de ocultar as propriedades que têm propriedades filho:  
  
- Se você tiver projetos aninhados onde o projeto pai por meio de programação controla alguns aspectos do projeto filho.  
  
- Se você usar um controle com um designer especializado e você não deseja dar aos desenvolvedores acesso completo a todas as propriedades do controle.  
  
- Se você tiver a propriedade do escopo de um objeto e para limitar a exibição de propriedades.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Para ocultar as propriedades que têm propriedades filho  
  
1. Defina as `pfDisplay` parâmetro no <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> para `FALSE`.  
  
2. Defina as `pfHide` parâmetro no <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> para `TRUE`.  
  
## <a name="see-also"></a>Consulte também  
 [Grade de exibição de propriedades](../extensibility/internals/properties-display-grid.md)