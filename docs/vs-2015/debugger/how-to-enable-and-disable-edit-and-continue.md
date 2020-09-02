---
title: Como habilitar e desabilitar editar e continuar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689258"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Como habilitar e desabilitar Editar e Continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode desabilitar ou habilitar editar e continuar na caixa de diálogo **Opções** em tempo de design. Não é possível alterar essa configuração enquanto você está depurando.  
  
 Editar e Continuar só funciona em compilações de depuração. Para o C++ nativo, Editar e Continuar exige o uso da opção /INCREMENTAL.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar/desabilitar a função Editar e Continuar  
  
1. Abra a página opções de depuração (**ferramentas/opções/depuração**).  
  
2. Role para baixo até **Editar e continuar** categoria.  
  
3. Para habilitar, marque a caixa de seleção **habilitar editar e continuar** . Para desabilitar, desmarque a caixa de seleção.  
  
   > [!NOTE]
   > Se IntelliTrace estiver habilitado e você coletar eventos de IntelliTrace e informações de chamada, Editar e Continuar estará desabilitado. Para obter mais informações, consulte [Configurar o IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Clique em **OK**.  
  
   Para obter mais informações sobre essas opções, consulte [geral, depuração, caixa de diálogo opções](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Editar e continuar](../debugger/edit-and-continue.md)
