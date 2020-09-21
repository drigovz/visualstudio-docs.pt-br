---
title: 'Como: Depurar de um projeto de DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838600"
---
# <a name="how-to-debug-from-a-dll-project"></a>Como depurar a partir de um projeto de DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para iniciar a depuração de um projeto de DLL, você deve especificar o aplicativo de chamada nas propriedades do projeto. As páginas de propriedades do C++ diferem no layout e no conteúdo das páginas de propriedades do C# e do Visual Basic.  
  
 Se uma DLL gerenciada for chamada pelo código nativo e você quiser depurar ambas, você poderá especificar isso nas propriedades do projeto. Para obter mais informações, consulte [como depurar em modo misto](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> Você não pode especificar um aplicativo de chamada externa nas Express Editions do Visual Studio. Em vez disso, você precisa adicionar um projeto executável à solução, defini-lo como o projeto de inicialização e chamar métodos em sua DLL a partir do projeto executável.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Para especificar o aplicativo de chamada em um projeto C++  
  
1. Clique com o botão direito do mouse no nó do projeto na **Gerenciador de soluções** e selecione **Propriedades**. Vá para a guia **depurar** .  
  
2. Verifique se o campo de **configuração** na parte superior da janela está definido como **depurar**.  
  
3. Vá para **Configuração propriedades/depuração**.  
  
4. Na lista **depurador a ser iniciado** , escolha **depurador local do Windows** ou **depurador remoto do Windows**.  
  
5. Na caixa **comando** ou **comando remoto** , adicione o nome do caminho totalmente qualificado do aplicativo.  
  
6. Adicione todos os argumentos de programa necessários à caixa **argumentos de comando** .  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Para especificar o aplicativo de chamada em um projeto C# ou Visual Basic  
  
1. Clique com o botão direito do mouse no nó do projeto na **Gerenciador de soluções** e selecione **Propriedades**. Vá para a guia **depurar** .  
  
     Selecione **Iniciar programa externo**e adicione o nome do caminho totalmente qualificado do programa a ser executado.  
  
     Se você precisar adicionar os argumentos de linha de comando do programa externo, adicione-os no campo **argumentos de linha de comando** .  
  
2. Você também pode chamar um aplicativo como uma URL. (Você poderá fazer isso se estiver depurando uma DLL gerenciada usada por um aplicativo local do ASP.NET.)  
  
     Em **Iniciar ação**, selecione o botão **Iniciar navegador no URL:** e preencha a URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Para iniciar a depuração do projeto da DLL  
  
1. Defina pontos de interrupção conforme necessário.  
  
2. Inicie a depuração (pressione F5, clique na seta verde ou clique em **depurar/iniciar depuração**).  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração de projetos de DLL](../debugger/debugging-dll-projects.md)   
 [Configurações de projeto para configurações de depuração em C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configurações de projeto para uma configuração de depuração de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Definições do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
