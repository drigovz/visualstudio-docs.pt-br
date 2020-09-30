---
title: Propriedades inválidas no arquivo. OFS para a classe de mensagem "
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66e8ecacffb58e945a3f80d03f47edc1329668d1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584653"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Propriedades inválidas no arquivo. OFS para a classe de mensagem

  O erro "uma ou mais propriedades no arquivo. OFS não são válidas para a classe de mensagem selecionada" aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região de formulário não são compatíveis com as classes de mensagem que você seleciona na página final do assistente de **nova região de formulário** .

Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

 Você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Na página final do assistente de **nova região de formulário** , selecione uma classe de mensagem que seja compatível com os campos na região do formulário.

- No designer de formulários no Outlook, remova os campos que não são compatíveis com as classes de mensagem. Remova os campos que você planeja selecionar na página final do assistente de **nova região de formulário** .

## <a name="see-also"></a>Confira também
- [Walkthrough: importar uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
