---
title: Executável para a caixa de diálogo de sessão de depuração | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 681a1b150058c66be42caca7241b9054151098f8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858786"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Caixa de diálogo Executável para Sessão de Depuração
Essa caixa de diálogo aparece quando você tenta depurar uma DLL para a qual nenhum executável está especificado. O Visual Studio não pode iniciar uma DLL diretamente. Em vez disso, ele iniciará o executável especificado. Você pode depurar a DLL quando ela for chamada pelo executável.  
  
 **Nome de arquivo executável**  
 Digite o nome do caminho para um executável que chama a DLL que você está depurando.  
  
 **URL em que o projeto pode ser acessado (somente servidor ATL)**  
 Se você estiver depurando um DLL do servidor ATL, digite a URL onde o projeto pode ser localizado.  
  
 Uma vez inseridas, essas configurações são armazenadas nas Páginas de Propriedades do projeto, de modo que você não precise inseri-las novamente para sessões de depuração subsequentes. Se você precisar alterar as configurações, poderá abrir as Páginas de Propriedades e alterar os valores. Para obter mais informações sobre como especificar um executável para a sessão de depuração, confira [Depurando DLLs](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)