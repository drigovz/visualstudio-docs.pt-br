---
title: Referência de API para extensibilidade de modelagem UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672804"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Referência de API para extensibilidade de modelagem UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode escrever o código do programa para ler e modificar os modelos criados com o Visual Studio. A referência de API fornece informações sobre as classes específicas para ajudá-lo com isso. Para obter mais informações orientadas a tarefas, consulte os tópicos em [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md). Para ver quais versões do Visual Studio oferecem suporte a modelos UML, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Assemblies

|Assembly|O que isso permite que você faça|
|--------------|--------------------------------|
|Microsoft. VisualStudio. Uml. interfaces. dll|-Ler e alterar elementos de modelo, como IUseCase, IAssociation e assim por diante.<br />-Navegue pelas relações entre os elementos.<br /><br /> Os namespaces e os tipos correspondem àqueles definidos na especificação UML.|
|Microsoft. VisualStudio. ArchitectureTools. Extensibility. dll|-Criar novas instâncias de elementos de modelo<br />-Acesse e modifique formas e diagramas.|

## <a name="see-also"></a>Consulte também
 [Estender modelos UML e](../modeling/extend-uml-models-and-diagrams.md) [referência de API de diagramas para o SDK de modelagem do Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
