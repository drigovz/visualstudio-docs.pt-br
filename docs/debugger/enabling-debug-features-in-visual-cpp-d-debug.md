---
title: Habilitando recursos de depuração em projetos C++ (-D_DEBUG) | Microsoft Docs
description: No Visual C++ você habilita os recursos de depuração definindo _DEBUG. Saiba como fazer isso e saiba como vincular um programa MFC para depurá-lo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1a2ead92108d66b54342019fc19702e7a6e53575
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862927"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Habilitando recursos de depuração em projetos C++ (/D_DEBUG)
No [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], os recursos de depuração como asserções são habilitados quando você compila seu programa com o símbolo **_DEBUG** definido. Há duas maneiras de definir **_DEBUG**:

- Especifique **#define _DEBUG** no código-fonte ou

- Especifique a opção do compilador **/D_DEBUG**. (Se você criar seu projeto no Visual Studio usando assistentes, **/D_DEBUG** será definido automaticamente na configuração Depuração).

  Quando **_DEBUG** é definido, o compilador compila as seções de código cercadas por **#ifdef _DEBUG** e por `#endif`.

  A configuração Depuração de um programa MFC deve ser vinculada a uma versão de depuração da biblioteca MFC. Os arquivos de cabeçalho MFC determinam a versão correta da biblioteca MFC à qual vincular com base nos símbolos definidos, como **_DEBUG** e **_UNICODE**. Para obter detalhes, confira [Versões da biblioteca MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Confira também
- [Depurando código nativo](../debugger/debugging-native-code.md)
- [Configurações do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)