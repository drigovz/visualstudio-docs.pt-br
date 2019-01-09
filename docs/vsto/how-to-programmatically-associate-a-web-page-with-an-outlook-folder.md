---
title: 'Como: Associar programaticamente uma página da web uma pasta do Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6dc6bec7ecbf872d10045cb24e007edec893585
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089629"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Como: Associar programaticamente uma página da web uma pasta do Outlook
  Este exemplo verifica uma pasta chamada `HtmlView` no Microsoft Office Outlook. Se a pasta não existir, o código cria a pasta e atribui a uma página da Web a ela. Se a pasta existir, o código exibe o conteúdo da pasta.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com pastas](../vsto/working-with-folders.md)   
 [Como: Recuperar uma pasta por nome de forma programática](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Como: Criar itens de pasta personalizados programaticamente](../vsto/how-to-programmatically-create-custom-folder-items.md)  
