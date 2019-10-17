---
title: Habilitando recursos de C++ depuração em projetos (-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7f772b74a42b9704f1fd77c731022ddb44774c68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430675"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Habilitando recursos de C++ depuração em projetos (/D_DEBUG)
No [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], os recursos de depuração como asserções são habilitados quando você compila seu programa com o símbolo **_DEBUG** definido. Há duas maneiras de definir **_DEBUG**:

- Especifique **#define _DEBUG** no código-fonte ou

- Especifique a opção do compilador **/D_DEBUG**. (Se você criar seu projeto no Visual Studio usando assistentes, **/D_DEBUG** será definido automaticamente na configuração Depuração).

  Quando **_DEBUG** é definido, o compilador compila as seções de código cercadas por **#ifdef _DEBUG** e por `#endif`.

  A configuração Depuração de um programa MFC deve ser vinculada a uma versão de depuração da biblioteca MFC. Os arquivos de cabeçalho MFC determinam a versão correta da biblioteca MFC à qual vincular com base nos símbolos definidos, como **_DEBUG** e **_UNICODE**. Para obter detalhes, confira [Versões da biblioteca MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Consulte também
- [Depurando código nativo](../debugger/debugging-native-code.md)
- [Configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)