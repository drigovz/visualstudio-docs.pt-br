---
title: 'Como: direcionar a interface do usuário multilíngüe do Office'
description: Saiba como você pode usar o Visual Studio para direcionar programaticamente o Microsoft Office interface do usuário multilíngue.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 245b257140cd0b1f54719ec7a132bf2297fc2dd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962334"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Como: direcionar a interface do usuário multilíngüe do Office
  A MUI (Multilingual User interface) é um recurso Microsoft Office que dá ao usuário final a capacidade de alterar o idioma da interface do usuário. Por exemplo, um usuário final trabalhando com uma interface de usuário em inglês pode alterar o idioma da interface do usuário para espanhol.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se seu aplicativo for usado por pessoas que usam muitos idiomas do Office, você poderá adicionar código para alterar automaticamente o idioma das cadeias de caracteres da interface do usuário para corresponder ao idioma usado pelo Office no computador do usuário (se o usuário tiver os recursos corretos instalados).

## <a name="to-check-the-current-office-ui-setting"></a>Para verificar a configuração atual da interface do usuário do Office

1. Use a <xref:System.Threading.Thread.CurrentUICulture%2A> Propriedade do thread atual. Defina o idioma das cadeias de caracteres da interface do usuário para corresponder ao idioma usado pela versão do Office que atualmente é executada no computador do usuário.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Consulte também
- [Como: direcionar aplicativos do Office por meio de assemblies de interoperabilidade primária](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)
