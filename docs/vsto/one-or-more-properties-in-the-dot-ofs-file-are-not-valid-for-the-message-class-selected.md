---
title: Propriedades inválidas no arquivo. OFS para a classe de mensagem "
description: Saiba como corrigir um erro que ocorre quando uma ou mais propriedades no arquivo. OFS não são válidas para a classe de mensagem selecionada.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b22870cdb038adee84adc0fd7a56c269cb048626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841907"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Propriedades inválidas no arquivo. OFS para a classe de mensagem

  O erro "uma ou mais propriedades no arquivo. OFS não são válidas para a classe de mensagem selecionada" aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região de formulário não são compatíveis com as classes de mensagem que você seleciona na página final do assistente de **nova região de formulário** .

Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

 Você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Na página final do assistente de **nova região de formulário** , selecione uma classe de mensagem que seja compatível com os campos na região do formulário.

- No designer de formulários no Outlook, remova os campos que não são compatíveis com as classes de mensagem. Remova os campos que você planeja selecionar na página final do assistente de **nova região de formulário** .

## <a name="see-also"></a>Consulte também
- [Walkthrough: importar uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
