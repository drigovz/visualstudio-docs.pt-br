---
title: 'Como: Enviar email por meio de programação'
ms.date: 08/14/2019
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
ms.openlocfilehash: 72d033add2ba8320b14eebd5af700ab225d34410
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551760"
---
# <a name="how-to-programmatically-send-email"></a>Como: Enviar email por meio de programação
  Este exemplo envia uma mensagem de email para contatos que têm o nome de domínio **example.com** em seus endereços de email.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Contatos que têm o nome de domínio **example.com** em seus endereços de email.

## <a name="robust-programming"></a>Programação robusta
 Não remova o código de filtro que procura o nome de domínio **example.com**. Sua solução enviará mensagens de email para todos os seus contatos se você remover o filtro.

## <a name="see-also"></a>Consulte também
- [Trabalhar com itens de email](../vsto/working-with-mail-items.md)
- [Como: Criar programaticamente um item de email](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Como: Acesse os contatos do Outlook de forma programática](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Como: Executar programaticamente ações quando uma mensagem de email for recebida](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
