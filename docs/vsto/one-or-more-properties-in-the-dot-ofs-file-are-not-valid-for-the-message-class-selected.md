---
title: Uma ou mais propriedades no arquivo .ofs não são válidas para a classe de mensagem selecionada
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
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977855"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Uma ou mais propriedades no arquivo .ofs não são válidas para a classe de mensagem selecionada
  Esse erro aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região de formulário não são compatíveis com as classes de mensagem que você seleciona na página final do assistente de **nova região de formulário** .

Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

 Você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Na página final do assistente de **nova região de formulário** , selecione uma classe de mensagem que seja compatível com os campos na região do formulário.

- No designer de formulários no Outlook, remova os campos que não são compatíveis com as classes de mensagem. Remova os campos que você planeja selecionar na página final do assistente de **nova região de formulário** .

## <a name="see-also"></a>Confira também
- [Walkthrough: importar uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
