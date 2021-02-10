---
title: Caixa de diálogo Definição de Designer de Fluxo de Trabalho-CorrelatesOn
description: Saiba como você pode usar a caixa de diálogo CorrelatesOn no Designer de Fluxo de Trabalho para editar a propriedade CorrelatesOn de uma atividade Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b4f371da2570d5573ce84c7e29393889202ae940
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955535"
---
# <a name="correlateson-definition-dialog-box"></a>Caixa de diálogo definição de CorrelatesOn

A caixa de diálogo **CorrelatesOn** é usada em Designer de fluxo de trabalho para editar a <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriedade de uma <xref:System.ServiceModel.Activities.Receive> atividade. Para obter mais informações, consulte [receber designer de atividade](../workflow-designer/receive-activity-designer.md).

Correlação entre atividades de <xref:System.ServiceModel.Activities.Receive> especifica como as operações de serviço diferentes conectam entre si em um fluxo de trabalho.

A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **CorrelatesOn** .

|Elemento da interface do usuário|DESCRIÇÃO|
|-|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> que é usado para rotear a mensagem à instância apropriado de fluxo de trabalho.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada. Esse valor corresponde à <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriedade. Consultas XPath estão contidas em um objeto de <xref:System.ServiceModel.MessageQuerySet> .|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar a caixa de diálogo CorrelatesOn

O designer de atividade **Receive** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho, sempre que as atividades são geralmente colocadas. Descartar o designer de atividade cria uma <xref:System.ServiceModel.Activities.Receive> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de recebimento. Para abrir a caixa de diálogo **definição de CorrelatesOn** , selecione o designer de atividade de **recebimento** e, em seguida, na grade de propriedades, selecione o botão de reticências ao lado do texto da coleção para a propriedade **CorrelatesOn** .

## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Activities.Receive>
- [Adicione a caixa de diálogo CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)