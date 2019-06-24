---
title: Localizar um endereço de email em contatos programaticamente
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26e32314db68ae064edac5537222447625cb051d
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328966"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Como: Pesquisar um endereço de email em contatos de forma programática
  Este exemplo procura uma pasta de contatos para os contatos que têm o nome de domínio **exemplo.com** em seus endereços de email.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Contatos que têm o nome de domínio **exemplo.com** em seus endereços de email (por exemplo, `somebody@example.com`), e que têm nomes e sobrenomes.

## <a name="see-also"></a>Consulte também
- [Trabalhar com itens de contato](../vsto/working-with-contact-items.md)
- [Como: Enviar email](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Como: Acessar os contatos do Outlook de forma programática](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Como: Adicionar uma entrada a contatos do Outlook de forma programática](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
