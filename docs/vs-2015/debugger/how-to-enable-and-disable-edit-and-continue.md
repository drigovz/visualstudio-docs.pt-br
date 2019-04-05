---
title: 'Como: Habilitar e desabilitar editar e continuar | Microsoft Docs'
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
ms.openlocfilehash: 0fe1af00bde865b98fb165efe109fe1bb5cabd49
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58999912"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Como: Habilitar e desabilitar editem e continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode desabilitar ou habilitar editar e continuar na **opções** caixa de diálogo em tempo de design. Não é possível alterar essa configuração enquanto você está depurando.  
  
 Editar e Continuar só funciona em compilações de depuração. Para o C++ nativo, Editar e Continuar exige o uso da opção /INCREMENTAL.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar/desabilitar a função Editar e Continuar  
  
1. Abrir página de opções de depuração (**Ferramentas / opções / depuração**).  
  
2. Role para baixo até **editar e continuar** categoria.  
  
3. Para habilitar, selecione a **habilitar editar e continuar** caixa de seleção. Para desabilitar, desmarque a caixa de seleção.  
  
   > [!NOTE]
   >  Se IntelliTrace estiver habilitado e você coletar eventos de IntelliTrace e informações de chamada, Editar e Continuar estará desabilitado. Para obter mais informações, consulte [configurar o IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Clique em **OK**.  
  
   Para obter mais informações sobre essas opções, consulte [geral, depuração, caixa de diálogo Opções](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Consulte também  
 [Editar e continuar](../debugger/edit-and-continue.md)
