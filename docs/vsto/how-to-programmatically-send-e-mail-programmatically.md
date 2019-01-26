---
title: 'Como: Enviar email'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51546047a12e23c688ccfdfd05aeaa9c2ab89f95
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866721"
---
# <a name="how-to-programmatically-send-email"></a>Como: Enviar email  
  Este exemplo envia uma mensagem de email para contatos que têm o nome de domínio **exemplo.com** em seus endereços de email.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Este exemplo requer:  
  
-   Contatos que têm o nome de domínio **exemplo.com** em seus endereços de email.  
  
## <a name="robust-programming"></a>Programação robusta  
 Não remova o código de filtro que procura o nome de domínio **exemplo.com**. Sua solução enviará mensagens de email para todos os seus contatos, se você remover o filtro.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com itens de email](../vsto/working-with-mail-items.md)   
 [Como: Criar um item de email de forma programática](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Como: Acessar os contatos do Outlook de forma programática](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Como: Executar ações programaticamente quando uma mensagem de email é recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
