---
title: Propriedades de atributos em diagramas de classe UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652062"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Propriedades de atributos em diagramas de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de classes UML, você pode adicionar *atributos* a classes e interfaces. Um atributo define os valores que podem ser anexados a instâncias da classe ou interface.

 Para adicionar um atributo, clique com o botão direito do mouse na classe ou interface, aponte para **Adicionar**e clique em **atributo**.

 Se os atributos de uma classe no diagrama não estiverem visíveis, clique na divisa na parte superior da classe ou interface para expandi-la. Se você puder ver o cabeçalho **atributos** , clique em **[+]** para expandir a seção atributos.

## <a name="signature-of-an-attribute"></a>Assinatura de um atributo
 A assinatura de um atributo é a linha que a representa em uma classe ou interface em um diagrama de classe UML. Ele tem este formato:

```
+ AttributeName : TypeName [*]
```

 \+ denota a visibilidade pública. Os outros valores permitidos são-(particular), # (protegido), ~ (pacote).

 `AttributeName` será sublinhado se o atributo for estático.

 `: TypeName` será omitido se o atributo não tiver nenhum tipo.

 `[*]` denota a multiplicidade. Será omitido se a multiplicidade for 1.

## <a name="properties"></a>Propriedades
 A tabela a seguir descreve as propriedades de um atributo em uma classe ou interface em um diagrama de classe UML.

 Para ver as propriedades de um atributo, clique com o botão direito do mouse no atributo na classe ou interface no diagrama e clique em **Propriedades**. As propriedades são exibidas na janela Propriedades.

 Para exibir as propriedades de um atributo, clique com o botão direito do mouse nele e clique em **Propriedades**.

|   **Propriedade**    | **Default**  |                                                                                                                                                                                                         Descrição                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valor padrão** |   (vazio)    |                                                                                                                                                                               O valor do atributo quando o classificador é instanciado.                                                                                                                                                                                |
| **É somente leitura**  |    Falso     |                                                                                                                                                                                    Se for true, o valor do atributo não poderá ser alterado.                                                                                                                                                                                    |
|   **Is Static**   |    Falso     |                                                                                                                    Se for true, um único valor para esse atributo será compartilhado entre todas as instâncias desse tipo.<br /><br /> Se for true, o nome do atributo será sublinhado onde ele aparece no diagrama.                                                                                                                    |
|     **Nome**      | (um novo nome) |                                                                                                                                                                                        Deve ser exclusivo dentro do classificador proprietário.                                                                                                                                                                                        |
|     **Tipo**      |    (nenhum)    |                                                Um tipo primitivo, como **inteiro**, ou um tipo que é definido no modelo. Você não pode usar tipos não primitivos, como **decimal** , porque o valor deve ser codificado nos metadados. Se você inserir um nome para um novo tipo nessa propriedade, um tipo será adicionado à seção **tipos não especificados** do Gerenciador de modelos UML.                                                 |
|  **Visibilidade**   |    Público    |                                     Os valores permitidos e os caracteres que aparecem na assinatura são os seguintes:<br /><br /> **+ Público** -visível globalmente<br /><br /> **-Private** – não é visível fora do tipo proprietário<br /><br /> **# Protected** -visível para tipos derivados do proprietário<br /><br /> **~ Pacote** -visível para outros tipos dentro do mesmo pacote.                                      |
|  **Itens de trabalho**   | 0 associado |                                                                                                                          Contagem de itens de trabalho associados. Somente leitura.<br /><br /> Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **É folha**    |    Falso     |                                                                                                                                                                    Se for true, ele não se destina a permitir a redefinição desse atributo em tipos derivados.                                                                                                                                                                     |
|  **Is Derived**   |    Falso     |                                                                                                              Se for true, esse atributo será calculado de outros atributos. Por exemplo, diagonal, calculada a partir da largura e da altura. Os detalhes devem ser escritos na **Descrição** ou em um comentário anexado.                                                                                                              |
|  **Descrição**  |   (vazio)    |                                                                                                                                                                        Para observações gerais ou para definir restrições nos valores no atributo.                                                                                                                                                                        |
| **Multiplicidade**  |      1       | **1** -este atributo tem um único valor do tipo especificado.<br /><br /> **0.. 1** -esse atributo pode ter um valor de `null` .<br /><br /> **\\**\* -o valor deste atributo é uma coleção de valores.<br /><br /> **1.. \\ ** \* -o valor deste atributo é uma coleção que contém pelo menos um valor.<br /><br /> *n* **..** *m* -o valor deste atributo é uma coleção que contém entre *n* e *m* valores. |
|  **Is Ordered**   |    Falso     |                                                                                                                                                                    Se for true, a coleção formará uma lista sequencial. Para **multiplicidade** de mais de 1.                                                                                                                                                                     |
|   **É Exclusivo**   |    Falso     |                                                                                                                                                                Se for true, não haverá valores duplicados na coleção. Para **multiplicidade** de mais de 1.                                                                                                                                                                |

## <a name="see-also"></a>Consulte Também
 [Diagramas de classe UML:](../modeling/uml-class-diagrams-reference.md) [Propriedades de referência de tipos em diagramas de classe UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [Propriedades de operações em diagramas](../modeling/properties-of-operations-on-uml-class-diagrams.md) de classe UML [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md) [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)
