---
title: 'Como: obter uma visão geral de um conjunto de esquema usando o modo de exibição de gráfico | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670891"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Como: Obter uma visão geral de um conjunto de esquema usando a exibição do gráfico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico descreve como usar o [modo de exibição de gráfico](../xml-tools/graph-view.md) para ver uma exibição de alto nível dos nós em um conjunto de esquema e as relações entre os nós.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo

1. Crie um novo arquivo de esquema XML e salve o arquivo como Relationships.xsd.

2. Clique no **Editor usar XML para exibir e editar o link do arquivo de esquema XML subjacente** na exibição iniciar.

3. Copie o código de exemplo do esquema XML do [esquema XML de exemplo: relações](../xml-tools/sample-xsd-file-relationships.md) e cole-o para substituir o código que foi adicionado ao novo arquivo XSD por padrão.

4. Clique com o botão direito do mouse em qualquer lugar no editor de XML e selecione **Designer de exibição**.

5. Selecione o modo de gráfico da barra de ferramentas XSD.

6. Selecione o nó **conjunto de esquema** no XML Schema Explorer e arraste o nó para design suface do modo de exibição de gráfico. Você deve ver todos os nós globais, e as setas que conectam os nós que possuem relações.

     ![Exibição de Gráfico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. Clique em qualquer nó na superfície de design e examine a barra de rastreamento para ver onde o nó selecionado é localizado no conjunto de esquema.

8. Rick-clique em qualquer nó de elemento na superfície de dedesigner e selecione **gerar XML de exemplo** para ver o documento de instância XML.
