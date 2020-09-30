---
title: Associar uma página da Web a uma pasta do Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 35eb2dc3b1b595a4bf960af67ac5006cd9839c6e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585334"
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
