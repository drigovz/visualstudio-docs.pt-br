---
title: 'Diagramas de classe UML: referência | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06e83e254cad77d4ede9716a18a51f6476fb51ad
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850177"
---
# <a name="uml-class-diagrams-reference"></a>Diagramas de classe UML: referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um diagrama de classe UML descreve as estruturas de objeto e de informações usadas pelo seu aplicativo, internamente e em comunicação com seus usuários. Ele descreve as informações sem referência a nenhuma implementação específica. Suas classes e relações podem ser implementadas de várias maneiras, como tabelas de banco de dados, nós XML ou composições de objetos de software.

> [!NOTE]
> Este tópico é sobre diagramas de classe UML. Há outro tipo de diagrama de classe, o diagrama de classes do .NET, que é usado para visualizar o código do programa. Para obter mais informações, consulte [projetando e exibindo classes e tipos](https://msdn.microsoft.com/library/ab7aty24.aspx).

 Para criar um diagrama de classes UML, no menu **arquitetura** , escolha **novo UML ou diagrama de camada**. Para obter mais informações sobre como desenhar diagramas de classe UML, consulte [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md). Para obter mais informações sobre como criar e desenhar diagramas de modelagem, consulte [Editar diagramas e modelos UML](../modeling/edit-uml-models-and-diagrams.md).

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lendo diagramas de classe
 A tabela nesta seção descreve os elementos que você pode ver em um diagrama de classes UML. Para obter informações sobre as propriedades desses elementos, consulte os seguintes tópicos:

- [Propriedades de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propriedades de operações em diagramas de classe UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Propriedades de associações em diagramas de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Três classes mostrando relações e propriedades](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **La** |       **Elemento**        |                                                                                                                                                             **Descrição**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Class**         |                                                           Uma definição de objetos que compartilham características estruturais ou comportamentais determinadas. Para obter mais informações, consulte [Propriedades de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Classificador        |                                                                                                             O nome geral para uma classe, interface ou enumeração. Componentes, casos de uso e atores também são classificadores.                                                                                                             |
|     2     | Recolher/expandir controle |                                                                                         Se você não puder ver os detalhes de um classificador, clique no expansor no canto superior esquerdo do classificador. Você também pode ter que clicar em [+] em cada segmento.                                                                                         |
|     3     |      **Attribute**       |   Um valor tipado anexado a cada instância de um classificador.<br /><br /> Para adicionar um atributo, clique na seção **atributos** e pressione **Enter**. Digite a assinatura do atributo. Para obter mais informações, consulte [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operação**       | Um método ou função que pode ser executado por instâncias de um classificador. Para adicionar uma operação, clique na seção **operações** e pressione **Enter**. Digite a assinatura da operação. Para obter mais informações, consulte [Propriedades de operações em diagramas de classe UML](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Associação**      |                                                                  Uma relação entre os membros de dois classificadores. Para obter mais informações, consulte [Propriedades de associações em diagramas de classe UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agregação**      |                                                                                                    Uma associação que representa uma relação de propriedade compartilhada. A propriedade **Aggregation** da função Owner é definida como **Shared**.                                                                                                     |
|    5b     |     **Composição**      |                                                                                                      Uma associação que representa uma relação de parte inteira. A propriedade **Aggregation** da função Owner é definida como **Composite**.                                                                                                      |
|     6     |   **Nome da Associação**   |                                                                                                                                         O nome de uma associação. O nome pode ser deixado em branco.                                                                                                                                          |
|     7     |      **Nome da função**       |                       O nome de uma função, ou seja, uma extremidade de uma associação. Pode ser usado para fazer referência ao objeto associado. Na ilustração anterior, para qualquer ordem `O`, `O.ChosenMenu` é seu menu associado.<br /><br /> Cada função tem suas próprias propriedades, listadas nas propriedades da associação.                       |
|     8     |     **Multiplicidade**     |                                         Indica quantos dos objetos nesse final podem ser vinculados a cada objeto no outro. No exemplo, cada pedido deve ser vinculado a exatamente um menu.<br /><br /> **\\** \* significa que não há nenhum limite superior para o número de links que podem ser feitos.                                         |
|     9     |    **Generalização**    |  O classificador *específico* herda parte de sua definição do classificador *geral* . O classificador geral está na extremidade da seta do conector. Os atributos, as associações e as operações são herdadas pelo classificador específico.<br /><br /> Use a ferramenta de **herança** para criar uma generalização entre dois classificadores.   |

 ![Pacote que contém a interface e a enumeração](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Forma|Elemento|Descrição|
|-----------|-------------|-----------------|
|10|**Interface**|Uma definição de parte do comportamento visível externamente de um objeto. Para obter mais informações, consulte [Propriedades de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeração**|Um classificador que consiste em um conjunto de valores literais.|
|12|**Pacote**|Um grupo de classificadores, associações, ações, linhas de vida, componentes e pacotes. Um diagrama de classe lógica mostra que os classificadores e os pacotes de membros estão contidos no pacote.<br /><br /> Os nomes são delimitados em pacotes, de forma que **Class1** dentro de **pacote1** seja diferente de **Class1** fora desse pacote. O nome do pacote aparece como parte das propriedades de **nome qualificado** de seu conteúdo.<br /><br /> Você pode definir a propriedade **pacote vinculado** de qualquer diagrama UML para se referir a um pacote. Todos os elementos que você criar nesse diagrama se tornarão parte do pacote. Eles aparecerão sob o pacote no **Gerenciador de modelos UML**.|
|13|**Import**|Uma relação entre pacotes, indicando que um pacote inclui todas as definições de outro.|
|14|**Dependência**|A definição ou implementação do classificador dependente pode mudar se o classificador na extremidade da ponta de seta for alterado.|

 ![Realização mostrada com conector e pirulito](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Forma|**Elemento**|Descrição|
|-----------|-----------------|-----------------|
|15|**Percepção**|A classe implementa as operações e os atributos definidos pela interface.<br /><br /> Use a ferramenta de **herança** para criar uma realização entre uma classe e uma interface.|
|16|**Percepção**|Uma apresentação alternativa da mesma relação. O rótulo no símbolo de pirulito identifica a interface.<br /><br /> Para criar essa apresentação, selecione uma relação de realização existente. Uma marca de ação aparece próxima à associação. Clique na marca de ação e, em seguida, clique em **mostrar como pirulito**.|

## <a name="see-also"></a>Veja também
 [Editar modelos UML e diagramas](../modeling/edit-uml-models-and-diagrams.md) [diagramas de classes UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md) [Propriedades de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Propriedades de operações em diagramas de classe UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Propriedades de associações em diagramas de classe UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)
