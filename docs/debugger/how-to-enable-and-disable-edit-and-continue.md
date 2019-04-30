---
title: 'Como: Habilitar e desabilitar editar e continuar | Microsoft Docs'
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
ms.openlocfilehash: 3bee60a54576ab816c63cf60f2226ebbbaf50c44
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388480"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Como: Habilitar e desabilitar editar e continuar (C#, VB, C++)

Você pode desabilitar ou habilitar **editar e continuar** no Visual Studio **opções** caixa de diálogo em tempo de design. **Editar e Continuar** só funciona em builds de depuração. Para obter mais informações, confira [Editar e Continuar](../debugger/edit-and-continue.md).

Para o C++ nativo, **editar e continuar** requer o uso de `/INCREMENTAL` opção. Para obter mais informações sobre os requisitos de recurso no C++, consulte este [postagem de blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) e [editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

**Para habilitar ou desabilitar editar e continuar:**

1. Se você estiver em uma sessão de depuração, pare a depuração (**Debug** > **parar depuração** ou **Shift**+**F5**) .

1. Na **ferramentas** > **opções** > (ou **depurar** > **opções**) > **depuração**  >  **Gerais**, selecione **editar e continuar** no painel direito.

    > [!NOTE]
    > Se IntelliTrace estiver habilitado e você coletar eventos de IntelliTrace e informações de chamada, Editar e Continuar estará desabilitado. Para obter mais informações, consulte [IntelliTrace](../debugger/intellitrace.md).

1. Para código C++, certifique-se **habilitar nativo editar e continuar** está selecionado e definir as opções adicionais:
    - **Aplicar alterações ao continuar (somente nativo)**

      Se selecionado, o Visual Studio compila automaticamente e aplica as alterações de código quando você continuar a depuração a partir de um estado de interrupção. Caso contrário, você pode optar por aplicar as alterações usando **Debug** > **aplicar alterações de código**.

    - **Avisar sobre código obsoleto (somente nativo)**

      Se selecionado, dá avisos sobre código obsoleto.

1. Clique em **OK**.
