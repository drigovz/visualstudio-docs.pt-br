---
title: Como visualizar uma associação de coleção (Designer de Classe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 434cfc541da3c670d8d444b9a4259b33476a17d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670518"
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Como visualizar uma associação de coleção (Designer de Classe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Propriedades e campos que são coleções de outros tipos podem ser exibidos no diagrama de classe como uma associação de coleção. Diferentemente de uma associação regular, que exibe um campo ou uma propriedade como uma linha que vincula a classe proprietária ao tipo do campo, uma associação de coleção é exibida como uma linha que vincula a classe proprietária ao tipo coletado.

### <a name="to-create-a-collection-association"></a>Para criar uma associação de coleção

1. No código, crie uma propriedade ou campo cujo tipo seja uma coleção fortemente tipada.

2. No diagrama de classe, expanda a classe de modo que os campos e as propriedades sejam mostrados.

3. Na classe, clique com o botão direito do mouse no campo ou propriedade e escolha **Mostrar como Associação de Coleção**.

     A propriedade ou o campo é mostrado como uma linha de associação vinculando ao tipo coletado.

## <a name="see-also"></a>Consulte também
 [Como criar associações entre tipos (Designer de classe)](../ide/how-to-create-associations-between-types-class-designer.md) [criando classes e tipos (Designer de classe)](../ide/designing-classes-and-types-class-designer.md) [exibindo tipos e relações (Designer de classe)](../ide/viewing-types-and-relationships-class-designer.md)
