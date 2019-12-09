---
title: Propriedades de elementos em diagramas de componente UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671455"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Propriedades de elementos em diagramas de componente UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de componente UML, cada elemento no diagrama tem propriedades. Para ver as propriedades de um elemento, clique com o botão direito do mouse no elemento no diagrama ou no **Gerenciador de modelos UML** e clique em **Propriedades**. As propriedades aparecem na janela **Propriedades** .

> [!NOTE]
> Este tópico é sobre as propriedades de elementos em diagramas de componentes UML. Para obter mais informações sobre como ler diagramas de componentes UML, consulte [diagramas de componentes UML: referência](../modeling/uml-component-diagrams-reference.md). Para obter mais informações sobre como desenhar diagramas de componente UML, consulte [diagramas de componente UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propriedades de elementos

|propriedade|Padrão|Elemento|Descrição|
|--------------|-------------|-------------|-----------------|
|**Nome**|Um nome padrão|Todos|Identifica o elemento.|
|**Nome qualificado**|Namespace:: nome|Todos|Identifica o elemento exclusivamente.<br /><br /> Um nome de componente ou tipo é prefixado com o nome qualificado do pacote que o contém.<br /><br /> Um nome de parte ou porta é prefixado com o nome qualificado do componente que o possui.|
|**Itens de trabalho**|0 associado|Todos|O número de itens de trabalho associados a este elemento. Para associar itens de trabalho, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).|
|**Descrição**|(nenhum)|Todos|Você pode fazer observações gerais sobre o elemento aqui.|
|**Cor**|(padrão para o tipo)|Componente, parte, delegação, assembly de parte|A cor da forma. Ao contrário de outras propriedades, essa é a cor da forma, em vez do elemento de modelo exibido pela forma.|
|**É instanciado indiretamente**|verdadeiro|Componente|O componente existe apenas como um artefato de design. Em tempo de execução, somente suas partes existem.|
|**É abstrato**|False|Componente|A definição de componente pode ser usada somente como uma generalização da qual outros componentes podem ser especializados.|
|**Visibilidade**|Público|Componente, parte, porta|**Público** -globalmente visível.<br /><br /> **Pacote** -visível no pacote.<br /><br /> **Particular** -visível dentro do componente de propriedade.<br /><br /> **Protegido** – visível para os componentes derivados do proprietário.|
|**Tipo**|Tipo na criação|Parte<br /><br /> Porta|O tipo de uma parte é um componente ou uma classe.<br /><br /> O tipo de uma porta é uma interface.|
|**Multiplicidade**|1|Parte<br /><br /> Porta|Indica quantas instâncias do tipo especificado formam parte do componente pai.<br /><br /> `1`-exatamente um.<br /><br /> `0..1`-um ou nenhum.<br /><br /> `*`-uma coleção de qualquer número.<br /><br /> `n..m`-uma coleção de de n a m instâncias.|
|**É comportamento**|False|Porta|Se for true, as mensagens para essa porta serão tratadas por atividades ou operações que são descritas como parte do componente, em vez de suas partes.|
|**É serviço**|False|Porta|Se for true, essa porta faz parte da interface publicada desse componente.|
|**LinkedPackage**|Modelo|Diagrama|O namespace padrão para elementos adicionados a este diagrama.|

## <a name="see-also"></a>Consulte também
 [Diagramas de caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)
