---
title: 'Como: determinar programaticamente o item atual do Outlook'
description: Saiba como você pode determinar programaticamente o item atual do Microsoft Outlook. Este exemplo usa o evento Explorer. SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 10b8bd8103e80040519b9e3c5546f892da326202
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526786"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Como: determinar programaticamente o item atual do Outlook
  Este exemplo usa o `Explorer.SelectionChange` evento para exibir o nome da pasta atual e algumas informações sobre o item selecionado. Em seguida, o código exibe o item selecionado.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Itens de compromisso, contato e email no Microsoft Office Outlook.

## <a name="see-also"></a>Veja também
- [Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)
- [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Como: pesquisar programaticamente por um contato específico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
