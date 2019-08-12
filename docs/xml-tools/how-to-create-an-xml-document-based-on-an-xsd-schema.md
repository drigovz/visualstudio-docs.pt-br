---
title: 'Como: Criar um documento XML baseado em um esquema XSD'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7739f33bad62667fdc7be8704237ebdd3932739c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918557"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Como: Criar um documento XML baseado em um esquema XSD

O recurso **gerar XML de exemplo** gera um arquivo XML de exemplo baseado em seu arquivo de esquema XML (XSD).

Você pode usar esta opção para os seguintes situações:

- Para entender o uso de várias construções no seu esquema.

- Para confirmar que o esquema faz o que é esperado dele.

O recurso **gerar XML de exemplo** só está disponível em elementos globais e requer um conjunto de esquema XML válido.

Esse recurso normalmente gera documentos XML válidos. No entanto, se o esquema contiver um ou mais dos seguintes, o exemplo poderá não ser válido:

- As restrições de identidade `xs:key`, `xs:keyref` e `xs:unique`.

- `xs:pattern` facetas.

- Enumerações do tipo `xs:QName`.

- Tipos `xs:ENTITY`, `xs:ENTITIES` e `xs:NOTATION`.

Além disso, observe que o conteúdo de `xs:base64Binary` será gerado apenas se as enumerações ocorrerem no esquema para esse tipo.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Para gerar um documento de instância XML baseado no arquivo XSD

1. Siga as etapas em [como: Crie e edite um arquivo](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)de esquema XSD.

2. No [XML Schema Explorer](../xml-tools/xml-schema-explorer.md), clique com o botão direito `PurchaseOrder` do mouse no elemento global. Selecione **gerar XML de exemplo**.

     Quando você seleciona essa opção, o PurchaseOrder. o arquivo *XML* com o seguinte conteúdo XML de exemplo será gerado e aberto no editor de XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```