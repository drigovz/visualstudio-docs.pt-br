---
title: Snippets XML
description: Saiba mais sobre o recurso de trechos de código XML no editor de XML que permite que você crie arquivos XML mais rapidamente reutilizando trechos de código XML e inserindo-os em seus arquivos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9114d50abd8f12e19f67d593927b94afcb010f6
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350186"
---
# <a name="xml-snippets"></a>Snippets XML

O editor de XML oferece um recurso, chamado *trechos XML* , que permite criar arquivos XML mais rapidamente. Você pode reutilizar XML inserindo snippets nos seus arquivos. Você também pode gerar dados XML com base em um esquema XSD (linguagem de definição de esquema XML).

## <a name="reusable-xml-snippets"></a>Trechos de código XML reutilizáveis

O editor de XML inclui muitos trechos de código que abrangem algumas tarefas comuns. Isso permite que você crie arquivos XML mais facilmente. Por exemplo, se você estivesse criando um esquema XML, usar os trechos de código "elemento de sequência de tipo complexo" e "elemento de tipo simples" insere o seguinte texto XML em seu arquivo. Você alteraria o valor de `name` para atender às suas necessidades.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Você pode inserir snippets de duas maneiras. O comando **Insert Snippet** insere o trecho XML na posição do cursor. O comando **surround with** encapsula o trecho XML em torno do texto selecionado. Ambos os comandos estão disponíveis no submenu **IntelliSense** , no menu **Editar** , ou no menu de atalho dentro do editor.

Para obter mais informações, consulte [como: usar trechos XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Trechos XML gerados pelo esquema

O editor de XML também tem a capacidade de gerar um trecho XML a partir de um esquema XML. Esse recurso permite que você popule um elemento com elementos XML gerados de informações de esquema para esse elemento. Para obter mais informações, consulte [como gerar um trecho XML a partir de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Criar novos trechos XML

Além dos trechos de código incluídos no Visual Studio por padrão, você também pode criar e usar seus próprios trechos de código XML. Para obter mais informações, consulte [como: criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Veja também

- [Snippets de código no Visual Studio](../ide/code-snippets.md)
- [Editor de XML](../xml-tools/xml-editor.md)
