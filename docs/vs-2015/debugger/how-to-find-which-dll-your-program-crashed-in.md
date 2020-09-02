---
title: 'Como: descobrir qual DLL seu programa falhou | Microsoft Docs'
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
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703624"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Como localizar em qual DLL o programa falhou
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora de seu próprio programa, poderá identificar a localização usando a janela **Módulos**.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos  
  
1. Observe o endereço onde a falha ocorreu.  
  
2. No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.  
  
3. Na janela **Módulos**, localize a coluna **Endereço**. Você poderá precisar usar a barra de rolagem para vê-la.  
  
4. Clique no botão **Endereço** na parte superior da coluna para classificar as DLLs por endereço.  
  
5. Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.  
  
6. Examine as colunas **Nome** e **Caminho** para ver o nome e o caminho da DLL.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: depurar DLLs nativas](../debugger/how-to-debug-native-dlls.md)   
 [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)
