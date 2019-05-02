---
title: 'Como: Examinar o código do sistema após uma exceção | Microsoft Docs'
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
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c34b2fdf2b6400ffe88f9e9ff08cbe6e4b41daa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092780"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Como: Examinar o código do sistema após uma exceção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando uma exceção ocorre, você poderá precisar examinar o código dentro de uma chamada do sistema para determinar a causa da exceção. O procedimento a seguir explica como fazer isso se você não tiver os símbolos carregados para o código do sistema ou se Just My Code estiver habilitado.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Para examinar o código do sistema após uma exceção  
  
1. Na janela **Pilha de Chamadas**, clique com o botão direito do mouse, em seguida, clique em **Mostrar Código Externo**.  
  
     Se Just My Code não estiver habilitado, essa opção não estará disponível no menu de atalho e o código do sistema será mostrado por padrão.  
  
2. Clique com o botão direito do mouse nos quadros de código externos que agora são exibidos na janela **Pilha de Chamadas**.  
  
3. Aponte para **Carregar Símbolos de** e, em seguida, clique em **Servidores de Símbolo da Microsoft**.  
  
    1. Se Just My Code tiver sido habilitado, uma caixa de diálogo será exibida. Indica que Just My Code agora foi desabilitado. Isso é necessário para entrar em chamadas do sistema.  
  
    2. A caixa de diálogo **Baixando símbolos públicos** é exibida. Ela desaparecerá quando o download for concluído.  
  
4. Agora você pode examinar o código do sistema na janela **Pilha de Chamadas** e em outras janelas. Por exemplo, você pode clicar duas vezes em um registro de ativação de chamadas para exibir o código em uma fonte ou na janela **Desmontagem**.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)
