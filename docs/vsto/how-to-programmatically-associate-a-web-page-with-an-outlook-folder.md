---
title: Associar uma página da Web a uma pasta do Outlook
description: Saiba como você pode associar uma página da Web com Microsoft Office pasta do Outlook. Este exemplo verifica uma pasta chamada HtmlView no Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885567"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Associar uma página da Web a uma pasta do Outlook

  Este exemplo verifica uma pasta chamada `HtmlView` em Microsoft Office Outlook. Se a pasta não existir, o código criará a pasta e atribuirá uma página da Web a ela. Se a pasta existir, o código exibirá o conteúdo da pasta.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Confira também
- [Trabalhar com pastas](../vsto/working-with-folders.md)
- [Como: recuperar programaticamente uma pasta por nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Como: criar programaticamente itens de pasta personalizados](../vsto/how-to-programmatically-create-custom-folder-items.md)
