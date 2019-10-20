---
title: Caixa de diálogo Definição de Designer de Fluxo de Trabalho-CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650594"
---
# <a name="correlateson-definition-dialog-box"></a>Caixa de diálogo definição de CorrelatesOn

A caixa de diálogo **CorrelatesOn** é usada em Designer de fluxo de trabalho para editar a propriedade <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> de uma atividade de <xref:System.ServiceModel.Activities.Receive>. Para obter mais informações, consulte [receber designer de atividade](../workflow-designer/receive-activity-designer.md).

Correlação entre atividades de <xref:System.ServiceModel.Activities.Receive> especifica como as operações de serviço diferentes conectam entre si em um fluxo de trabalho.

A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **CorrelatesOn** .

|Elemento da Interface do Usuário|Descrição|
|-|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> que é usado para rotear a mensagem à instância apropriado de fluxo de trabalho.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada. Esse valor corresponde à propriedade <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Consultas XPath estão contidas em um objeto de <xref:System.ServiceModel.MessageQuerySet> .|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar a caixa de diálogo CorrelatesOn

O designer de atividade **Receive** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho, sempre que as atividades são geralmente colocadas. Descartar o designer de atividade cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com um <xref:System.Activities.Activity.DisplayName%2A> de recebimento padrão. Para abrir a caixa de diálogo **definição de CorrelatesOn** , selecione o designer de atividade de **recebimento** e, em seguida, na grade de propriedades, selecione o botão de reticências ao lado do texto da coleção para a propriedade **CorrelatesOn** .

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Receive>
- [Caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)