---
title: Habilitando recursos de depuração no Visual C++ (-D_DEBUG) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686699"
---
# <a name="enabling-debug-features-in-visual-c-d_debug"></a>Habilitando funcionalidades de depuração no Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], os recursos de depuração como asserções são habilitados quando você compila seu programa com o símbolo **_DEBUG** definido. Há duas maneiras de definir **_DEBUG**:  
  
- Especifique **#define _DEBUG** no código-fonte ou  
  
- Especifique a opção do compilador **/D_DEBUG**. (Se você criar seu projeto no Visual Studio usando assistentes, **/D_DEBUG** será definido automaticamente na configuração Depuração).  
  
  Quando **_DEBUG** é definido, o compilador compila as seções de código cercadas por **#ifdef _DEBUG** e por `#endif`.  
  
  A configuração Depuração de um programa MFC deve ser vinculada a uma versão de depuração da biblioteca MFC. Os arquivos de cabeçalho MFC determinam a versão correta da biblioteca MFC à qual vincular com base nos símbolos definidos, como **_DEBUG** e **_UNICODE**. Para obter detalhes, confira [Versões da biblioteca MFC](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração de código nativo](../debugger/debugging-native-code.md)   
 [Definições do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
