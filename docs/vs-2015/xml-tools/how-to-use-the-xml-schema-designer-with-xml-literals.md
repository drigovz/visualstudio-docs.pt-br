---
title: 'Como: usar o designer de esquema XML com literais XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656288"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Como: Use o designer de esquema XML com literais XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico descreve como exibir um esquema associado com um literal XML em um projeto Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Para criar um novo projeto de aplicativo de console do Visual Basic

1. Inicie o Visual Studio 2010.

2. No menu **Arquivo**, selecione **Novo** e em seguida **Projeto**. A caixa de diálogo **Novo Projeto** aparecerá. Para **tipos de projeto**, selecione **outros idiomas e,** em seguida, selecione **Visual Basic**. Para **modelos**, selecione aplicativo de console. Em seguida, digite `XMLLiterals` o campo **nome** e um local do projeto no campo **local** . Clique em **OK**.

     O novo poject é criado. O projeto de XMLLiterals contém um arquivo de origem Visual Basic, Module1.vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Para adicionar um arquivo XSD existente ao projeto

1. Abra um novo arquivo de texto no bloco de notas. Copie o código de exemplo do esquema XML do [esquema da ordem de compra](../xml-tools/sample-xsd-file-simple-schema.md) e cole-o no arquivo.

2. Salve o arquivo em qualquer local com o nome PurchaseOrderSchema.xsd.

3. Na Gerenciador de Soluções, clique com o botão direito do mouse no nome do projeto, selecione **Adicionar**e, em seguida, selecione **Item existente...**. A caixa de diálogo de **Item Addexisting** é exibida. Navegue até o arquivo PurchaseOrderSchema. xsd, selecione-o e clique em **Adicionar**.

     O projeto de XMLLiterals agora contém dois arquivos: Module1.vb e PurchaseOrderSchema.xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Para adicionar código Visual Basic com uma literal XML, com base no arquivo XSD incluído no projeto

1. Substitua o código no arquivo Module1.vb com o seguinte código:

    ```
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

    Module Module1
        Sub Main()

            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                                 <ns:ShipTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:ShipTo>
                                 <ns:BillTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:BillTo>
                             </ns:PurchaseOrder>

        End Sub
    End Module
    ```

2. Clique com o botão direito do mouse em qualquer nó XML em um literal XML ou em uma importação de namespace XML e selecione **Mostrar no Gerenciador de esquema**.

     XML Schema Explorer lado a lado é exibido com um arquivo Visual Basic que possui a literal XML assotiated com o esquema XML.
