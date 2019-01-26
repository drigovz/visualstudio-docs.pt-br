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
ms.openlocfilehash: a607fc0e885ea73f95f4b48a82777234977644bb
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872983"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Uma ou mais propriedades no arquivo .ofs não são válidas para a classe de mensagem selecionada
  Este erro aparece quando você importa uma região de formulário projetada no Outlook, mas um ou mais campos na região do formulário não são compatíveis com as classes de mensagem que você selecionar na página final do **nova região de formulário** assistente.  

Por exemplo, você pode selecionar **tarefa (IPM. Tarefa)** na página final do **nova região de formulário** assistente. Se a região do formulário tem um **endereço comercial** campo, você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o **endereço comercial** campo não é compatível com o `IPM.Task` classe de mensagem.  
  
 Você pode selecionar **tarefa (IPM. Tarefa)** na página final do **nova região de formulário** assistente. Se a região do formulário tem um **endereço comercial** campo, você receberá esse erro porque uma tarefa não tem um endereço comercial. Portanto, o **endereço comercial** campo não é compatível com o `IPM.Task` classe de mensagem.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Na página final do **nova região de formulário** assistente, selecione a classe de mensagem que é compatível com os campos na região do formulário.  
  
-   No Designer de formulários do Outlook, remova os campos que não são compatíveis com as classes de mensagem. Remover campos que você pretende selecionar na página final do **nova região de formulário** assistente.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Importar de uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
