---
title: Trechos de código XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66736431b295f974bda1ca855d88cd5f5f868e7d
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526145"
---
# <a name="xml-snippets"></a>Trechos de código XML

O editor XML oferece um recurso, chamado *trechos XML*, que permite que você criar arquivos XML mais rapidamente. Você pode reutilizar XML inserindo snippets nos seus arquivos. Você também pode gerar dados XML com base em um esquema XSD (linguagem) de definição de esquema XML.

## <a name="reusable-xml-snippets"></a>Trechos de código reutilizáveis XML

O editor XML inclui muitos trechos que abrangem algumas tarefas comuns. Isso permite que você crie arquivos XML mais facilmente. Por exemplo, se você estivesse criando um esquema XML, usar os trechos de código "Elemento de sequência de tipo complexo" e "Elemento de tipo simples" insere o seguinte texto XML ao seu arquivo. Você alteraria o valor de `name` para atender às suas necessidades.

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

Você pode inserir snippets de duas maneiras. O **Inserir trecho** comando insere o trecho XML a posição do cursor. O **envolver com** comando encapsula o trecho XML ao redor do texto selecionado. Ambos os comandos estão disponíveis do **IntelliSense** submenu sob o **editar** menu, ou no menu do botão direito do mouse no editor.

Para obter mais informações, confira [Como: Usar trechos de código XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Trechos XML gerados por esquema

O editor XML também tem a capacidade de gerar um trecho XML de um esquema XML. Esse recurso permite que você popule um elemento com elementos XML gerados de informações de esquema para esse elemento. Para obter mais informações, confira [Como: Gerar um trecho XML a partir de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Criar novos trechos XML

Além dos trechos que são incluídos com o Visual Studio, por padrão, você também pode criar e usar seus próprios trechos XML. Para obter mais informações, confira [Como: Criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Consulte também

- [Trechos de código no Visual Studio](../ide/code-snippets.md)
- [Editor de XML](../xml-tools/xml-editor.md)