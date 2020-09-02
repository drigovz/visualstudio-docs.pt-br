---
title: 'Como: depurar código injetado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df35a25534961c6ab94891d2da6fe54f05c37a3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681085"
---
# <a name="how-to-debug-injected-code"></a>Como depurar código injetado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Usar atributos pode simplificar muito a programação C++. Para obter mais informações, consulte [conceitos](https://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Alguns atributos são interpretados diretamente pelo compilador. Outros atributos injetam o código na origem do programa, que o compilador em seguida compila. Este código injetado facilita a programação reduzindo a quantidade de códigos que você precisa escrever. Entretanto, às vezes, um bug pode causar falha no aplicativo ao executar o código injetado. Quando isso acontece, você provavelmente desejará examinar o código injetado. O Visual Studio fornece duas maneiras de ver o código injetado:  
  
- Você pode exibir o código injetado na janela **Desmontagem**.  
  
- Usando [/Fx](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), você pode criar um arquivo de origem mesclada que contém o código original e injetado.  
  
  A janela **Desmontagem** mostra as instruções da linguagem assembly que corresponde ao código-fonte e o código injetado por atributos. Além disso, a janela **Desmontagem** pode mostrar a anotação do código-fonte.  
  
### <a name="to-turn-on-source-annotation"></a>Para ativar a anotação de origem  
  
- Clique com o botão direito do mouse na janela **Desmontagem** e escolha **Mostrar Código-Fonte** no menu de atalho.  
  
     Se você souber a localização de um atributo em uma janela de origem, poderá usar o menu de atalho para localizar o código injetado na janela **Desmontagem**.  
  
### <a name="to-view-injected-code"></a>Para exibir o código injetado  
  
1. O depurador deve estar no modo de interrupção.  
  
2. Em uma janela do código-fonte, coloque o cursor na frente do atributo cujo código injetado você deseja exibir.  
  
3. Clique com o botão direito do mouse e selecione **Ir para Desmontagem** no menu de atalho.  
  
     Se a localização do atributo estiver perto do ponto de execução atual, você poderá selecionar a janela **Desmontagem** no menu **Depurar**.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Para exibir o código de desmontagem no ponto de execução atual  
  
1. O depurador deve estar no modo de interrupção.  
  
2. No menu **Depurar**, escolha **Windows** e clique em **Desmontagem**.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
