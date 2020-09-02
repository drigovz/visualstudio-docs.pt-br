---
title: 'Como: depurar DLLs nativas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702675"
---
# <a name="how-to-debug-native-dlls"></a>Como depurar DLLs nativas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Quando você depura uma DLL, pode iniciar a depuração de:  
  
- O projeto usado para criar o executável que chama a DLL.  
  
  \- ou –  
  
- O projeto usado para criar a própria DLL.  
  
  Se você tiver o projeto usado para criar o executável, inicie a depuração do início desse projeto. Você pode abrir um arquivo de origem para a DLL e definir os pontos de interrupção nesse arquivo, mesmo que não seja uma parte do projeto usado para criar o executável. Para obter mais informações, confira [Pontos de interrupção](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Se você iniciar a depuração do projeto que cria a DLL, deverá especificar o executável que deseja usar ao depurar a DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Para especificar um executável para a sessão de depuração  
  
1. Em **Gerenciador de soluções**, selecione o projeto que cria a dll.  
  
2. No menu **Exibir** , escolha**páginas de propriedades**.  
  
3. Na caixa de diálogo **páginas de propriedades** , abra a pasta **Propriedades de configuração** e selecione a categoria **depuração** .  
  
4. Na caixa **comando** , especifique o nome do caminho para o contêiner. Por exemplo, C:\Arquivos de Programas\MyApplication\MYAPP.EXE.  
  
5. Na caixa **argumentos de comando** , especifique os argumentos necessários para o executável.  
  
   Se você não especificar o executável na caixa de diálogo**páginas de propriedades** do _projeto_, a [caixa de diálogo executável para depuração da sessão](../debugger/executable-for-debugging-session-dialog-box.md) será exibida quando você iniciar a depuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)
