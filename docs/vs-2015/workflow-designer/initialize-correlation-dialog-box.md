---
title: Caixa de diálogo inicializar correlação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659048"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar a caixa de diálogo correlação
A caixa de diálogo **inicializar correlação** é usada no [!INCLUDE[wfd1](../includes/wfd1-md.md)] para editar a <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade de uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. [!INCLUDE[crdefault](../includes/crdefault-md.md)] o tópico [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **inicializar correlação** .

|Elemento da interface do usuário|Descrição|
|----------------|-----------------|
|**Correlação**|<xref:System.ServiceModel.Activities.CorrelationHandle> de correlação para inicializar.|
|**Inicializar em**|Um par chave/valor que contém os dados para inicializar. Isso corresponde à propriedade de <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Um exemplo de um par válido chave/valor seria uma chave chamada “OrderID” emparelhado com uma variável chamada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar a caixa de diálogo correlação inicializar

- Clique em **Exibir** no designer de atividade do **InitializeCorrelation** ou selecione uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade em [!INCLUDE[wfd2](../includes/wfd2-md.md)] e, em seguida, clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Propriedade na grade de propriedades.

## <a name="see-also"></a>Consulte Também
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)