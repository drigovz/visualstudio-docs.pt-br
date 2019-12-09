---
title: Propriedades de elementos em diagramas de caso de uso UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671410"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Propriedades de elementos em diagramas de caso de uso UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de caso de uso UML, cada elemento no diagrama tem propriedades. Para ver as propriedades de um elemento, clique com o botão direito do mouse no elemento no diagrama ou no **Gerenciador de modelos UML** e clique em **Propriedades**. As propriedades aparecem na janela **Propriedades** .

> [!NOTE]
> Este tópico é sobre as propriedades de elementos em diagramas de caso de uso UML. Para obter mais informações sobre como ler diagramas de atividade UML, consulte [diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md). Para obter mais informações sobre como desenhar diagramas de atividade UML, consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propriedades de elementos

|propriedade|Padrão|Elemento|Descrição|
|--------------|-------------|-------------|-----------------|
|**Nome**|Um nome padrão|Todos|Identifica o elemento.|
|**Nome qualificado**|Pacote:: nome|Todos|Identifica o elemento exclusivamente. Prefixado com o nome qualificado do pacote que o contém.|
|**Itens de trabalho**|0 associado|Todos|O número de itens de trabalho associados a este elemento. Para associar itens de trabalho, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).|
|**Descrição**|(nenhum)|Todos|Você pode fazer observações gerais sobre o elemento aqui.|
|**Cor**|(padrão)|Todos|A cor da forma. Ao contrário de outras propriedades, essa não é uma propriedade do elemento exibido pela forma.|
|**Caminho da imagem**|(nenhum)|Ator|O caminho do arquivo de uma imagem que deve ser usada em vez do ícone de ator padrão. O ícone deve ser um arquivo de recurso no projeto do Visual Studio.|
|**Entidades**|(nenhum)|Caso de uso|O subsistema ou outro tipo que possui o caso de uso.<br /><br /> Você pode defini-lo colocando o caso de uso em um subsistema no diagrama.|
|**Visibilidade**|Público|Caso de uso, ator, subsistema|**Público** -globalmente visível.<br /><br /> **Pacote** -visível no pacote.|
|**IsAbstract**|False|Caso de uso, ator, subsistema|Se for true, o tipo não poderá ser instanciado e será destinado como base para especialização por outras definições.|
|**É instanciado indiretamente**|verdadeiro|subsistema|O subsistema existe apenas como um artefato de design. Em tempo de execução, somente suas partes existem.|
|**Hiperlink**|(nenhum)|Artefato|A URL ou o caminho do arquivo do diagrama ou documento ao qual o artefato fornece um link.|

 Para obter uma lista das propriedades de associações, consulte [Propriedades de associações em diagramas de classe UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Consulte também
 [Diagramas de caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)
