---
title: Trabalhando com o diagrama de definição de DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14e365d6bbe99634135bfad133d840b98e22e3b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663034"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Trabalhando com o diagrama de definição de DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O diagrama de uma [!INCLUDE[dsl](../includes/dsl-md.md)] definição é uma ferramenta importante para definir a linguagem específica do domínio. É possível adicionar elementos ao seu modelo de domínio e definir as relações no diagrama e é possível modificar o layout do diagrama para torná-lo mais legível.

## <a name="the-layout-of-the-diagram"></a>O layout do diagrama
 O [!INCLUDE[dsl](../includes/dsl-md.md)] diagrama de definição tem duas partições, a partição de **classes e relações** e a partição de **elementos de diagrama** . A partição **classes e relações** exibe classes de domínio, relações de domínio e herança. A partição de **elementos de diagrama** exibe classes de forma, classes de conector, classes de raia e o diagrama de designer gerado.

 As classes de domínio podem aparecer em vários locais nas partições **classes e relações** . Uma definição de classe de domínio exibe uma árvore de herança se esta for a classe base para outras classes de domínio e uma árvore de relações se for a fonte de relações de incorporação ou de referência. Espaços reservados de classe de domínio aparecem como alvos de relações de incorporação ou de referência. Por padrão, os elementos de espaço reservado são exibidos com o compartimento de **Propriedades de domínio** recolhido. Eles não mostram a herança ou as relações de incorporação ou referência.

 Quando você adiciona uma classe de domínio, ela aparece na parte inferior da partição **classes e relações** . Ao adicionar uma relação de incorporação ou referência, ela é desenhada abaixo e à direita da classe de domínio da fonte.

 À medida que adicionar classes de domínio e relações, pode tornar-se difícil localizar uma classe de domínio específica. Você pode encontrar uma classe de domínio clicando com o botão direito do mouse no **Gerenciador de DSL** e clicando em **Localizar no diagrama**.

 As seções a seguir descrevem como é possível alterar a aparência do diagrama para facilitar a leitura.

## <a name="copying-elements"></a>Copiando elementos
 É possível usar copiar, cortar e colar em elementos no diagrama de definição DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Aumentar ou diminuir o zoom no diagrama
 Você pode ampliar ou reduzir o diagrama usando a barra de ferramentas **Designer de DSL** para definir o nível de zoom.

## <a name="hiding-map-lines"></a>Ocultando linhas do mapa
 As linhas do mapa são linhas desenhadas entre uma relação de classe ou do domínio e a forma ou o conector ao qual ela está mapeada. Você pode ocultar linhas de mapa clicando no botão **Mostrar linhas de mapa** na barra de ferramentas **Designer de DSL** . Para mostrar as linhas, clique no botão novamente.

## <a name="changing-the-diagram-layout"></a>Alterar o layout do diagrama
 Você pode alterar o layout da partição **classes e relações** da seguinte maneira.

### <a name="expandcollapse"></a>Expandir/Recolher
 Você pode reduzir o tamanho de um elemento de forma de compartimento que representa uma classe de domínio ou uma forma clicando com o botão direito do mouse e clicando em **recolher**. Isso oculta o compartimento de **Propriedades de domínio** da forma. Para mostrar o compartimento de **Propriedades de domínio** novamente, clique com o botão direito do mouse na forma e clique em **expandir**.

### <a name="move-updown"></a>Mover para Cima/para Baixo
 Você pode mover uma classe de domínio ou um elemento de diagrama para cima ou para baixo na partição clicando com o botão direito do mouse no elemento e clicando em **mover para cima** ou **mover para baixo**. Se você mover um elemento do espaço reservado que está exibido como um alvo de uma relação de incorporação ou referência, a relação será movida com ele.

### <a name="expandcollapse-relationships-tree"></a>Árvore de relações de expandir/recolher
 Se uma classe de domínio reproduzir a função de origem em relações de incorporação ou referência com outras classes de domínio, você poderá ocultar as relações clicando com o botão direito do mouse na definição de classe de domínio e clicando em **recolher árvore de relações**. Para mostrar as relações, clique com o botão direito do mouse no elemento de definição e clique em **expandir árvore de relações**.

### <a name="expandcollapse-inheritance-tree"></a>Expandir/Recolher Árvore de Relacionamentos
 Se uma classe de domínio for a classe base de outras classes de domínio, você poderá ocultar a árvore de herança clicando com o botão direito do mouse na definição de classe de domínio e clicando em **recolher árvore de herança**. Para mostrar a árvore de herança, clique com o botão direito do mouse no elemento de definição e clique em **expandir árvore de herança**.

### <a name="bring-tree-here"></a>Bring Tree Here
 Você pode consolidar o diagrama clicando com o botão direito do mouse em uma classe de domínio de espaço reservado e clicando em **colocar árvore aqui**. A classe de domínio do espaço reservado torna-se um elemento de definição e exibe as árvores de herança e relações. O elemento de definição anterior torna-se um elemento do espaço reservado, se este for o alvo de uma relação ou o filho em uma relação de herança; caso contrário, ele desaparece.

### <a name="split-tree"></a>Dividir Árvore
 Você pode dividir as árvores de herança ou de relações clicando com o botão direito do mouse na definição de classe de domínio que as exibe e clicando em **dividir árvore**. O elemento de definição torna-se um elemento de espaço reservado e a classe de domínio de definição, juntamente com suas árvores de herança e relações, agora é exibida na parte inferior da partição.

### <a name="show-as-class"></a>Show As Class
 Se uma relação de domínio tiver relações derivadas, ou se tiver uma incorporação ou relações de referência com outras relações de domínio, você poderá exibir a relação como uma classe clicando com o botão direito do mouse na relação e, em seguida, clicando em **mostrar como classe**. A relação será exibida com um compartimento de **Propriedades de domínio** e mostrará as árvores de herança e relações.

## <a name="see-also"></a>Consulte Também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
