---
title: 'Como: Depurar um controle ActiveX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8dea98b05f5350f581128f18f38ec5f095505a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105651"
---
# <a name="how-to-debug-an-activex-control"></a>Como: Depurar um controle ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para depurar seu controle ActiveX, você deverá especificar um contêiner (executável) em que o controle será executado.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Para especificar um contêiner para a sessão de depuração  
  
1. No Gerenciador de Soluções, selecione o projeto.  
  
2. Dos **modo de exibição** menu, escolha **páginas de propriedade**.  
  
3. Na caixa de diálogo **Páginas de Propriedades de Projeto**, abra a pasta **Propriedades de Configuração** e selecione **Depurando**.  
  
4. Na categoria **Depurando**, localize a propriedade **Comando**.  
  
5. Especifique o nome do caminho para o contêiner. Por exemplo, C:\Arquivos de Programas\Internet Explorer\IEXPLORE.EXE.  
  
6. Se você especificar o Internet Explorer como o contêiner e estiver usando o Active Desktop, digite `/new` na caixa **Argumentos do Comando**.  
  
7. Clique em **OK**.  
  
     Se você não especificar um contêiner na caixa de diálogo **Páginas de Propriedades do Projeto**, poderá especificar o contêiner quando iniciar a depuração. Quando você selecionar um comando de execução para iniciar a depuração, a [caixa de diálogo Executável para Sessão de Depuração](../debugger/executable-for-debugging-session-dialog-box.md) é exibida. Especifique o nome do caminho do contêiner na caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Controles ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testando propriedades e eventos com contêiner de teste](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)
