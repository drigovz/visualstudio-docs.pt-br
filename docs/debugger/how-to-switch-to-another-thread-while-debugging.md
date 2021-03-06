---
title: Alternar para outro thread durante a depuração
description: Examine diferentes métodos para alternar para outro thread durante a depuração de um aplicativo multithread no Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: affc4dec196169580ff23c5faf2f7876a71fbba9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896523"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Como alternar para outro thread durante a depuração no Visual Studio (C#, Visual Basic, C++)
Ao depurar um aplicativo multithread, você pode usar qualquer um dos vários métodos para alternar do thread com o qual você está trabalhando para outro thread.

> [!NOTE]
> Se você quiser controlar a ordem na qual os threads são executados, será necessário [congelar e descongelar Threads](../debugger/get-started-debugging-multithreaded-apps.md).

Quando você examina threads no editor de código e as diferentes janelas de depuração multi-threaded, a seta amarela indica o thread atual. Uma seta verde com uma parte inferior indica que um thread não atual tem o contexto do depurador atual.

### <a name="to-switch-to-any-thread-that-appears"></a>Para alternar para qualquer thread que aparece

- Na janela **threads** ou de **inspeção paralela** , clique duas vezes no thread.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para alternar para um thread em uma janela de origem

- Na medianiz à esquerda, clique com o botão direito do mouse em um marcador de thread ícone de marcador de ![thread](../debugger/media/dbg-thread-marker.png "ThreadMarker"), aponte para **alternar para** e, em seguida, clique no nome do thread para o qual você deseja alternar. O menu de atalho mostra apenas os threads nesse local específico.

     Se nenhum marcador de thread aparecer, clique com o botão direito do mouse na janela **threads** e verifique se **Mostrar threads na origem** está selecionado.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para alternar para um thread na barra de ferramentas do Local de Depuração

1. Na barra de ferramentas **local de depuração** , clique na lista **thread** .

2. Na lista, clique no thread para o qual você deseja alternar.

## <a name="see-also"></a>Confira também
- [Depurar aplicativos multissegmentados](../debugger/debug-multithreaded-applications-in-visual-studio.md)
