---
title: 'Diagramas de caso de uso UML: referência | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657300"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagramas de caso de uso UML: referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, um *diagrama de caso de uso* resume quem usa seu aplicativo ou sistema e o que ele pode fazer com ele. Para criar um diagrama de caso de uso UML, no menu **arquitetura** , clique em **novo UML ou diagrama de camada**.

 Um diagrama de caso de uso atua como um foco para a descrição dos requisitos do usuário. Ele descreve as relações entre os requisitos, os usuários e os principais componentes. Ele não descreve os requisitos em detalhes; Eles podem ser descritos em diagramas separados ou em documentos que podem ser vinculados a cada caso de uso. Para obter informações sobre como os diagramas de caso de uso podem ajudá-lo a entender, discutir e comunicar as necessidades dos usuários, consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Este tópico descreve os elementos que estão disponíveis em diagramas de caso de uso. Para obter mais informações sobre como desenhar diagramas de caso de uso, consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md). Para obter mais informações sobre como criar e desenhar diagramas de modelagem, consulte [Editar diagramas e modelos UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-use-case-diagrams"></a>Lendo diagramas de caso de uso
 As tabelas nas seções a seguir descrevem os elementos que estão disponíveis em um diagrama de caso de uso, junto com suas propriedades principais. Para obter uma lista completa de propriedades, consulte [Propriedades de elementos em diagramas de caso de uso UML](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).

### <a name="actors-use-cases-and-subsystems"></a>Atores, casos de uso e subsistemas
 ![Elementos em um diagrama de caso de uso](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**Forma**|**Element**|**Descrição e propriedades principais**|
|---------------|-----------------|-----------------------------------------|
|1|**Ator**|Representa um usuário, uma organização ou um sistema externo que interage com seu aplicativo ou sistema. Um ator é um tipo de tipo.<br /><br /> -   **Caminho da imagem** -o caminho do arquivo de uma imagem que deve ser usada em vez do ícone de ator padrão. O ícone deve ser um arquivo de recurso no projeto do Visual Studio.|
|2|**Caso de uso**|Representa as ações executadas por um ou mais atores na busca de uma meta específica. Um caso de uso é um tipo de tipo.<br /><br /> -   **Assuntos** -o subsistema no qual o caso de uso é exibido.|
|3|**Associação**|Indica que um ator faz parte em um caso de uso.|
|4|**Subsistema ou componente**|O sistema ou aplicativo no qual você está trabalhando, ou uma parte dele. Pode ser qualquer coisa de uma rede grande para uma única classe em um aplicativo.<br /><br /> Os casos de uso que um sistema ou componente dá suporte aparecem dentro de seu retângulo. Pode ser útil mostrar alguns casos de uso fora do retângulo, para esclarecer o escopo do seu sistema.<br /><br /> Um subsistema em um diagrama de caso de uso tem basicamente o mesmo tipo de um componente em um diagrama de componente.<br /><br /> -   **É instanciado indiretamente** -se for false, o sistema em execução terá um ou mais objetos que correspondem diretamente a esse subsistema. Se for true, o subsistema será um constructo no design que aparece no sistema em execução somente por meio da instanciação de suas partes constituintes.|

### <a name="structuring-use-cases"></a>Estruturando casos de uso
 ![Casos de uso com include, Extend e generalização](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|Forma|**Element**|Descrição|
|-----------|-----------------|-----------------|
|5|**Incluir**|Um que inclui o caso de uso chama ou invoca o incluído. A inclusão é usada para mostrar como um caso de uso é dividido em etapas menores. O caso de uso incluído está na extremidade da ponta de seta.<br /><br /> Observe que o diagrama não mostra a ordem das etapas. Você pode usar um diagrama de atividade, um diagrama de sequência ou outro documento para descrever esses detalhes.|
|6|**Estender**|Um caso de uso de extensão adiciona metas e etapas ao caso de uso estendido. As extensões operam somente sob determinadas condições. O caso de uso estendido está na extremidade da ponta de seta.<br /><br /> Observe que o diagrama não mostra as circunstâncias exatas sob as quais a extensão se aplica: você pode gravá-los em um comentário ou em outro documento.|
|7|**Herança**|Relaciona um elemento especializado e generalizado. O elemento generalizado está na extremidade da ponta de seta.<br /><br /> Um caso de uso especializado herda as metas e os atores de sua generalização e pode adicionar metas e etapas mais específicas para atingi-las.<br /><br /> Um ator especializado herda os casos de uso, os atributos e as associações de sua generalização e pode adicionar mais.|
|8|**Dependência**|Indica que o design da origem depende do design do destino.|
|9|**Comentário**|Usado para adicionar notas gerais ao diagrama.|
|10|**Artefato**|Um artefato fornece um link para outro diagrama ou documento. Você pode criá-lo arrastando um arquivo de Gerenciador de Soluções. Ele pode ser vinculado com uma dependência a qualquer outro elemento no diagrama. Um artefato normalmente é usado para vincular um caso de uso a um diagrama de sequência, uma página do OneNote, um documento do Word ou uma apresentação do PowerPoint que o descreve detalhadamente. O documento pode ser um item na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solução ou um documento em um local compartilhado, como um site do SharePoint.<br /><br /> -   **Hiperlink**. A URL ou o caminho do arquivo do diagrama ou documento.<br /><br /> Clique duas vezes em um artefato para abrir o arquivo ou a página da Web à qual ele se vincula.|
|11 (não mostrado)|**Pacotes**|Casos de uso, atores e subsistemas podem ser contidos em pacotes. As formas de pacote não aparecem no diagrama, mas você pode definir a propriedade **LinkedPackage** do diagrama. Os elementos que você cria posteriormente no diagrama são colocados dentro do pacote. Para obter mais informações, consulte [definir pacotes e namespaces](../modeling/define-packages-and-namespaces.md).|

## <a name="see-also"></a>Consulte Também
 [Diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md) [editar modelos UML e](../modeling/edit-uml-models-and-diagrams.md) diagramas [diagramas de sequência UML: referenciar](../modeling/uml-sequence-diagrams-reference.md) [diagramas de classe UML: referenciar](../modeling/uml-class-diagrams-reference.md) diagramas de [componentes UML: referência](../modeling/uml-component-diagrams-reference.md) a [diagramas de componentes UML: referência](../modeling/uml-component-diagrams-reference.md)
