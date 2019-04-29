---
title: 'Como: Localizar em qual DLL o programa falhado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7a9421af9e0caf085feb1afb27b53befe837668
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894041"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Como: Localizar em qual DLL o programa falhado (C#, C++, Visual Basic, F#)

 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora de seu próprio programa, poderá identificar a localização usando a janela **Módulos**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos

1. Observe o endereço onde a falha ocorreu.

    Se o endereço não é exibido na mensagem de erro, você precisa usar métodos alternativos para identificar a DLL. Se você suspeitar de uma DLL do sistema, você poderá [carregar símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) de servidores de símbolo da Microsoft durante a depuração. Caso contrário, talvez você precise [criar um arquivo de despejo](../debugger/using-dump-files.md) com heap informações em vez disso. Vários [ferramentas](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) estão disponíveis para criar arquivos de despejo.

2. No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.

3. Na janela **Módulos**, localize a coluna **Endereço**. Você poderá precisar usar a barra de rolagem para vê-la.

4. Clique no botão **Endereço** na parte superior da coluna para classificar as DLLs por endereço.

5. Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.

6. Examine as colunas **Nome** e **Caminho** para ver o nome e o caminho da DLL.

## <a name="see-also"></a>Consulte também
- [Depurando projetos de DLL](../debugger/debugging-dll-projects.md)
- [Como: Usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)