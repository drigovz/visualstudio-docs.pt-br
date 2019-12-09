---
title: Propriedades de tipos em diagramas de classe UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671328"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Propriedades de tipos em diagramas de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de classes UML, um *tipo* é uma classe, uma interface ou uma enumeração.

> [!NOTE]
> Este tópico é sobre as propriedades de tipos em diagramas de classe UML. Para mais informações, consulte os seguintes tópicos:

- [Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)

- [Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)

- [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propriedades de operações em diagramas de classe UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Propriedades de associações em diagramas de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>Propriedades
 Essas são as propriedades de uma classe, interface ou enumeração.

 Para ver as propriedades de um tipo, clique com o botão direito do mouse no tipo no diagrama ou no **Gerenciador de modelos UML**e clique em **Propriedades**. As propriedades aparecem na janela **Propriedades** .

|**Property**|**Padrão**|Aparece em|Descrição|
|------------------|-----------------|----------------|-----------------|
|**Nome**|Um nome padrão|Todos os elementos|Identifica o elemento.|
|**Nome qualificado**|Contendo o pacote:: nome do tipo|Todos os elementos|Identifica o elemento exclusivamente. Prefixado com o nome qualificado do pacote que o contém.|
|**Cor**|Padrão para o tipo de tipo|Todos os elementos|A cor desta forma. Ao contrário das outras propriedades, essa não é uma propriedade do elemento Model subjacente. Exibições diferentes do mesmo tipo podem ter cores diferentes.|
|**É abstrato**|False|Class|Se for true, a classe não poderá ser instanciada e será destinada para uso como uma classe base.|
|**É folha**|False|Classe, interface|Se for true, o tipo não se destina a ter tipos derivados.|
|**Está ativo**|False|Class|Se for true, cada instância desse tipo será associada a um thread de controle.|
|**Visibilidade**|Público|Classe, interface, enumeração|-Público-globalmente visível.<br />-Private – esse tipo é visível dentro do pacote que o possui.<br />-Pacote-visível no pacote.|
|**Itens de trabalho**|0 associado|Todos os elementos|O número de itens de trabalho associados a este elemento. Para associar itens de trabalho, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).|
|**Descrição**|(blank)|Todos os elementos|Você pode fazer observações gerais sobre o item aqui.|
|**Associação de modelo**|(nenhum)|Classe, interface, enumeração|Se não estiver vazio, esse tipo será definido pela Associação de valores de parâmetro a essa classe de modelo. Expanda a propriedade para ver as associações dos parâmetros do modelo.|
|**Parâmetros de modelo**|(nenhum)|Classe, interface, enumeração|Se não estiver vazia, esta é uma classe de modelo que tem os parâmetros listados aqui. Para adicionar parâmetros ou exibir as propriedades de parâmetros individuais, clique em **[...]** .|

## <a name="see-also"></a>Consulte também
 [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Propriedades de operações em diagramas de classe UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Propriedades de associações em diagramas de classe](../modeling/properties-of-associations-on-uml-class-diagrams.md) UML [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)
