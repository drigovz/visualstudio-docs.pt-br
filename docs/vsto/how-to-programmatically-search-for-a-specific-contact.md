---
title: 'Como: Pesquisar um contato específico de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: feff583d28bf53f4bffc9b425d52902688b80a4b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607155"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Como: Pesquisar um contato específico de forma programática
  Este exemplo procura uma pasta de contatos do Outlook para um contato específico por nome e sobrenome. O exemplo supõe que um contato denominado **John Evans** existe na pasta de contatos.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com itens de contato](../vsto/working-with-contact-items.md)
- [Introdução à programação VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
