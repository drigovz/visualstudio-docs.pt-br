---
title: Designer de fluxo de trabalho - caixa de diálogo correlação inicializar
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f001e053b0c2fdfe892175b00ed3f39dc6f1b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829755"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar a caixa de diálogo correlação

O **inicializar correlação** caixa de diálogo é usada no Designer de fluxo de trabalho para editar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade de um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. Para obter mais informações, consulte [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

A tabela a seguir descreve os elementos de (UI) de interface do usuário para o **inicializar correlação** caixa de diálogo:

|Elemento da Interface do Usuário|Descrição|
|-|-----------------|
|**Correlação**|<xref:System.ServiceModel.Activities.CorrelationHandle> de correlação para inicializar.|
|**Inicializar em**|Um par chave/valor que contém os dados para inicializar. Esse valor corresponde à <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade. Um exemplo de um par chave/valor válido é uma chave chamada "OrderID" emparelhado com uma variável chamada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar a caixa de diálogo correlação inicializar

Clique em **exibição** sobre o **InitializeCorrelation** atividade designer ou selecione um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade no Designer de fluxo de trabalho. Em seguida, clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade na grade de propriedade.

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)