---
title: Depuração usando o Visualizador da loja | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654887"
---
# <a name="debugging-by-using-the-store-viewer"></a>Depurando por meio do Visualizador de Repositório
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com o Visualizador da loja, você pode examinar o estado de um *repositório* usado pelo [!INCLUDE[dsl](../includes/dsl-md.md)] . O Visualizador da loja exibe todos os elementos de modelo de domínio que estão em um repositório específico, juntamente com propriedades de elemento e links entre elementos.

## <a name="opening-store-viewer"></a>Abrindo o Visualizador da loja
 Quando você estiver na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compilação experimental, pare seu código em um ponto de interrupção em que uma instância do repositório contém informações de modelo. Em seguida, abra o Visualizador da loja digitando o seguinte comando na janela **imediata** :

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> Você deve substituir `mystore` pelo nome da instância do repositório. Além disso, se você adicionar o namespace ao seu código, poderá digitar o comando para exibir o Visualizador de loja sem o namespace totalmente qualificado:
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 O `Show` método tem várias sobrecargas. Você pode especificar uma instância de um repositório ou uma partição como o parâmetro.

 Como alternativa, você pode colocar a linha de código que exibe o Visualizador da loja em qualquer lugar no código em que o parâmetro que você passa para o `Show` método está no escopo. Essa ação exibe o Visualizador da loja quando a linha de código é executada como um instantâneo do conteúdo do repositório.

### <a name="using-store-viewer"></a>Usando o Visualizador da loja
 Quando o Visualizador da loja é aberto, uma janela de Windows Forms do modelo é exibida, como mostra a ilustração a seguir.

 ![](../modeling/media/storeviewer2.png "storeviewer2") Visualizador da loja

 O Visualizador da loja tem três painéis: o painel esquerdo, o painel superior direito e o painel inferior direito. O painel esquerdo é uma exibição de árvore dos tipos no `DomainDataDirectory` membro de uma loja. Se você expandir o nó de partição e clicar em um elemento, as propriedades do elemento aparecerão no painel superior direito. Se o elemento estiver vinculado a outros elementos, os elementos adicionais aparecerão no painel inferior direito. Se você clicar duas vezes em um elemento no painel inferior direito, o elemento será realçado no painel esquerdo.

## <a name="see-also"></a>Consulte Também
 [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
