---
title: Soluções VBA e do Office no Visual Studio comparadas
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 313af1a48b4c8fac6281fd8250ed36104a5276b6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866877"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Soluções VBA e do Office no Visual Studio comparadas
  Microsoft Visual Basic for Applications (VBA) usa o código não gerenciado que está totalmente integrado com aplicativos do Office. Projetos do Microsoft Office criados usando o Visual Studio permitem que você aproveite o .NET Framework e as ferramentas de design do Visual Studio.  
  
 Para obter informações sobre os tipos de soluções do Office que você pode criar usando o Visual Studio, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Comparação  
 A tabela a seguir fornece uma comparação básica entre soluções VBA e soluções do Office no Visual Studio.  
  
|Soluções do VBA|Soluções do Office no Visual Studio|  
|-------------------|---------------------------------------|  
|Usa o código que está conectado ao e persistente com um documento específico.|Usa o código que é armazenado separadamente do documento (para personalizações no nível do documento), ou em um assembly que é carregado pelo aplicativo (para suplementos do VSTO).|  
|Funciona com as APIs de VBA e modelos de objeto do Office.|Fornece acesso a modelos de objeto do Office e o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] APIs.|  
|Projetado para uma experiência de desenvolvedor simplificada e de gravação da macro.|Projetado para segurança, facilidade de manutenção de código e a capacidade de usar o ambiente de desenvolvimento integrado completo do Visual Studio (IDE).|  
|Funciona bem para soluções que se beneficiam de uma integração total com aplicativos do Office.|Funciona bem para soluções que se beneficiam de todos os recursos do Visual Studio e o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Tem limitações para a empresa, especialmente nas áreas de segurança e implantação.|Projetado para uso na empresa.|  
  
 Algumas coisas são ainda mais fácil de fazer rapidamente usando o VBA. Especificamente, você talvez queira continuar usando o VBA para:  
  
-   Funções de planilha personalizado.  
  
-   Gravação de macros.  
  
## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combinar soluções VBA e soluções do Office criadas usando o Visual Studio  
 Você pode chamar o código VBA de soluções do Office criadas usando o Visual Studio, e você também pode chamar o código em soluções do Office criadas usando o Visual Studio do VBA. A técnica específica é diferente dependendo se sua solução do Office é um suplemento do VSTO ou uma personalização no nível de documento. Para obter mais informações, consulte [chamar o código de outras soluções do Office no VSTO Add-ins](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) e [combinar VBA e personalizações no nível de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Chamar o código no VSTO Add-ins de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Combinar o VBA e personalizações no nível de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Proteger as soluções do Office](../vsto/securing-office-solutions.md)   
 [Introdução ao &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
