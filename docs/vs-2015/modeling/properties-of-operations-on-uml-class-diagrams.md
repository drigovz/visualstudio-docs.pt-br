---
title: Propriedades de operações em diagramas de classe UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671348"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Propriedades de operações em diagramas de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de classes UML, você pode adicionar *operações* a classes e interfaces. Uma operação é um método ou uma função que pode ser executada por uma instância de uma classe ou interface.

 Para adicionar uma operação, clique com o botão direito do mouse na classe ou interface, aponte para **Adicionar**e clique em **operação**.

 Se as operações de uma classe no diagrama não estiverem visíveis, clique na divisa de expansão na parte superior da classe ou da interface. Se você puder ver o cabeçalho da **operação** , clique em **[+]** para expandir a seção operações.

## <a name="signature-of-an-operation"></a>Assinatura de uma operação
 A assinatura de uma operação é a linha de texto que a representa em uma classe ou interface em um diagrama de classe UML. Ele tem o seguinte formato:

 \+ OperationName (parâmetro1: type1 [*],...): ReturnType [ \* ]

 \+ denota a visibilidade pública. Os outros valores permitidos são-(particular), # (protegido), ~ (pacote).

 `OperationName` será sublinhado se a propriedade **is static** for true e for Italic se a propriedade **is abstract** for true.

 `: ReturnType` será omitido se nenhum tipo de retorno for definido.

 `[*]` denota a multiplicidade de um parâmetro ou tipo de retorno. Será omitido se a multiplicidade for 1.

 Consulte a próxima seção para obter uma descrição completa dessas propriedades.

## <a name="properties"></a>Propriedades
 Essas são as propriedades de uma operação em uma classe ou interface em um diagrama de classes UML.

 Para ver as propriedades de uma operação, clique com o botão direito do mouse na operação na classe ou interface no diagrama e clique em **Propriedades**. As propriedades aparecem na janela **Propriedades** .

|      Propriedade       |   Padrão    |                                                                                                                                                                                 Descrição                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Nome**       | (um novo nome) |                                                                                                                                                                Deve ser exclusivo dentro do tipo recipiente.                                                                                                                                                                 |
|   **Parâmetros**    |    (nenhum)    |      Uma lista com o <em>nome</em>do formulário **:**<em>tipo</em>**,** <em>nome</em>**:**<em>tipo</em>**,....** Clique em **[...]** para editar a lista.<br /><br /> Os tipos podem ser tipos primitivos ou tipos que são definidos no modelo. Se você inserir um nome para um novo tipo nessa propriedade, um tipo será adicionado à seção **tipos não especificados** do Gerenciador de modelos UML.      |
|   **Tipo de retorno**   |    (nenhum)    |                                                                               **(nenhum)**, ou um tipo primitivo, ou um tipo que é definido no modelo. Se você inserir um nome para um novo tipo nessa propriedade, um tipo será adicionado à seção **tipos não especificados** do Gerenciador de modelos UML.                                                                                |
| **Pós-condições**  |    (nenhum)    |                                                                                                                         Uma condição opcional que especifica uma relação entre o estado do sistema antes e depois da execução da operação.                                                                                                                         |
|  **Pré-condições**  |    (nenhum)    |                                                                                                                            Uma condição opcional que especifica as suposições sobre o estado do sistema antes que a operação comece a ser executado.                                                                                                                            |
| **Condições do corpo** |    (nenhum)    |                                                                                                                                                       Uma restrição opcional nos valores retornados pela operação.                                                                                                                                                       |
|   **Visibilidade**    |    Público    |                  Os valores permitidos e os caracteres que aparecem na assinatura são:<br /><br /> **+ Público** -visível globalmente<br /><br /> **-Private** – não é visível fora do tipo proprietário<br /><br /> **# Protected** -visível para tipos derivados do proprietário<br /><br /> **~ Pacote** -visível para outros tipos dentro do mesmo pacote.                   |
|    **Assinatura**    |  +*Nome*()   |                                                                                      Resume a visibilidade, o nome, os parâmetros e o tipo de retorno dessa operação. Você pode alterar essas propriedades editando a assinatura no diagrama ou editando as propriedades individuais.                                                                                      |
|   **Itens de trabalho**    | 0 associado |                                                                                                  Contagem de itens de trabalho associados. Somente leitura.<br /><br /> Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Simultaneidade**   |  Sequencial  | **Sequencial** -a operação é ou será projetada sem controle de simultaneidade. Chamar essa operação simultaneamente pode resultar em falhas.<br /><br /> **Protegido** – a operação será bloqueada automaticamente até que outras instâncias da TI sejam concluídas.<br /><br /> **Simultâneo** – a operação é projetada para que várias chamadas para ela possam ser executadas simultaneamente. |
|    **Is Static**    |    Falso     |                                                                                                  Se for true, essa operação será compartilhada entre todas as instâncias desse tipo.<br /><br /> Se for true, o nome da operação será sublinhado onde aparece no diagrama.                                                                                                   |
|   **É Abstrato**   |    Falso     |                                                                                                                                        Se for true, nenhum código será associado a essa operação. Portanto, a classe proprietária é abstract.                                                                                                                                         |
|     **É folha**     |    Falso     |                                                                                                                                              O designer pretenderá que essa operação não possa ser substituída em classes derivadas.                                                                                                                                              |
|    **Is Query**     |    Falso     |                                                                                                 Se for true, nenhuma alteração significativa no estado do sistema será feita por essa operação. Portanto, ele pode ser usado, por exemplo, em um teste para verificar o estado do sistema.                                                                                                  |
|  **Multiplicidade**   |      1       |                                 **1** -um único valor do tipo especificado.<br /><br /> **0.. 1** -pode ser `null` .<br /><br /> \* -uma coleção de valores do tipo especificado.<br /><br /> **1.. \\ ** \* -uma coleção que contém pelo menos um valor.<br /><br /> *n* `..` *m* -uma coleção que contém `n` `m` os valores e.                                  |
|   **Is Ordered**    |    Falso     |                                                                                                                                             Se for true, a coleção formará uma lista sequencial. Para **multiplicidade** maior que 1.                                                                                                                                              |
|    **É Exclusivo**    |    Falso     |                                                                                                                                         Se for true, não haverá valores duplicados na coleção. Para **multiplicidade** maior que 1.                                                                                                                                         |

## <a name="see-also"></a>Consulte Também
 [Diagramas de classe UML:](../modeling/uml-class-diagrams-reference.md) [Propriedades de referência de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Propriedades de associações em diagramas de classe UML](../modeling/properties-of-associations-on-uml-class-diagrams.md) [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)
