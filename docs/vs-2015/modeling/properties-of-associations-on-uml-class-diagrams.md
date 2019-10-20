---
title: Propriedades de associações em diagramas de classe UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c5c914d87f0740dcd7b0f71190a4c2f54727f66
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652086"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Propriedades de associações em diagramas de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de classes UML, você pode desenhar *associações* entre qualquer par de tipos. Um tipo é uma classe, interface ou enumeração.

 Uma associação indica que o sistema que você está desenvolvendo armazena links de algum tipo entre as instâncias dos tipos associados. Em geral, ele não implica nada sobre a implementação dos links. Por exemplo, eles podem ser ponteiros, linhas em uma tabela, nomes de referência cruzada em XML e assim por diante.

 Uma associação é um método diagramáticas de mostrar um atributo ou um par de atributos. Por exemplo, se você tiver definido um restaurante de classe para ter um atributo do tipo menu, poderá declarar a mesma definição desenhando uma associação entre o restaurante e o menu.

 Para desenhar uma associação, clique em **Associação** na caixa de ferramentas, clique no primeiro tipo e, em seguida, no segundo. Você pode clicar no mesmo tipo duas vezes para mostrar que as instâncias podem ser vinculadas a outras instâncias do mesmo tipo.

## <a name="properties"></a>Propriedades
 Essas são as propriedades de uma associação em um diagrama de classes UML.

 Para ver as propriedades de uma associação, clique com o botão direito do mouse na associação e clique em **Propriedades**. As propriedades serão exibidas no janela Propriedades.

 Algumas das propriedades também são visíveis no diagrama, conforme mostrado na ilustração a seguir.

 ![Propriedades em associações](../modeling/media/uml-classprop.png "UML_ClassProp")

|**Property**|Descrição|
|------------------|-----------------|
|**Nome (1)**|Identifica a associação. Também aparece no diagrama próximo ao ponto intermediário da associação.|
|**Nome qualificado**|Identifica a associação exclusivamente. Prefixado com o nome qualificado do pacote que contém a primeira função da associação.|
|**Itens de trabalho**|O número de itens de trabalho vinculados a essa associação. Para vincular itens de trabalho, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).|
|**Cor**|A cor do conector. Ao contrário das outras propriedades, essa é uma propriedade dessa exibição da associação, não uma propriedade da relação subjacente no modelo.|
|**Primeira função**<br /><br /> **Segunda função**|Cada extremidade da associação é chamada de função. Cada função descreve as propriedades do atributo equivalente na classe na extremidade oposta da associação.<br /><br /> No diagrama de exemplo, a associação entre o menu e o item de menu tem funções chamadas de menu e conteúdo.<br /><br /> Contents é o nome de um atributo na classe de menu.|

### <a name="properties-of-each-role"></a>Propriedades de cada função
 Para ver as propriedades de cada função, expanda a **primeira função** ou a segunda propriedade de **função** .

|     **Property**     |          **Padrão**          |                                                                                                                                                                                                                                                                                                                                        Descrição                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Nome da função (2)**   | Nome do tipo nesta função |                                                                                                                                                                                                                                                                                                       O nome da função. Aparece próximo ao final da associação no diagrama.                                                                                                                                                                                                                                                                                                        |
|   **Agregação**    |             Nenhum              |                                                                        **Nenhum** (4) – representa uma relação geral entre instâncias das classes.<br /><br /> **Composição** (5)-o objeto nessa função contém o objeto na função oposta. Você pode usar a ferramenta **composta** para criar uma associação com agregação composta.<br /><br /> **Compartilhado** (6)-o objeto nesta função contém referências ao objeto na outra função. Você pode usar a ferramenta de **agregação** para criar uma associação com agregação compartilhada.<br /><br /> A interpretação exata está aberta para a Convenção local.                                                                         |
|    **É derivado**    |             False             |                                                                                                                                                                                                                          Se for true, o objeto nessa extremidade do link será calculado de outros atributos e associações. Por exemplo, MyWorkPlace calculada de myempregador. WorkPlace. Os detalhes devem ser digitados na descrição ou em um comentário anexado.                                                                                                                                                                                                                           |
| **É Union derivada** |             False             |                                                                                                                                                                                                                                                                                                             Se for true, a função será a União de um conjunto de funções em tipos derivados.                                                                                                                                                                                                                                                                                                             |
|   **É navegável**   |             verdadeiro              |                                                 A associação pode ser lida nessa direção. Dada uma instância da função oposta, o software que você está descrevendo pode determinar com eficiência a instância associada nessa função.<br /><br /> Se uma função for navegável e a outra não for, uma seta será exibida (7) na associação na direção navegável.<br /><br /> Por padrão, a ferramenta de associação cria uma associação que é navegável em uma direção. Para convertê-lo em uma associação bidirecional, você pode selecionar a associação, clicar na marca de ação que aparece e, em seguida, clicar em **tornar bidirecional**.                                                 |
|   **É somente leitura**   |             False             |                                                                                                                                                                                                                                                                                   Se for true, uma instância da associação não poderá ser alterada depois de ser criada. O link é sempre para o mesmo objeto.                                                                                                                                                                                                                                                                                    |
| **Multiplicidade (3)** |               1               | **1** -essa extremidade da Associação sempre se vincula a um objeto. Na figura, cada item de menu tem um menu.<br /><br /> **0.. 1** -essa extremidade da Associação vincula a um objeto ou não há nenhum link.<br /><br /> **\\** \*-todos os objetos na outra extremidade da associação estão vinculados a uma coleção de objetos nesse final, e a coleção pode estar vazia.<br /><br /> **1.. \\** \*-todos os objetos na outra extremidade da associação estão vinculados a pelo menos um objeto neste final. Na figura, cada menu tem pelo menos um item de menu.<br /><br /> *n* **..** *m* -cada objeto na outra extremidade tem uma coleção de entre *n* e *m* links para objetos neste fim. |
|    **É ordenado**    |             False             |                                                                                                                                                                                                                                                                                                  Se for true, a coleção retornada formará uma lista sequencial. Para multiplicidade maior que 1.                                                                                                                                                                                                                                                                                                   |
|    **É exclusivo**     |             False             |                                                                                                                                                                                                                                                                                              Se for true, não haverá valores duplicados na coleção retornada. Para multiplicidade maior que 1.                                                                                                                                                                                                                                                                                              |
|    **Visibilidade**    |            Público             |                                                                                                                                                                                                                                 Público-visível globalmente<br /><br /> Privado – não visível fora do tipo proprietário<br /><br /> Protegido – visível para tipos derivados do proprietário<br /><br /> Pacote-visível para outros tipos dentro do mesmo pacote.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Consulte também
 [Diagramas de classe UML:](../modeling/uml-class-diagrams-reference.md) [Propriedades de referência de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Propriedades de operações em diagramas de](../modeling/properties-of-operations-on-uml-class-diagrams.md) classe UML [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)
