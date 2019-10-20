---
title: Caixa de diálogo Definição de CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656945"
---
# <a name="correlateson-definition-dialog-box"></a>Caixa de diálogo definição de CorrelatesOn
A caixa de diálogo **CorrelatesOn** é usada em [!INCLUDE[wfd1](../includes/wfd1-md.md)] para editar a propriedade <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> de uma atividade de <xref:System.ServiceModel.Activities.Receive>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] o tópico de [recebimento](../workflow-designer/receive-activity-designer.md) .

 Correlação entre atividades de <xref:System.ServiceModel.Activities.Receive> especifica como as operações de serviço diferentes conectam entre si em um fluxo de trabalho.

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **CorrelatesOn** .

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> que é usado para rotear a mensagem à instância apropriado de fluxo de trabalho.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada. Isso corresponde à propriedade de <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> . Consultas XPath estão contidas em um objeto de <xref:System.ServiceModel.MessageQuerySet> .|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar a caixa de diálogo CorrelatesOn
 O designer de atividade **Receive** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. Selecione o designer de atividade de **recebimento** e clique no botão de reticências ao lado do texto (coleção) da propriedade **CorrelatesOn** na grade de propriedades para que a caixa de diálogo de **definição CorrelatesOn** seja exibida.

## <a name="see-also"></a>Consulte também
 caixa de diálogo <xref:System.ServiceModel.Activities.Receive> [Adicionar CorrelationInitializers caixa](../workflow-designer/add-correlationinitializers-dialog-box.md) de diálogo [inicializar correlação](../workflow-designer/initialize-correlation-dialog-box.md)