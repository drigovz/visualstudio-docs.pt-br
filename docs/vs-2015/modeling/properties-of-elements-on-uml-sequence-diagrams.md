---
title: Propriedades de elementos em diagramas de sequência UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671422"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Propriedades de elementos em diagramas de sequência UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de sequência UML, cada elemento no diagrama tem propriedades. Para ver as propriedades de um elemento, clique com o botão direito do mouse no elemento no diagrama ou no **Gerenciador de modelos UML** e clique em **Propriedades**. As propriedades aparecem na janela **Propriedades** .

> [!NOTE]
> Este tópico é sobre as propriedades de elementos em diagramas de sequência UML. Para obter mais informações sobre como ler diagramas de sequência UML, consulte [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md). Para obter mais informações sobre como desenhar diagramas de sequência UML, consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propriedades de elementos

|propriedade|Padrão|Elemento|Descrição|
|--------------|-------------|-------------|-----------------|
|**Nome**|Um nome padrão|Todos|Identifica o elemento.|
|**Nome qualificado**|Pacote:: nome|Todos|Identifica o elemento exclusivamente. Prefixado com o nome qualificado do pacote que o contém.|
|**Itens de trabalho**|0 associado|Todos|O número de itens de trabalho associados a este elemento. Para associar itens de trabalho, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).|
|**Descrição**|(blank)|Todos|Você pode fazer observações gerais sobre o item aqui.|
|**Cor**|(padrão para o tipo de elemento)|Linha da vida, mensagem|A cor da forma. Essa é uma propriedade da forma, em vez do elemento exibido.|
|**Tipo**|(blank)|Vital|O tipo da instância que a linha de vida representa.<br /><br /> Se houver um símbolo de referência exibido no cabeçalho da linha de vida, essa classe ou interface existirá separadamente no Gerenciador de modelos UML e poderá ser exibida em um diagrama de classe.|
|**Ator**|False|Vital|Indica se a linha de vida representa um componente de usuário, dispositivo ou software externo ao componente sobre o qual o diagrama se encontra.|
|**Quase**|**Concluir** -uma mensagem que tem o remetente e o destinatário.<br /><br /> **Encontrado** -uma mensagem que tem um remetente não especificado.<br /><br /> **Lost** -uma mensagem que tem um receptor não especificado.|Mensagem|Indica quais extremidades de uma mensagem são anexadas a uma linha da vida.<br /><br /> Você não pode alterar essa propriedade. Ele é definido quando você cria a mensagem.|
|**Organizar**|**AsynchCall** – uma mensagem assíncrona.<br /><br /> **SynchCall** -uma mensagem síncrona.<br /><br /> **Reply** -a parte de retorno de uma mensagem síncrona.<br /><br /> **CreateMessage** -uma mensagem de criação de instância.|Mensagem|O tipo de mensagem. Você não pode alterar essa propriedade. Ele é determinado pela ferramenta que você usa para criar a mensagem.|
|**Operacional**|esvaziá|Mensagem|Um método chamado pela mensagem na linha de vida de recebimento.<br /><br /> Visível somente se a linha de vida de recebimento estiver vinculada a uma interface ou uma classe.|
|**Refere-se a**|Um diagrama de sequência|Uso de interação|O diagrama de sequência chamado por esse uso de interação.|
|**Operador de interação**|Definido quando você usou o comando **surround with**|Fragmento combinado|O operador representado por este fragmento ou coleção de fragmentos.|
|**Proteja**|esvaziá|Operando de interação em um fragmento combinado|A sequência no fragmento não ocorrerá a menos que a proteção seja verdadeira.<br /><br /> Para selecionar o fragmento superior de qualquer fragmento combinado, clique abaixo do título do fragmento.|
|**Mín., máx.**|(sem restrição)|Fragmento combinado de loop|O número mínimo e máximo de vezes que o loop é executado.|
|**Mensagens**|esvaziá|Considere e<br /><br /> Ignorar fragmentos combinados|As mensagens que são consideradas ou ignoradas neste fragmento.|

## <a name="see-also"></a>Consulte também
 [Diagramas de sequência UML: referenciar](../modeling/uml-sequence-diagrams-reference.md) [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md) [descrevem o fluxo de controle com fragmentos em diagramas de sequência UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
