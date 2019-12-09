---
title: Executável para a caixa de diálogo sessão de depuração | Microsoft Docs
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
ms.openlocfilehash: 92cf53ed499318d60c8da5147685e3f0f340e404
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736231"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Caixa de diálogo Executável para Sessão de Depuração

Essa caixa de diálogo aparece quando você tenta depurar uma DLL para a qual nenhum executável está especificado. O Visual Studio não pode iniciar uma DLL diretamente. Em vez disso, o Visual Studio inicia o executável especificado. Você pode depurar a DLL quando ela é chamada pelo executável.

 **Nome do arquivo executável** Insira o nome do caminho para um executável que chama a DLL que você está depurando.

 **URL em que o projeto pode ser acessado (somente servidor ATL)** Se você estiver Depurando uma DLL de servidor ATL, insira a URL onde o projeto pode ser encontrado.

 Depois de inseridas, essas configurações são armazenadas nas páginas de propriedades do projeto, portanto, você não precisará inseri-las novamente para sessões de depuração subsequentes. Se você precisar alterar as configurações, poderá abrir as Páginas de Propriedades e alterar os valores. Para obter mais informações sobre como especificar um executável para a sessão de depuração, confira [Depurando DLLs](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.yml)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)