---
title: Soluções do VBA e do Office no Visual Studio comparadas
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
ms.openlocfilehash: 24e7d3674712a17d940b94637db808c0d91d2d6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982131"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Soluções do VBA e do Office no Visual Studio comparadas
  O Microsoft Visual Basic for Applications (VBA) usa código não gerenciado que é totalmente integrado aos aplicativos do Office. Microsoft Office projetos criados usando o Visual Studio permitem que você aproveite as ferramentas de design do .NET Framework e do Visual Studio.

 Para obter informações sobre os tipos de soluções do Office que você pode criar usando o Visual Studio, consulte [visão geral do desenvolvimento de soluções do office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Comparação
 A tabela a seguir fornece uma comparação básica entre as soluções do VBA e as soluções do Office no Visual Studio.

|Soluções do VBA|Soluções do Office no Visual Studio|
|-------------------|---------------------------------------|
|Usa o código que está conectado e persistido com um documento específico.|Usa o código que é armazenado separadamente do documento (para personalizações em nível de documento) ou em um assembly que é carregado pelo aplicativo (para suplementos do VSTO).|
|Funciona com os modelos de objeto do Office e as APIs do VBA.|Fornece acesso aos modelos de objeto do Office e às [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] APIs.|
|Projetado para gravação de macro e uma experiência de desenvolvedor simplificada.|Projetado para segurança, manutenção de código mais fácil e a capacidade de usar o IDE (ambiente de desenvolvimento integrado) completo do Visual Studio.|
|Funciona bem para soluções que se beneficiam de uma forte integração com aplicativos do Office.|Funciona bem para soluções que se beneficiam dos recursos completos do Visual Studio e do [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Tem limitações para a empresa, especialmente nas áreas de segurança e implantação.|Projetado para uso na empresa.|

 Algumas coisas ainda são mais fáceis de fazer rapidamente usando o VBA. Especificamente, talvez você queira continuar usando o VBA para:

- Funções de planilha personalizadas.

- Gravação de macro.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combine soluções do VBA e soluções do Office criadas usando o Visual Studio
 Você pode chamar o código VBA das soluções do Office criadas usando o Visual Studio e também pode chamar o código nas soluções do Office criadas usando o Visual Studio do VBA. A técnica específica difere dependendo se sua solução do Office é um suplemento do VSTO ou uma personalização no nível do documento. Para obter mais informações, consulte [chamar código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) e [combinar personalizações do VBA e no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Confira também
- [Visão geral do desenvolvimento de soluções do Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md)
- [Chamar código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Combine personalizações do VBA e no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
- [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
