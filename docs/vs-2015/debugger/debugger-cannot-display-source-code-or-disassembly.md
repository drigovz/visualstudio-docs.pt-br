---
title: O depurador não pode exibir o código-fonte ou a desmontagem | Microsoft Docs
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
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186505"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>O depurador não pode exibir o código-fonte ou a desmontagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este erro é:  
  
 O depurador não pode exibir o código-fonte ou a desmontagem do local atual no qual a execução foi interrompida.  
  
 Essa mensagem de erro pode ocorrer por várias razões:  
  
- Você pode ter atingido um ponto de interrupção em um local para o qual não há o código-fonte, ao depurar uma linguagem que não oferece suporte a desmontagem. Abra a janela **pontos de interrupção** , localize o ponto de interrupção e exclua-o.  
  
- Se você estiver depurando scripts, você pode ter atingido um ponto de interrupção enquanto não havia nenhum thread em seu programa. Escolha **Etapa** ou **Continuar** no menu **Depurar** para retomar a depuração.  
  
- Os critérios de segurança podem ter impedido que o depurador lesse a pilha, o thread, o registro e outras informações de contexto do programa que você está depurando. É mais provável que isso ocorra se você estiver depurando um aplicativo Web e não tiver a permissão correta para acessar o diretório virtual. Defina a segurança do diretório virtual como Anônima e tente novamente.  
  
## <a name="see-also"></a>Consulte Também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Depuração no Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)
