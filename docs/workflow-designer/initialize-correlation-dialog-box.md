---
title: Caixa de diálogo Designer de Fluxo de Trabalho-inicializar correlação
description: Saiba como você pode usar a caixa de diálogo inicializar correlação no Designer de Fluxo de Trabalho para editar a propriedade CorrelationData de uma atividade InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a41511f9bfb381eeb422cc9cf7ec015d55ceff70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931507"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar a caixa de diálogo correlação

A caixa de diálogo **inicializar correlação** é usada em Designer de fluxo de trabalho para editar a <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade de uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. Para obter mais informações, consulte [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **inicializar correlação** :

|Elemento da interface do usuário|DESCRIÇÃO|
|-|-----------------|
|**Correlação**|<xref:System.ServiceModel.Activities.CorrelationHandle> de correlação para inicializar.|
|**Inicializar em**|Um par chave/valor que contém os dados para inicializar. Esse valor corresponde à <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade. Um exemplo de um par chave/valor válido é uma chave chamada "OrderID" emparelhada com uma variável chamada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar a caixa de diálogo correlação inicializar

Clique em **Exibir** no designer de atividade do **InitializeCorrelation** ou selecione uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade em Designer de fluxo de trabalho. Em seguida, clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Propriedade na grade de propriedades.

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
