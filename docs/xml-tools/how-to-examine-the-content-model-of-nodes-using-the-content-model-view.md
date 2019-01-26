---
title: Examinar o modelo de conteúdo de nós usando o modo de exibição do modelo de conteúdo no Designer de esquema XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a8f1f3a6897e64c58245ac336cb42074db3e262
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930941"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Como: Examinar o modelo de conteúdo de nós usando a exibição do modelo de conteúdo

Este tópico descreve como explorar os nós usando o [modo de exibição do modelo de conteúdo](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo

1.  Crie um novo arquivo de esquema XML.

2.  Clique em **Use o Editor de XML para exibir e editar o arquivo de esquema XML subjacente** no modo de início.

3.  Copie o código de exemplo de esquema XML do [esquema XML de exemplo: esquema de ordem de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md) e cole-o para substituir o código que foi adicionado ao novo arquivo XSD por padrão.

4.  Selecione o `purchaseOrder` elemento no esquema Explorer clicando com o `purchaseOrder` no Editor de XML do elemento e selecionando **Mostrar em XML Explorer**.

5.  Clique com botão direito do `purchaseOrder` no XML Explorer e selecione **Mostrar na exibição do modelo de conteúdo**.

     A exibição do modelo de conteúdo exibe o elemento de `purchaseOrder` na superfície de design.

6.  Expanda `shipTo`, `billTo`, e nós de `items` clicando duas vezes em cada nó ou double clicando na seta à direita de cada nó.

     Os nós de elemento de `purchaseOrder` são expandidos e agora você pode ver o modelo de conteúdo do elemento.

7.  Clique em qualquer nó no elemento de `purchaseOrder` e examine a barra de rastreamento para ver onde o esquema define o nó selecionado for encontrado.

8.  Clique o **mostrar a documentação** botão na barra de ferramentas XSD para ativar /desativar o documenation. Você também pode clicar com o botão direito do mouse na superfície de design para ativar /desativar a documentação.

9. Rick-clique a `purchaseOrder` nó e selecione **gerar XML de exemplo** para ver o documento de instância XML.