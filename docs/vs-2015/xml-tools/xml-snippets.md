---
title: Trechos XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669357"
---
# <a name="xml-snippets"></a>Snippets XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor de XML oferece um recurso, chamado *trechos XML*, que permite criar arquivos XML mais rapidamente. Você pode reutilizar XML inserindo snippets nos seus arquivos. Você também pode gerar os dados XML com base no esquema de linguagem de definição de esquema XML (XSD).

## <a name="reusable-xml-snippets"></a>Snippets reutilizáveis XML
 O editor XML inclui muitos snippets que abrangem algumas tarefas comuns. Isso permite que você crie arquivos XML mais facilmente. Por exemplo, se você estivesse criando um esquema XML, usando o elemento de sequência tipo complexo” e “os snippets do elemento tipo simples” inserir o seguinte texto XML para o arquivo. Você alteraria o valor de `name` para atender às suas necessidades.

```
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

 Você pode inserir snippets de duas maneiras. O comando **Insert Snippet** insere o trecho XML na posição do cursor. O comando **surround with** encapsula o trecho XML em torno do texto selecionado. Ambos os comandos estão disponíveis no submenu **IntelliSense** , no menu **Editar** , ou no menu de atalho do editor.

 Para obter mais informações, consulte [como: usar trechos XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Snippets Esquema- gerados XML
 O editor XML também tem a capacidade de gerar um snippet de um esquema XML. Esse recurso permite que você popule um elemento com elementos XML gerados de informações de esquema para esse elemento.

 Para obter mais informações, consulte [como gerar um trecho XML a partir de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Crie novos snippets XML
 Além dos trechos de código incluídos no [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio por padrão, você também pode criar e usar seus próprios trechos de código XML.

 Para obter mais informações, consulte [como: criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Consulte também
 [Editor de XML](../xml-tools/xml-editor.md)
