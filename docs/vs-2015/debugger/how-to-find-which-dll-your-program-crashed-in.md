---
title: 'Como: Localizar em qual DLL o programa falhado | Microsoft Docs'
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
ms.openlocfilehash: 1da5ba504c22f78ebd3c0705bd5ee903fb4a2997
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060554"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Como: Localizar em qual DLL o programa falhado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora de seu próprio programa, poderá identificar a localização usando a janela **Módulos**.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos  
  
1. Observe o endereço onde a falha ocorreu.  
  
2. No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.  
  
3. Na janela **Módulos**, localize a coluna **Endereço**. Você poderá precisar usar a barra de rolagem para vê-la.  
  
4. Clique no botão **Endereço** na parte superior da coluna para classificar as DLLs por endereço.  
  
5. Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.  
  
6. Examine as colunas **Nome** e **Caminho** para ver o nome e o caminho da DLL.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Depurar DLLs nativas](../debugger/how-to-debug-native-dlls.md)   
 [Como: Usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)
