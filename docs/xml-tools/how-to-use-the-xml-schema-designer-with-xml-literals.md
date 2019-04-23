---
title: 'Como: Usar o designer de esquema XML com literais XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9e92cbdca3ac2c5c366ec054ba79f2e7324986c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067606"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Como: Usar o designer de esquema XML com literais do XML

Este tópico descreve como exibir um esquema associado com um literal XML em um projeto Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Criar um novo projeto do Visual Basic

1. Abra o Visual Studio.

2. Criar um novo Visual Basic **aplicativo de Console** projeto chamado **XMLLiterals**.

     O novo projeto contém um arquivo de origem do Visual Basic, *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Adicionar um arquivo XSD existente

1. Abra um novo arquivo de texto no bloco de notas. Copie o código de exemplo de esquema XML do [esquema de ordem de compra](../xml-tools/sample-xsd-file-simple-schema.md) e cole-a para o arquivo.

2. Salve o arquivo em algum local com o nome *Purchaseorderschema*.

3. Na **Gerenciador de soluções**, o nome do projeto com o botão direito, selecione **Add**e, em seguida, selecione **Item existente**. O **AddExisting Item** caixa de diálogo é exibida. Navegue até a *Purchaseorderschema* do arquivo, selecione-o e, em seguida, clique em **Add**.

     O projeto de XMLLiterals agora contém dois arquivos: *Module1.vb* e *Purchaseorderschema*.

## <a name="add-code"></a>Adicione o código

Para adicionar o código do Visual Basic com uma literal XML, com base no arquivo XSD incluído no projeto:

1. Substitua o código em *Module1.vb* arquivo pelo código a seguir:

   ```vb
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

2. Qualquer nó XML em um literal XML ou uma importação de namespace XML com o botão direito e selecione **Mostrar no Schema Explorer**.

   O **XML Schema Explorer** é exibido lado a lado com um arquivo de Visual Basic que possui o literal XML associado com o conjunto de esquema XML.