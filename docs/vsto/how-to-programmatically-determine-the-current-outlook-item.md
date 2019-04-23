---
title: 'Como: Determinar o item atual do Outlook de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5566538b428502c8e63e752463b0271daeac2918
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052500"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Como: Determinar o item atual do Outlook de forma programática
  Este exemplo usa o `Explorer.SelectionChange` evento para exibir o nome da pasta atual e algumas informações sobre o item selecionado. O código, em seguida, exibe o item selecionado.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Compromisso, contatos e itens de email no Microsoft Office Outlook.

## <a name="see-also"></a>Consulte também
- [Visão geral de modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)
- [Como: Recuperar uma pasta por nome de forma programática](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Como: Pesquisar um contato específico de forma programática](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
