---
title: Como alternar para outro thread durante a depuração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176514"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Como alternar para outro thread durante a depuração
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você depura um aplicativo de vários threads, pode usar qualquer dos vários métodos para alternar o contexto do thread com o qual você vem trabalhando para outro thread.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Para alternar para determinado thread exibido na janela de threads  
  
- Clique duas vezes no thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para alternar para um thread em uma janela de origem  
  
- Na medianiz à esquerda, clique com o botão direito do mouse em um indicador de thread, aponte para **alternar para**e clique no nome desse thread para o qual você deseja alternar. O menu de atalho mostra apenas os threads nesse local específico.  
  
     Se nenhum indicador aparecer, clique com o botão direito do mouse na janela **threads** e verifique se **Mostrar threads na origem** está selecionado.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para alternar para um thread na barra de ferramentas do Local de Depuração  
  
1. Na barra de ferramentas **local de depuração** , clique na caixa **thread** .  
  
2. Na lista, clique no thread para o qual você deseja alternar.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
