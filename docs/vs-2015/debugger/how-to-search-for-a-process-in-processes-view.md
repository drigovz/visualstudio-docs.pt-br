---
title: 'Como: Pesquisar por um processo na exibição de processos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e39168e36e9540ec8c5e23a9030d996b81c4097c
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64799506"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Como: Pesquise um processo na exibição de processos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode procurar um processo específico na exibição de processos por meio de sua cadeia de caracteres de ID ou o módulo de processo como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrará os atributos do processo selecionado na árvore de processo.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Para pesquisar por um processo na exibição de processos  
  
1. Organizar as janelas assim que Spy + + e um ativo [exibição de processos](../debugger/processes-view.md) janela são visíveis.  
  
2. Dos **pesquisa** menu, escolha **localizar processo**  
  
    O [caixa de diálogo de pesquisa de processo](../debugger/process-search-dialog-box.md) é aberta.  
  
3. Como critérios de pesquisa, digite a ID do processo ou uma cadeia de caracteres do módulo.  
  
4. Limpe todos os campos para o qual você deseja especificar valores.  
  
   > [!TIP]
   > Para localizar todos os processos pertencentes a um módulo, desmarque a **processo** caixa e digite o nome do módulo na **módulo** caixa. Em seguida, use **Localizar próximo** para continuar a pesquisa de processos.  
  
5. Escolher **para cima** ou **para baixo** para a direção inicial da pesquisa.  
  
6. Clique em **OK**.  
  
   Se um processo de correspondência for encontrado, ele é realçado na **exibição de processo** janela.
