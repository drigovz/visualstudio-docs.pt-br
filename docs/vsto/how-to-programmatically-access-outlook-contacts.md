---
title: 'Como: Acessar os contatos do Outlook de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9fc9cf214a8aebd663a7de29528790aa3cc0b46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967677"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Como: Acessar os contatos do Outlook de forma programática
  Este exemplo localiza todos os contatos cujos sobrenomes contêm uma cadeia de caracteres de pesquisa especificado.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Contatos cujos sobrenomes contêm a cadeia de caracteres "**Na"** (por exemplo, Tzipi Butnaru) na **contatos** pasta.

## <a name="see-also"></a>Consulte também
- [Trabalhar com itens de contato](../vsto/working-with-contact-items.md)
- [Como: Adicionar uma entrada a contatos do Outlook de forma programática](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Como: Pesquisar um contato específico de forma programática](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Como: Pesquisar um endereço de email em contatos de forma programática](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Como: Excluir contatos do Outlook de forma programática](../vsto/how-to-programmatically-delete-outlook-contacts.md)
