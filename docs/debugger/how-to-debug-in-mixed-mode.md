---
title: 'Como: Depurar no modo misto | Microsoft Docs'
ms.date: 11/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db26a3a68b15dcd6252f6bd02a540e105c993b54
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896052"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Como: Depurar no modo misto (C#, C++, Visual Basic)

Os procedimentos a seguir descrevem como habilitar a depuração de código gerenciado e nativo juntos, também conhecido como mista de depuração. Há dois cenários de depuração de modo misto:

- O aplicativo que chama uma DLL é escrito em código nativo, e a DLL é gerenciada.

- O aplicativo que chama uma DLL é escrito em código gerenciado e a DLL está no código nativo. Para obter um tutorial que orienta você durante esse cenário em mais detalhes, consulte [depurar código gerenciado e nativo](../debugger/how-to-debug-managed-and-native-code.md).

Você pode permitir que os depuradores gerenciados e nativos do projeto de aplicativo chamada **propriedade** páginas. As configurações são diferentes entre os aplicativos nativos e gerenciados.

Se você não tiver acesso a projeto de um aplicativo de chamada, você pode depurar a DLL do projeto de DLL. Modo misto para depurar apenas o projeto DLL não é necessário. Para obter mais informações, confira [Como: Depurar por meio de um projeto DLL](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> As caixas de diálogo e comandos que você vê podem ser diferentes daquelas que neste artigo, dependendo de suas configurações do Visual Studio ou a edição. Para alterar suas configurações, escolha **ferramentas** > **importar e exportar configurações**. Para obter mais informações, confira [Redefinir as configurações](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Habilitar a depuração de modo misto para um aplicativo de chamada nativo

1. Selecione o projeto C++ na **Gerenciador de soluções** e clique no **Properties** ícone, pressione **Alt**+**Enter**, ou Clique com botão direito e escolha **propriedades**.

1. No  **\<projeto > páginas de propriedades** caixa de diálogo caixa, expanda **as propriedades de configuração**e, em seguida, selecione **depuração**.

1. Defina **Tipo de Depurador** como **Misto** ou **Automático**.

1. Selecione **OK**.

   ![Habilitar a depuração de modo misto](../debugger/media/dbg-mixed-mode-from-native.png "habilitar a depuração de modo misto")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Habilitar a depuração de modo misto para um aplicativo de chamada gerenciado

1. Selecione o C# ou no projeto do Visual Basic **Gerenciador de soluções** e selecione o **propriedades** ícone, pressione **Alt**+**Enter**, ou clique com botão direito e escolha **propriedades**.

1. Selecione o **Debug** guia e, em seguida, selecione **habilitar a depuração de código nativo**.

1. Feche a página de propriedades para salvar as alterações.

   ![Habilitar a depuração de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "habilitar a depuração de código nativo")

> [!NOTE]
> Na maioria das versões do Visual Studio 2017, você precisa usar o arquivo *launchSettings.json* em vez das propriedades do projeto para habilitar a depuração de modo misto de um código nativo em um aplicativo .NET Core. Para obter detalhes, consulte [depurar código gerenciado e nativo](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Consulte também

- [Como: Depurar por meio de um projeto DLL](../debugger/how-to-debug-from-a-dll-project.md)