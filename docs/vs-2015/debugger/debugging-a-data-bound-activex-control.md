---
title: Depurando um controle ActiveX associado a dados | Microsoft Docs
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
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686751"
---
# <a name="debugging-a-data-bound-activex-control"></a>Depurando um controle ActiveX com ligação de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você estiver desenvolvendo um controle ActiveX que será associado a um controle da fonte de dados, poderá criar seu próprio aplicativo de contêiner e usar esse contêiner para depurar o controle ActiveX.  
  
 Por exemplo, você pode criar um aplicativo MFC baseado em diálogo e colocar o controle associado a dados e um controle da fonte de dados na caixa de diálogo. Você pode usar esse aplicativo MFC para teste de tempo de execução e como o executável do contêiner para depurar seu controle ActiveX associado a dados.  
  
## <a name="using-the-test-container"></a>Usando o contêiner de teste  
 Se você quiser um contêiner que possa modificar facilmente para dar suporte a várias interfaces no controle ou no contêiner, use o contêiner de teste ActiveX como o executável para a sessão de depuração. No contêiner de teste ActiveX, clique em **Opções** no menu **Contêiner** para habilitar várias interfaces. Para obter mais informações, consulte [testando Propriedades e eventos com contêiner de teste](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Se você precisar entrar no código do contêiner enquanto está depurando, use a versão de depuração do contêiner ou use a versão de depuração do contêiner de teste ActiveX. Para obter mais informações, consulte [TSTCON exemplo: Contêiner de teste de controle ActiveX](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
