---
title: Obter uma visão geral de um conjunto de esquemas
description: 'Designer de esquema XML: saiba como usar o modo de exibição de gráfico no Gerenciador de esquema XML para ver uma exibição de alto nível dos nós em um conjunto de esquema e as relações entre os nós.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 699167f8fe3662bbb162706f3f9fc6e5d53d82dc
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995285"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Como: obter uma visão geral de um conjunto de esquema usando o modo de exibição de gráfico

Este tópico descreve como usar o [modo de exibição de gráfico](../xml-tools/graph-view.md) para ver uma exibição de alto nível dos nós em um conjunto de esquema e as relações entre os nós.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo

1. Crie um novo arquivo de esquema XML e salve o arquivo como *Relationships. xsd*.

2. Clique no **Editor usar XML para exibir e editar o link do arquivo de esquema XML subjacente** na exibição iniciar.

3. Copie o código de exemplo do esquema XML do [esquema XML de exemplo: relações](../xml-tools/sample-xsd-file-relationships.md) e cole-o para substituir o código que foi adicionado ao novo arquivo XSD por padrão.

4. Clique com o botão direito do mouse em qualquer lugar no editor de XML e selecione **Designer de exibição**.

5. Selecione o modo de exibição de gráfico na **barra de ferramentas XSD**.

6. Selecione o nó **conjunto de esquema** no **XML Schema Explorer** e arraste o nó para a superfície de design do modo de exibição de gráfico. Você deve ver todos os nós globais, e as setas que conectam os nós que possuem relações.

     ![Exibição de gráfico](../xml-tools/media/relationshipingraphview.gif)

7. Clique em qualquer nó na superfície de design e examine a barra de rastreamento para ver onde o nó selecionado é localizado no conjunto de esquema.

8. Rick-clique em qualquer nó de elemento na superfície de design e selecione **gerar XML de exemplo** para ver o documento de instância XML.
