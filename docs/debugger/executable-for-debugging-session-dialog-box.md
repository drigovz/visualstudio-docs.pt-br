---
title: Executável para a caixa de diálogo sessão de depuração | Microsoft Docs
description: Para depurar uma DLL, você deve especificar um executável para chamar a DLL. Saiba mais sobre a caixa de diálogo que aparece quando nenhum executável é especificado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4f1f1a88ad30d5102043571473be0d72d71a054
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863043"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Caixa de diálogo Executável para Sessão de Depuração

Essa caixa de diálogo aparece quando você tenta depurar uma DLL para a qual nenhum executável está especificado. O Visual Studio não pode iniciar uma DLL diretamente. Em vez disso, o Visual Studio inicia o executável especificado. Você pode depurar a DLL quando ela é chamada pelo executável.

 **Nome do arquivo executável** Insira o nome do caminho para um executável que chama a DLL que você está depurando.

 **URL em que o projeto pode ser acessado (somente servidor ATL)** Se você estiver Depurando uma DLL de servidor ATL, insira a URL onde o projeto pode ser encontrado.

 Depois de inseridas, essas configurações são armazenadas nas páginas de propriedades do projeto, portanto, você não precisará inseri-las novamente para sessões de depuração subsequentes. Se você precisar alterar as configurações, poderá abrir as Páginas de Propriedades e alterar os valores. Para obter mais informações sobre como especificar um executável para a sessão de depuração, consulte [Debugging DLLs](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Confira também

- [Depurando no Visual Studio](../debugger/index.yml)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)