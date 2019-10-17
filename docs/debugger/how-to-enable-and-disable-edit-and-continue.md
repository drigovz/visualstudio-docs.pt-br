---
title: Como habilitar e desabilitar editar e continuar | Microsoft Docs
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430526"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Como habilitar e desabilitar editar e continuar (C#, VB,) C++

Você pode desabilitar ou habilitar **Editar e continuar** na caixa de diálogo **Opções** do Visual Studio em tempo de design. **Editar e Continuar** só funciona em builds de depuração. Para obter mais informações, confira [Editar e Continuar](../debugger/edit-and-continue.md).

Para o C++nativo, **Editar e continuar** requer o uso da opção `/INCREMENTAL`. Para obter mais informações sobre os requisitos C++de recursos no, consulte esta [postagem de blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) e [EditC++and Continue ()](../debugger/edit-and-continue-visual-cpp.md).

**Para habilitar ou desabilitar editar e continuar:**

1. Se você estiver em uma sessão de depuração, pare a depuração (**Debug** > **Stop debugging** ou **Shift**+**F5**).

1. Na **ferramentas** > **opções** > (ou **depurar** > **opções**) > **depuração**  >  **Gerais**, selecione **editar e continuar** no painel direito.

    > [!NOTE]
    > Se IntelliTrace estiver habilitado e você coletar eventos de IntelliTrace e informações de chamada, Editar e Continuar estará desabilitado. Para obter mais informações, consulte [IntelliTrace](../debugger/intellitrace.md).

1. Para C++ código, certifique-se de habilitar a opção **Editar e continuar nativo** está selecionado e defina as opções adicionais:
    - **Aplicar alterações ao continuar (somente nativo)**

      Se selecionado, o Visual Studio compila automaticamente e aplica alterações de código quando você continua a depuração de um estado de interrupção. Caso contrário, você pode optar por aplicar as alterações usando **Debug** > **aplicar alterações de código**.

    - **Avisar sobre código obsoleto (somente nativo)**

      Se selecionado, fornecerá avisos sobre o código obsoleto.

1. Clique em **OK**.
