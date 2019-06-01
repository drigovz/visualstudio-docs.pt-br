---
title: 'Designer de esquema XML: Obter a visão geral do conjunto de esquema usando o modo de exibição gráfico'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a0fc62a0d6dfe772a550f33cafa02bc5bc1bf3
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432166"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Como: Obtenha uma visão geral de um esquema definido usando o modo de exibição de gráfico

Este tópico descreve como usar o [modo de exibição gráfico](../xml-tools/graph-view.md) para ver uma exibição de alto nível de nós em um conjunto de esquema e as relações entre os nós.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo

1. Crie um novo arquivo de esquema XML e salve o arquivo como *Relationships*.

2. Clique o **editor de XML de uso para exibir e editar o arquivo de esquema XML subjacente** link no modo de início.

3. Copie o código de exemplo de esquema XML do [esquema XML de exemplo: relações](../xml-tools/sample-xsd-file-relationships.md) e cole-o para substituir o código que foi adicionado ao novo arquivo XSD por padrão.

4. Clique com botão direito em qualquer lugar no editor de XML e selecione **Designer de exibição**.

5. Selecione o modo de exibição de gráfico do **barra de ferramentas XSD**.

6. Selecione **do conjunto de esquema** nó na **XML Schema Explorer** e arraste o nó para a superfície de design de exibição de gráfico. Você deve ver todos os nós globais, e as setas que conectam os nós que possuem relações.

     ![Exibição de gráfico](../xml-tools/media/relationshipingraphview.gif)

7. Clique em qualquer nó na superfície de design e examine a barra de rastreamento para ver onde o nó selecionado é localizado no conjunto de esquema.

8. Rick-clique em qualquer nó de elemento na superfície do design e selecione **gerar XML de exemplo** para ver o documento de instância XML.