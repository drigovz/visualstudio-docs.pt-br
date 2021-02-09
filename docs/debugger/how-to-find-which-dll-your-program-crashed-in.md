---
title: Descobrir em qual DLL seu programa falhou | Microsoft Docs
description: Use a janela módulos para identificar qual DLL externa estava ativa quando o aplicativo falhou. Você pode fazer isso para uma DLL do sistema ou para o código de outra pessoa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4636c3b5150bd04b8a776b28d210be1cef79dcda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877636"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Como: descobrir qual DLL seu programa falhou (C#, C++, Visual Basic, F #)

 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu. Se você tiver uma falha em uma DLL fora de seu próprio programa, poderá identificar a localização usando a janela **Módulos**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para descobrir onde ocorreu uma falha usando a janela Módulos

1. Observe o endereço onde a falha ocorreu.

    Se o endereço não for mostrado na mensagem de erro, talvez seja necessário usar métodos alternativos para identificar a DLL. Se você suspeitar de uma DLL do sistema, poderá [carregar símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) dos servidores de símbolo da Microsoft durante a depuração. Caso contrário, talvez seja necessário [criar um arquivo de despejo](../debugger/using-dump-files.md) com informações de heap. Várias [ferramentas](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) estão disponíveis para criar arquivos de despejo.

2. No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.

3. Na janela **Módulos**, localize a coluna **Endereço**. Você poderá precisar usar a barra de rolagem para vê-la.

4. Clique no botão **Endereço** na parte superior da coluna para classificar as DLLs por endereço.

5. Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.

6. Examine as colunas **Nome** e **Caminho** para ver o nome e o caminho da DLL.

## <a name="see-also"></a>Confira também
- [Depurando projetos de DLL](../debugger/debugging-dll-projects.md)
- [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)