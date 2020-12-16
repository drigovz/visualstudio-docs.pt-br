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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b655a7bb6ab4b9ab971c0edd775aa8f29150dead
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525093"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Propriedades inválidas no arquivo. OFS para a classe de mensagem

  O erro "uma ou mais propriedades no arquivo. OFS não são válidas para a classe de mensagem selecionada" aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região de formulário não são compatíveis com as classes de mensagem que você seleciona na página final do assistente de **nova região de formulário** .

Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

 Você pode selecionar **tarefa (IPM. Tarefa)** na página final do assistente de **nova região de formulário** . Se a região do formulário tiver um campo de **endereço comercial** , você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o campo de **endereço comercial** não é compatível com a `IPM.Task` classe Message.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Na página final do assistente de **nova região de formulário** , selecione uma classe de mensagem que seja compatível com os campos na região do formulário.

- No designer de formulários no Outlook, remova os campos que não são compatíveis com as classes de mensagem. Remova os campos que você planeja selecionar na página final do assistente de **nova região de formulário** .

## <a name="see-also"></a>Veja também
- [Walkthrough: importar uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
