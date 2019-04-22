---
title: Trechos de código XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e2fbba9006c1621b8f98084d4ffd4c637be1127
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654649"
---
# <a name="xml-snippets"></a>Snippets XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Editor XML oferece um recurso, chamado *trechos XML*, que permite que você criar arquivos XML mais rapidamente. Você pode reutilizar XML inserindo snippets nos seus arquivos. Você também pode gerar os dados XML com base no esquema de linguagem de definição de esquema XML (XSD).  
  
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
  
 Você pode inserir snippets de duas maneiras. O **Inserir trecho** comando insere o trecho XML a posição do cursor. O **envolver com** comando encapsula o trecho XML ao redor do texto selecionado. Ambos os comandos estão disponíveis do **IntelliSense** submenu sob o **editar** menu, ou no menu de atalho do editor.  
  
 Para obter mais informações, confira [Como: Usar trechos de código XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Snippets Esquema- gerados XML  
 O editor XML também tem a capacidade de gerar um snippet de um esquema XML. Esse recurso permite que você popule um elemento com elementos XML gerados de informações de esquema para esse elemento.  
  
 Para obter mais informações, confira [Como: Gerar um trecho XML a partir de um esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Crie novos snippets XML  
 Além dos trechos que são incluídos com [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio por padrão, você também pode criar e usar seus próprios trechos XML.  
  
 Para obter mais informações, confira [Como: Criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Consulte também  
 [Editor de XML](../xml-tools/xml-editor.md)
